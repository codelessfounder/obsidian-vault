---

---

Got it, Harry. Here’s a practical, end-to-end blueprint for Disco’s **outcome engine** using a React (TS) PWA + Supabase. It’s split into architecture, schema, API, code patterns, security/RLS, verification, and ops/testing—so you can lift pieces straight into Cursor.

**
1) Architecture at a glance**
• **Client (React PWA, TS):**
    ◦ Collects **clientSeed**; displays **hashed serverSeed**, **nonce**, and the **verifiable transcript**.
    ◦ Calls a Supabase **Edge Function** to get the outcome (never computes the final outcome client-side).
• **Edge Functions (TypeScript on Deno):**
    ◦ Holds **current serverSeed (secret)** and **serverSeedHash (public)**.
    ◦ Deterministically computes outcomes via **HMAC-SHA256(serverSeed, clientSeed|nonce|gameId|… ) → RNG stream → game math**.
    ◦ Writes an **immutable round record** + cryptographic artefacts to Postgres.
• **Supabase (Postgres + RLS):**
    ◦ Tables for **seeds**, **rounds**, **bets**, **limits**, **audit logs**.
    ◦ RLS so players can only see their own rounds; public verification view exposes only **serverSeedHash** and revealed seeds *after rotation*.
• **Back-office (admin panel):**
    ◦ Rotate seeds, view exposure, cap limits, kill-switch specific games/variants.**
2) Deterministic PRNG + “Provably Fair” recipe**
**Why:** Certified practice is PRNG + game math. For transparency, wrap with provably-fair: player supplies **clientSeed**, server commits to **serverSeedHash** before play, then reveals **serverSeed** after rotation. Anyone can recompute outcomes.
**Core function**

`// Edge Function (server-side only)
import { crypto } from "https://deno.land/std/crypto/mod.ts";

// 1. Derive a 32-byte digest (HMAC) from (serverSeed, message)
async function hmacSHA256(serverSeed: string, message: string): Promise<Uint8Array> {
  const key = await crypto.subtle.importKey(
    "raw",
    new TextEncoder().encode(serverSeed),
    { name: "HMAC", hash: "SHA-256" },
    false,
    ["sign"],
  );
  const sig = await crypto.subtle.sign("HMAC", key, new TextEncoder().encode(message));
  return new Uint8Array(sig);
}

// 2. Expand into a stream of pseudo-random numbers in [0,1)
export async function* rngStream(params: {
  serverSeed: string; clientSeed: string; nonce: number; roundSalt: string;
}) {
  let counter = 0;
  while (true) {
    const msg = `${params.clientSeed}:${params.nonce}:${params.roundSalt}:${counter}`;
    const digest = await hmacSHA256(params.serverSeed, msg);
    // use first 4 bytes → uint32 → [0,1)
    const u32 = (digest[0]<<24) | (digest[1]<<16) | (digest[2]<<8) | digest[3];
    const x = (u32 >>> 0) / 2**32;
    yield x; // consume sequentially in game math
    counter++;
  }
}
`
**Mapping RNG → game outcome (example: coin flip 50/50)**

`export async function coinFlipOutcome(args: {
  serverSeed: string; clientSeed: string; nonce: number; roundSalt: string;
}) {
  const stream = rngStream(args);
  const { value: r } = await stream.next();
  return r! < 0.5 ? "HEADS" : "TAILS";
}
`
**Mapping for weighted tables (e.g., variable discount / multiplier):**

`// weights sum to 1.0; preserves certified RTP via math model.
type WeightedOutcome<T> = { value: T; p: number };
export async function weightedPick<T>(
  weights: WeightedOutcome<T>[],
  prng: AsyncGenerator<number, any, unknown>
): Promise<T> {
  const { value: r } = await prng.next();
  let acc = 0;
  for (const w of weights) {
    acc += w.p;
    if (r! < acc) return w.value;
  }
  return weights[weights.length - 1].value; // numeric drift guard
}
`**
3) Game-math layer (RTP/volatility)**
• Keep **RNG generation** separate from **math**.
• Define per-game **paytables**, **hit rates**, **variance knobs** (e.g., outcome weights, streak rules).
• Maintain a **versioned “math spec”** (JSON) stored in Supabase; every round stores **math_version** for audit reproducibility.**
4) Supabase schema (minimal core)**

`-- Seeds committed for a season/epoch of rounds
create table server_seeds (
  id uuid primary key default gen_random_uuid(),
  created_at timestamptz default now(),
  -- Plain server seed kept encrypted-at-rest; access via Edge only
  server_seed ciphertext,            -- use pgcrypto or KMS ext
  server_seed_hash text not null,    -- SHA-256(server_seed), public
  active boolean not null default true,
  rotates_at timestamptz not null    -- planned rotation time
);

-- Player-submitted client seeds (optional; default if none)
create table client_seeds (
  id uuid primary key default gen_random_uuid(),
  user_id uuid not null references auth.users(id),
  client_seed text not null,
  created_at timestamptz default now()
);

-- Each round/outcome is immutable (append-only)
create table game_rounds (
  id uuid primary key default gen_random_uuid(),
  created_at timestamptz default now(),
  user_id uuid not null references auth.users(id),
  game_id text not null,                 -- e.g. 'coin_flip_v1'
  math_version text not null,            -- ties to JSON spec
  stake numeric(18,2) not null,          -- or credits
  currency text not null default 'CREDITS',
  server_seed_id uuid not null references server_seeds(id),
  server_seed_hash text not null,        -- convenience copy
  client_seed text not null,
  nonce bigint not null,                 -- per-user/game counter
  round_salt text not null,              -- e.g. round id or UUID
  outcome jsonb not null,                -- e.g. {result:"HEADS", payout:2}
  proof jsonb not null,                  -- {serverSeedHash, clientSeed, nonce, roundSalt, hmacs:[...]}
  exposure_delta numeric(18,2) not null, -- +/-
  finalized boolean not null default true
);

-- Risk & limits
create table risk_limits (
  id uuid primary key default gen_random_uuid(),
  game_id text not null,
  max_stake numeric(18,2) not null,
  max_payout numeric(18,2) not null,
  enabled boolean not null default true
);
`
**Indexes & integrity**
• Index `game_rounds` on `(user_id, created_at desc)`, `(server_seed_id)`.
• Use **generated columns** or triggers for checks (e.g., payout ≤ max_payout).**
5) RLS & security (high-level)**
• `game_rounds`: **SELECT** where `user_id = auth.uid()`; INSERT via **Edge Function** service role only (clients never write outcomes directly).
• `server_seeds`: only **SELECT server_seed_hash, rotates_at** to *all*; **server_seed** (plaintext) never exposed except to a controlled **reveal endpoint** *after rotation*.
• `risk_limits`: readable by Edge only; public endpoint can surface derived read-only caps.**
6) Edge Function: create round (canonical flow)**

`// /functions/create_round/index.ts
import { serve } from "https://deno.land/std/http/server.ts";
import { createClient } from "https://esm.sh/@supabase/supabase-js@2";

serve(async (req) => {
  try {
    const supabase = createClient(Deno.env.get("SUPABASE_URL")!, Deno.env.get("SUPABASE_SERVICE_ROLE_KEY")!);
    const { gameId, stake, clientSeed, nonce } = await req.json();

    // 1) Load active server seed (id, hash, plaintext from KMS/pgcrypto)
    const { data: seed } = await supabase.rpc("get_active_server_seed"); // build as a Postgres function that decrypts
    if (!seed) return new Response("No active seed", { status: 503 });

    // 2) Compose PRNG stream & run game math (deterministic)
    const roundSalt = crypto.randomUUID(); // included in proof; not secret
    const outcome = await computeOutcome({
      gameId,
      serverSeed: seed.server_seed_plaintext,
      clientSeed,
      nonce,
      roundSalt
    });

    // 3) Risk checks (stake, potential payout caps)
    await enforceRisk(supabase, gameId, stake, outcome.payout);

    // 4) Write immutable round
    const proof = makeProof(seed.server_seed_hash, clientSeed, nonce, roundSalt, outcome.hmacs);
    const { error } = await supabase.from("game_rounds").insert({
      user_id: outcome.userId,
      game_id: gameId,
      math_version: outcome.mathVersion,
      stake, currency: "CREDITS",
      server_seed_id: seed.id,
      server_seed_hash: seed.server_seed_hash,
      client_seed: clientSeed,
      nonce,
      round_salt: roundSalt,
      outcome,
      proof,
      exposure_delta: Number(outcome.payout) - Number(stake)
    });
    if (error) throw error;

    // 5) Return player-facing payload
    return Response.json({
      result: outcome.playerView,
      proof,
      serverSeedHash: seed.server_seed_hash,
      nonce,
      roundSalt
    });

  } catch (e) {
    console.error(e);
    return new Response("Error", { status: 500 });
  }
});
`**Note:** `get_active_server_seed` should decrypt `server_seed` using pgcrypto or KMS; keep service-role access constrained to Edge only.**
7) Client usage (React, TS)**

`// capture clientSeed once per session (or let player set it)
const defaultClientSeed = crypto.getRandomValues(new Uint32Array(2)).join("-");
localStorage.setItem("disco:clientSeed", defaultClientSeed);

// when playing:
const res = await fetch("/functions/v1/create_round", {
  method: "POST",
  headers: { "Content-Type": "application/json", Authorization: `Bearer ${supabase.auth.session()?.access_token}` },
  body: JSON.stringify({
    gameId: "coin_flip_v1",
    stake: 10,
    clientSeed: localStorage.getItem("disco:clientSeed"),
    nonce: userRoundCounter, // maintained per user/game in DB or client then verified server-side
  })
});
const data = await res.json();
// Display data.result & render a “Verify” link that recomputes locally using serverSeed (after reveal)
`**
8) Seed rotation & reveal**
• **Rotation cadence**: e.g., hourly or daily depending on volume.
• On rotation:
    1. Mark old seed `active=false`; **publish its plaintext** to a **read-only “reveal” table**.
    2. Generate new seed; store its **hash** publicly before first round.
• Verification page lets anyone recompute outcomes from the transcript:
    ◦ Inputs: `serverSeed (revealed)`, `clientSeed`, `nonce`, `roundSalt`, `gameId`, `math_version`.
    ◦ Re-run the same HMAC pipeline in the browser.**
9) Risk & exposure controls (legal best practice)**
• **Do not** alter outcomes in real-time.
• Manage exposure via:
    ◦ **max_stake / max_payout** per game/segment.
    ◦ **cool-offs** / per-user velocity limits.
    ◦ **jackpot insurance** (for relevant games).
    ◦ **geo-fencing and KYC thresholds** at the session level (Edge check before play).
• Add simple **operator dashboards** to watch rolling RTP, variance, and session anomalies.**
10) Auditing and immutability**
• Append-only `game_rounds`; never UPDATE outcome fields.
• Periodic **hash-chain**:
    ◦ Store `round_chain_hash = SHA256(prev_round_chain_hash || current_round_row_hash)` to create a tamper-evident ledger.
• Write **WORM snapshots** (e.g., nightly) to Supabase storage with signed checksum in a second location.**
11) Math specs & simulation**
• Store **math JSON** (weights, paytables, cap rules) in a versioned table; reference `math_version` in rounds.
• Build a **sim harness** (Node/TS) to run **≥1e8** trials per game variant to confirm RTP/volatility before enabling:

`// Pseudocode for CI sim
for (let i=0; i<1e7; i++) {
  const r = await computeOutcome({ serverSeed: "SIM", clientSeed:`u${i}`, nonce:i, roundSalt:`s${i}`});
  // accumulate stats...
}
// assert |empiricalRTP - targetRTP| < epsilon; fail CI if not met
`**
12) Observability**
• Log edges: latency, error codes, round writes/sec, payout distributions.
• **Metrics to watch**: rolling RTP by game & cohort, GGR, NGR, session length, repeat rate, exposure by tail events.**
13) Compliance hooks (future-proofing)**
• Per-round **KYC state** snapshot, **geo country**, **responsible-play flags**.
• Easy export (`COPY TO`) of round rows for **lab audits** (GLI / iTech).
• If/when you pursue lab certification, freeze the **math_version** and **Edge artefacts**; sign build artefacts.**
Quick checklist to ship MVP safely**
1. Implement HMAC-based PRNG + weighted outcome helpers (server only).
2. Create `server_seeds`, `game_rounds`, `risk_limits` tables + RLS.
3. Edge Function `create_round` with deterministic math & proof object.
4. Client **clientSeed** entry + proof UI (serverSeedHash, nonce, roundSalt).
5. Seed rotation job + public **reveal** endpoint/table.
6. Sim harness for RTP/variance; CI gate on math changes.
7. Risk caps & kill-switch flags.
8. Hash-chain audit and nightly snapshots.
If you want, I can drop **ready-to-paste Supabase SQL (with RLS policies)** and a **typed **`**computeOutcome**`** module** for your coin-flip, dice, and mines variants next.

---

simple RNG::

Great—let’s keep it dead simple, server-side only, with a fixed expected RTP of **0.90** and zero client influence. Below is a minimal pattern you can paste into Supabase/Edge today and iterate later into “provably fair”.**
Goal**
• **Backend decides the outcome** (no client calc).
• **Fixed RTP=0.90** by design (expected payout = 0.9 × stake).
• **Binary outcome** to start (either 0x or 2x), which keeps the math trivial and variance understandable.
**RTP math (binary):**

Let probability of a 2× win be `p`. Expected multiplier = `2*p + 0*(1-p) = 2p`.

Set `2p = 0.9 → p = 0.45`.

So: 45% win for **2×**, 55% lose for **0×** ⇒ expected 0.9× on every wager.**
1) Minimal tables (SQL)**

`-- Players’ rounds/outcomes (append-only)
create table if not exists rng_rounds (
  id uuid primary key default gen_random_uuid(),
  created_at timestamptz not null default now(),
  user_id uuid not null references auth.users(id),
  game_id text not null default 'rng_v0_bin_2x',
  stake numeric(18,2) not null check (stake > 0),
  currency text not null default 'CREDITS',
  rtp_target numeric(5,4) not null default 0.90,
  win_prob numeric(5,4) not null default 0.45, -- p(win 2x)
  random_u numeric(18,10) not null,            -- stored for audit
  result_multiplier numeric(6,3) not null,     -- 0.000 or 2.000
  payout numeric(18,2) not null,               -- stake * multiplier
  finalized boolean not null default true
);

-- Only the player can read their rounds
alter table rng_rounds enable row level security;

create policy rng_rounds_select_self
on rng_rounds for select
to authenticated
using (auth.uid() = user_id);

-- Prevent direct writes from clients
revoke insert, update, delete on rng_rounds from anon, authenticated;
`
*(This keeps it lean: one table; no seeds/nonce yet. You can add those later.)***
2) Edge Function (TypeScript on Deno)**
**Route:** `/functions/create_rng_round`
**Behaviour:**
• Auth required.
• Reads `{ stake }`.
• Draws one secure random `u ∈ [0,1)`.
• If `u < 0.45` → `multiplier=2.0`, else `0.0`.
• Writes the row and returns `{ multiplier, payout }`.

`// supabase/functions/create_rng_round/index.ts
import { serve } from "https://deno.land/std@0.224.0/http/server.ts";
import { createClient } from "https://esm.sh/@supabase/supabase-js@2";

function uniform01(): number {
  // 53-bit uniform in [0,1)
  const a = new Uint32Array(2);
  crypto.getRandomValues(a);
  // Take 21 high bits of a[0] and 32 bits of a[1] => 53 bits
  const hi = a[0] >>> 11;              // 21 bits
  const lo = a[1];                     // 32 bits
  const val = (hi * 2 ** 32) + lo;     // 53-bit integer
  return val / 2 ** 53;
}

serve(async (req) => {
  try {
    if (req.method !== "POST") {
      return new Response("Method not allowed", { status: 405 });
    }

    // Auth: require a valid user
    const supabase = createClient(
      Deno.env.get("SUPABASE_URL")!,
      Deno.env.get("SUPABASE_SERVICE_ROLE_KEY")!
    );

    const authHeader = req.headers.get("Authorization") || "";
    const jwt = authHeader.replace("Bearer ", "");
    const { data: auth } = await supabase.auth.getUser(jwt);
    const user = auth?.user;
    if (!user) return new Response("Unauthorised", { status: 401 });

    const { stake, currency = "CREDITS" } = await req.json();
    if (!stake || Number(stake) <= 0) {
      return new Response("Invalid stake", { status: 400 });
    }

    // Fixed RTP config (binary: 2x win with p=0.45)
    const RTP_TARGET = 0.90;
    const WIN_PROB = 0.45;    // 2x if u < 0.45 else 0x

    // Draw one secure random number server-side
    const u = uniform01();

    const multiplier = u < WIN_PROB ? 2.0 : 0.0;
    const payout = Number((Number(stake) * multiplier).toFixed(2));

    // Persist
    const { error } = await supabase
      .from("rng_rounds")
      .insert({
        user_id: user.id,
        stake,
        currency,
        rtp_target: RTP_TARGET,
        win_prob: WIN_PROB,
        random_u: u,
        result_multiplier: multiplier,
        payout,
      });

    if (error) throw error;

    return Response.json({
      ok: true,
      gameId: "rng_v0_bin_2x",
      stake,
      currency,
      multiplier,
      payout,
      // For transparency (optional UI copy):
      rtpTarget: RTP_TARGET,
      winProbability: WIN_PROB,
    });
  } catch (e) {
    console.error(e);
    return new Response("Server error", { status: 500 });
  }
});
`**
3) Frontend call (no outcome logic client-side)**

`const res = await fetch("/functions/v1/create_rng_round", {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
    Authorization: `Bearer ${(await supabase.auth.getSession()).data.session?.access_token}`,
  },
  body: JSON.stringify({ stake: 10, currency: "CREDITS" }),
});
const data = await res.json();
// data.multiplier and data.payout come from the server.
// Render the result; do not compute anything client-side.
`**
4) Notes & trade-offs (intentionally simple)**
• **Why binary 0× / 2×?** It perfectly locks RTP with one parameter (`p=0.45`) and is trivial to reason about. You can later add more tiers (e.g., 0×/0.5×/1×/3× with probabilities summing to expected 0.9×).
• **Variance:** RTP=0.9 is an expectation over many rounds; short-run results will swing. Binary outcomes keep variance high but easy to simulate.
• **Auditability:** We store `random_u` for quick sanity checks. This is **not** “provably fair”; it’s just server-side RNG. You can bolt on seed commitment later without changing the API contract.
• **Security:** RLS prevents players from reading others’ rounds; only the Edge function (service role) can insert. No client-side writes to `rng_rounds`.
• **Caps (optional quick add):** Add a simple guard in the function to block `stake > MAX_STAKE` and/or `payout > MAX_PAYOUT` if you want a basic exposure limit.**
5) Easy extensions when you’re ready**
• **Provably fair:** Replace `uniform01()` with an HMAC/HKDF stream using a hidden `serverSeed` + public `serverSeedHash`; publish the seed on rotation.
• **Risk controls:** Add `risk_limits` and enforce `payout ≤ max_payout` with a DB CHECK.
• **Telemetry:** Track rolling RTP by user/cohort to spot anomalies.
If you want, I can turn this into a ready-to-run Supabase CLI scaffold (function + SQL migration + a tiny React hook) next.