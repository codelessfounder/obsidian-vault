---

---


There are two upload photo buttons 

- one for when a user has no recent sessions 
- one for when a user has a recent session in their cart

this needs to be consolidated at some point

---

coinflip

- winnings should show total payout (bet plus winnings), not just the won amount 


---

Linking recent session to gameplay is causing errors on a new upload 

---

Some tiles (bomb) aren’t clickable during mines

---

We need separate components on homepage uploading a new photo and continuing a session

---

There are 3 main components: 

- Upload a new photo
- Sessions 
- Gameplay 

The output from upload a new photo and sessions is the same: 

- 1 new session 
- 1 cart 
- X cart items 

Both of these components will feed this through to the gameplay component so the user can play that session 

[Carttotal.t](http://carttotal.tax/)sx is present in all of these components. 

- we’ll need 3 
- This element needs to be reusable 
- One of these problems is that we’re using the same carttotal and there’s too many conditional states attached to it 

Unauthenticated users and Authenticated users with no previous session::

- empty cart
- Upload new photo yout

---

the disco loaders are not consistent throughout the app

---

the carttotal.tsx in upload.tsx handles the image preview before you analyse

---

to do 22 september 2025:

- [x] confetti appears when a user navigates from recent session to gameplay 
- [x] upload.tsx visible when a user navigates from recent session
- [x] coins game is not effecting the progressbar like mines is
- [x] on page load, the sessions progress bar value should have the same animation as the one in gameplay
- [x] progressbar in sessionhistorytable displays item amount, not the total_payout from sessions
- [x] mines bomb and some tiles are not clickable/working

---

- [ ] fix demo page load 
- [ ] add cart header to analysing image display 
- [ ] when a session from sessionhistory table is played, that session should become the most recent session 
- [ ] change any UI saying session to Cart
- [ ] having nothing in your cart means you can’t upload anything to your 
- [ ] recentbets should not be visible when a user is a playing a game

---




---

~~we need a new column called “outcomes” in supabase, where entries are generated on the backend ~~

---

we need to find a way to make the user feel like theyre winning discounts more - improve the contexualisation of discounts:

- screen fades darker while the progressbar is going up or down every time a bet ends

---

~~BUG: when a user gets 21 with 3 cards, it shows as a lost~~

---

client seed 

![[image 1.png]]


---

login functionality with metamask (can be done on rainbet) 

copy user authentication from rainbet 

---

percentage for progressbar instead of amount?

---

head to head betting - social playing to see who pays for things 

---

RNG server side outcomes have been implemented, but MANY API calls are made per bet, which increases latency. 

- in future, create one edge function with multiple actions, instead of many edge functions 
- implement provably fair approach with seed logic

---

when a user gets over 100%, the session should end. they should be: 

- suggested by disco to play for new items 
- able to share their win with friends 

---

geoblocking (popup only)

---

FIX ANALYSE PHOTO DUPE IT LOOKS TRASH


---

cartotal or progressbar should be pinned to the top beneath header for context

---


---

~~Split sessionhistory table into completed and ongoing ~~

- ~~sort by closest to 100% for ongoing ~~

---

Implement perplexity AI free for search API and image analysis 

Add ability to add previous items to play for 

Update logo to this 

![[IMG_0072.png]]


---

add chat bar for new users

---

~~Gameplay.tsx should be visible AS SOON as they click a tile on the mainpage, but greyed out until the user selects which game to play for. ~~


---


Eventually, the right sidebar will become a component and copies of upload.tsx and sessions.tsx will live in there 

---

Style betamount and the game component just like duel (side by side touching ting)

---

carttotal.tsx should persist across the games:

- if the user plays sports betting or table games, their wins and losses will contributed or not 

---

Vite is for lightweight singlepage apps, Next.js is for full stack, high performance production ready applications

---

How should Disco reward the user (visually) for getting to 100% off their item?

we need to change instant blackjack win logic so the anticipatory period is extended

---

URL parameters need to be added because:

- No deep linking / sharing. Users can’t bookmark a particular state or send a link that opens the same view.
- Back/forward behaviour can be unexpected (browser history won’t reflect view changes).
- Poor SEO for pages that should be indexed (if that matters).
- Harder to restore state after a refresh (unless you persist to storage).
- Harder to measure and attribute in analytics (no distinct URLs to track).


---

we need forced scroll to top after session data is passed to gameplay from cartsidebar 

---

**Likely Performance Bottlenecks**

- **Large, static UI bundle**

All front-end routes share the main bundle. The codebase has many UI components under src/components/ui, but there’s no sign of route-based code splitting or dynamic imports. Any page load pulls in the entire component set, making the initial payload heavy and slow to parse. Network waterfalls in production would likely show this as large JS downloads and long main-thread busy time.

- **Global state cascades**

The central src/stores files export Zustand stores that get referenced across numerous components. Some stores appear to bundle a lot of concerns (e.g., wallet connection, session/game state, animation state). When a single value changes, many subscribers re-render. This is especially expensive in React trees with deep component nesting. You can confirm by profiling React DevTools: look for repeated renders after a single coin-flip event or wallet update.

- **Rendering large lists repeatedly**

Certain components (like Sessions.tsx) render large tables or grids with animation wrappers. Without virtualization or memoization, each update forces the entire list to re-render—especially problematic on mobile Safari. Watch for map + motion combinations; profiling should show a lot of time under “reconcileChildren”.

- **Animation-heavy transitions**

Framer Motion is used throughout. Animations on modals, cards, and background effects all run concurrently. When combined with large DOM repaint regions (e.g., gradients, glassmorphism), the GPU and CPU both get taxed, resulting in dropped frames on lower-end devices. Check the Frame Timeline in Chrome DevTools—the purple “Rendering” bars will be thick during state transitions.

- **Expensive third-party SDKs**

Wallet integrations pull in ethers.js and other crypto libraries. Those libraries are large and initialize async connections. They likely run on every load because wallet state lives in a global store. Lazy-loading the wallet SDK and deferring initialization until the user actually connects would improve startup.

- **Server API chatter**

The app fetches game session data, wallet balances, and leaderboard info on mount. Multiple components trigger their own fetches, often with overlapping data. You’ll see N+1 patterns if you analyze network logs: e.g., one module fetches /sessions, another fetches /session/:id, and yet another calls /wallet. Each request waits for Supabase or backend API responses, elongating render time.

- **Image assets and background effects**

Styled backgrounds under public/ and src/assets/ are high-resolution PNGs and gradients. They are used without responsive variants or lazy loading, forcing large downloads even on small screens. Check Largest Contentful Paint metrics; images probably dominate.

## **Follow-Up Checks**

- Run Lighthouse (mobile + desktop) to quantify first contentful paint, interaction readiness, and main-thread blocking time.
- Profile with React DevTools to confirm re-render hotspots.
- Capture a performance recording in Chrome and filter to “Scripting” and “Rendering” to see where frame budget is spent.
- Inspect bundle size via next build / npm run build with ANALYZE=true to pinpoint largest chunks.


---

Casino sounds:

- [Freesound - Search](https://freesound.org/search/?q=coin&f=&s=Automatic+by+relevance&si_tags=0&si_name=0&si_description=0&si_packname=0&si_sound_id=0&si_username=0&d0=0&d1=*&ig=0&r=0&g=1&dp=0&cm=0&mm=0)
- [Free Casino Sound Effects Download - Pixabay](https://pixabay.com/sound-effects/search/casino/)
- [Download Free Casino Sound Effects | Mixkit](https://mixkit.co/free-sound-effects/casino/)


---

Need to change the front page to tell users about the USP 

---

We need to create slots

- a girl said it was easily the most played game 

---

$5000 per week gets you to be a VIP


---

cart preview and cart price edit are priority 

---

OpenSpec Questions:

1. Create your first change proposal:
"I want to add [YOUR FEATURE HERE]. Please create an
OpenSpec change proposal for this feature"
2. Learn the OpenSpec workflow:
"Please explain the OpenSpec workflow from openspec/AGENTS.md
and how I should work with you on this project"


---

we need a slots game

---

building a vite typsecript supabase casino: considerations - 

Short answer: technically — **yes**. Vite + TypeScript for the frontend and Supabase for much of the backend **can** get you a working online-casino prototype quickly. But there are heavy legal, payments, fairness and security requirements you **must** handle before you ever take real money or market to players. Below I’ll explain the technical fit, the hard non-technical blocking points, and a practical architecture + checklist you can follow.

# Technical fit (what works well)

- **Vite + TypeScript** is an excellent modern frontend stack: fast dev server, HMR, first-class TypeScript support — great for building UI and game clients. [vitejs+1](https://vite.dev/?utm_source=chatgpt.com)
- **Supabase** gives you Postgres, Auth, Storage, Realtime and Edge Functions (TypeScript serverless at the edge) — useful building blocks for user auth, game state, presence, and lightweight server logic. Realtime is suitable for low-latency game events / presence. Edge Functions and DB functions let you run server-side logic close to users. [Supabase+2Supabase+2](https://supabase.com/docs/guides/getting-started/features?utm_source=chatgpt.com)

# Critical non-technical blockers (dealbreakers unless resolved)

- **Licensing & regulation.** Online gambling is heavily regulated (examples: UK Gambling Commission LCCP). If you accept bets from people in regulated jurisdictions you generally need an operator licence and must follow strict rules (age checks, affordability, advertising limits, reporting, etc.). Running without a licence is illegal in many countries. **Get legal advice early.** [Gambling Commission+1](https://www.gamblingcommission.gov.uk/licensees-and-businesses/lccp/online?utm_source=chatgpt.com)
- **Payments.** Major payment providers (Stripe etc.) explicitly prohibit processing gambling/lotteries for many use cases. You’ll need specialist PSPs that support gambling and comply with AML/KYC rules — these providers do extra underwriting and paperwork. Don’t assume consumer payment rails will accept you. [Stripe+1](https://stripe.com/en-th/legal/restricted-businesses?utm_source=chatgpt.com)
- **Fairness & RNG auditability.** Regulated operators must prove games are fair. Many casinos implement server-side cryptographically secure RNG and/or “provably fair” schemes (especially crypto casinos). This needs careful design and third-party auditing. [cloudbet.com+1](https://www.cloudbet.com/en/academy/crypto-betting-basics/provably-fair-gaming?utm_source=chatgpt.com)

# Recommended architecture (practical)

3. **Frontend (Vite + TS)**
    - Build UI/game client with Vite + React/Preact + TypeScript. Use game loops / rendering separate from networking code. [vitejs](https://vite.dev/?utm_source=chatgpt.com)
4. **Auth & users (Supabase Auth)**
    - Use Supabase Auth for signups; enforce email/2FA. But do **not** rely on client for sensitive decisions.
5. **Server authoritative game logic**
    - **Run all RNG and win/loss determination server-side** (Edge Functions or dedicated backend). Keep client as display only. Supabase Edge Functions are convenient for TS server code but for high throughput consider dedicated Node/Go game servers. (Edge Functions are great but consider concurrency, cold starts, and audit logging needs.) [Supabase+1](https://supabase.com/docs/guides/getting-started/features?utm_source=chatgpt.com)
6. **Database & auditing (Postgres)**
    - Use Postgres for transactional records, ledgers and immutable audit trails (transactional logs, balances). Use database functions and strict RBAC / RLS to prevent tampering. [Supabase](https://supabase.com/docs/guides/database/functions?utm_source=chatgpt.com)
7. **Realtime & presence**
    - Use Supabase Realtime for presence, lobby updates, and low-latency events — but **don’t** rely on it for authoritative RNG outcomes (those must be posted from server to DB). [Supabase](https://supabase.com/docs/guides/realtime?utm_source=chatgpt.com)
8. **Payments & KYC**
    - Integrate a gambling-friendly PSP and a KYC/AML provider. Store KYC results and transaction records in your DB. Remember PSPs usually require business underwriting and compliance docs. [Stripe+1](https://stripe.com/en-th/legal/restricted-businesses?utm_source=chatgpt.com)
9. **Fairness & audits**
    - Implement cryptographically secure RNG (e.g., server CSPRNG + HMAC commitments or provably fair scheme) and retain full logs so independent auditors can verify. Consider third-party RNG/certification. [cloudbet.com+1](https://www.cloudbet.com/en/academy/crypto-betting-basics/provably-fair-gaming?utm_source=chatgpt.com)

# Pros and cons of using Supabase

- **Pros:** fast to build, Postgres features, Realtime and Edge Functions make prototyping much faster. Good DX for TS teams. [Supabase+1](https://supabase.com/docs/guides/getting-started/features?utm_source=chatgpt.com)
- **Cons / cautions:** Supabase is a general backend — you’ll likely need additional infrastructure for:
    - High-throughput deterministic game servers (if your games are real-time and competitive).
    - Compliance reporting, heavy audit retention, and secure key management (HSM) for RNG secrets.
    - Advanced rate-limiting and anti-fraud tooling which you may need to integrate separately.

# Practical checklist before you launch with real money

- ✅ Talk to a gambling-experienced lawyer about licences for your target countries. [Gambling Commission](https://www.gamblingcommission.gov.uk/licensees-and-businesses/lccp/online?utm_source=chatgpt.com)
- ✅ Confirm acceptable payment providers and their onboarding requirements (Stripe is likely **not** an option). [Stripe](https://stripe.com/en-th/legal/restricted-businesses?utm_source=chatgpt.com)
- ✅ Design server-side RNG, provably-fair options, and plan for third-party audits. [cloudbet.com+1](https://www.cloudbet.com/en/academy/crypto-betting-basics/provably-fair-gaming?utm_source=chatgpt.com)
- ✅ Put in place KYC/AML, age verification, and responsible-gambling features. [Gambling Commission](https://www.gamblingcommission.gov.uk/licensees-and-businesses/lccp/online?utm_source=chatgpt.com)
- ✅ Use secure logging, immutable transaction ledgers, and maintain backups/retention for audits. [Supabase](https://supabase.com/docs/guides/database/functions?utm_source=chatgpt.com)
- ✅ Stress test real-time performance — Realtime is fine for many use cases, but load may require dedicated game servers. [Supabase](https://supabase.com/docs/guides/realtime?utm_source=chatgpt.com)

# Final recommendation

Start with **Vite + TypeScript** for your client and **Supabase** for an MVP and proof-of-concept (auth, DB, realtime, Edge Functions). Use them to build the UX and the non-money game flow. But **don’t** accept real money or market publicly until you’ve locked down licensing, payments, server-authoritative RNG, KYC/AML and third-party audits. For a regulated, production money platform expect to integrate specialized providers and possibly move some services off Supabase into dedicated, certified systems.

If you want, I can:

- sketch a starter repo architecture (file layout + which parts live on Supabase vs dedicated servers), or
- draft a one-page compliance checklist tailored to one jurisdiction (pick a country), or
- show a minimal provably-fair design (server-client HMAC approach) you could prototype.

Which of those would help you next?

### You said:

yes but aside from legal regulations etc, is it heavy duty enough technically to scale and handle many users

### ChatGPT said:

Thought for 10s

Short answer: yes — **technically** Vite + TypeScript for the client and Supabase for much of the backend *can* scale to support a large user base, but only if you design around a few concrete platform limits and add a few classic scale components (connection pooling, dedicated real-time/game servers, caches/queues, read replicas). Below I’ll call out the main bottlenecks, what to do about each, and a compact scalable-architecture pattern you can implement.

# Quick verdict

- Great for rapid iteration and an MVP: static client built with Vite (fast builds + static hosting) + Supabase (Postgres, Auth, Realtime, Edge Functions). [vitejs+1](https://vite.dev/guide/build?utm_source=chatgpt.com)
- Not “one-box handles everything” at very large scale. You’ll need extra infra once you move beyond prototype traffic (connection pooling, dedicated realtime/gaming services, caches, message brokers). [Supabase+1](https://supabase.com/blog/supavisor-1-million?utm_source=chatgpt.com)

# Primary technical pain points & mitigations

10. **Postgres connection limits** — Postgres on Supabase (and on most managed DBs) has finite connections; naive many-connection patterns will hit limits. Use PgBouncer / Supavisor (connection pooling) and design your app to reuse pooled connections. For heavy scale you’ll need read-replicas and possibly partitioning/sharding. [Supabase+2Supabase+2](https://supabase.com/docs/guides/database/connecting-to-postgres?utm_source=chatgpt.com)
11. **Realtime / WebSocket quotas** — Supabase Realtime is capable but has quotas (concurrent connections, message rates). For massive concurrent real-time players you may hit quotas; for game lobbies or presence Supabase is fine, but for very high message rates consider a dedicated realtime service (e.g., Ably, Pusher, or your own socket cluster). [Supabase+1](https://supabase.com/docs/guides/realtime/quotas?utm_source=chatgpt.com)
12. **Edge Functions / serverless limits** — Edge Functions are convenient for server-side logic, but watch for cold starts, per-instance limits and execution-time patterns. Keep heavy, latency-sensitive game logic on dedicated servers rather than many cold serverless invocations. (Recent Supabase improvements reduce cold starts, but you should still benchmark your workload.) [GitHub+2Supabase+2](https://github.com/orgs/supabase/discussions/29301?utm_source=chatgpt.com)
13. **Throughput & determinism for game logic** — Any money/competitive game must be server-authoritative and deterministic. For very high throughput (thousands of game outcomes/second) run dedicated horizontally-scalable game servers or a pool of workers instead of relying purely on Edge Functions/DB triggers.
14. **State, caching and rate-limits** — Use Redis (or another in-memory store) for ephemeral state, leaderboards, rate limiting and locking. Use message queues (Kafka/Rabbit/SQS) to buffer spikes and to decouple writes to the ledger from user-facing flows.

# Practical scalable architecture (recommended)

- Static assets & client: build with Vite → deploy to CDN (Cloudflare/S3+CloudFront/Netlify/Vercel). (fast, cheap, scales automatically). [vitejs](https://vite.dev/guide/build?utm_source=chatgpt.com)
- Auth & user DB: Supabase Auth + Postgres for canonical data, but protect Postgres with PgBouncer/Supavisor and use read replicas for analytics/reads. [Supabase+1](https://supabase.com/docs/guides/database/connecting-to-postgres?utm_source=chatgpt.com)
- Realtime/presence: start with Supabase Realtime for lobbies/presence. If you anticipate >10k concurrent real-time players or heavy messaging, evaluate a dedicated realtime provider or a horizontally-scaled socket cluster. [Ably Realtime+1](https://ably.com/compare/pusher-vs-supabase?utm_source=chatgpt.com)
- Game authority & RNG: run server-authoritative logic on a pool of dedicated servers (Kubernetes or autoscaling VM group) — keep RNG secrets out of Edge/clients. Use Edge Functions for less latency-sensitive endpoints only. [Supabase](https://supabase.com/docs/guides/functions/architecture?utm_source=chatgpt.com)
- Cache & locking: Redis for ephemeral state, locks, counters, leaderboards.
- Queue & workers: message queue + worker pool to process settlement, payouts, audit logging asynchronously and reliably.
- Monitoring & autoscaling: set up Prometheus/Grafana / Datadog for latency, DB connections, websocket counts, function cold starts, queue lengths.

# Concrete scale tips & numbers (practical)

- Don’t open a DB connection per request/thread — use PgBouncer pooled connections; Supabase tooling already uses pooling (Supavisor/PgBouncer). Upgrade compute tier if pool limits become a ceiling. [Supabase+1](https://supabase.com/blog/supavisor-1-million?utm_source=chatgpt.com)
- Measure your Realtime usage early — watch concurrent sockets and messages/sec. Supabase documents quotas and will surface quota errors when exceeded. Plan fallbacks. [Supabase](https://supabase.com/docs/guides/realtime/quotas?utm_source=chatgpt.com)
- Push static assets & game logic assets to CDN and use client-side prediction only for UX; always confirm authoritative result from the server.
- Benchmark: simulate realistic client behavior (connects/sec, messages/sec, game outcome rate) and scale each component (DB, realtime, game servers) until you find the bottleneck — don’t guess.

# When to move off “Supabase-only”

- If you need >10k concurrent real-time players, sustained thousands of messages/sec, or sub-50ms authoritative game outcome latency, plan to run specialized realtime/game servers + dedicated DB cluster and caching layer. Supabase remains useful for auth, user data and audit logs, but critical hot paths should be on infra built for low latency and extreme concurrency. [Ably Realtime+1](https://ably.com/compare/pusher-vs-supabase?utm_source=chatgpt.com)

# Short checklist to get from MVP → large scale

15. Add PgBouncer / Supavisor and set sensible pool sizes. [Supabase+1](https://supabase.com/docs/guides/database/connecting-to-postgres?utm_source=chatgpt.com)
16. Add Redis for ephemeral state and rate limiting.
17. Separate server-authoritative game engines (K8s or managed VM autoscaling).
18. If heavy realtime: test Supabase Realtime quotas and evaluate a dedicated realtime provider. [Supabase+1](https://supabase.com/docs/guides/realtime/quotas?utm_source=chatgpt.com)
19. Put robust monitoring and automated scaling on every layer.
20. Load test with realistic scenarios (connects, plays, bursts).

---

If you want, I can:

- sketch a concrete infra diagram (Supabase + Redis + game server pool + queue + CDN) with component responsibilities, or
- produce a short load-test plan + example k6 scenarios to simulate 10k concurrent players

---

android users need to be able to natively upload photos

---

Type of odds: 

Heads Up 

Chance 

Parlay

---

sweepstakes

---

leaderboard - see Duel

---

game mode change: resets cart total. item data should persist. 

---

Micro lottery: 

- your groceries paid for for 1 year 
- Toothpaste for a lifetime 
- 10 years of toilet paper 

---

Social/head to head is a priority 

---

add a “discount” game mode to head to head and chance”

---

- [ ] Coins toggle display 
![[Screenshot_2025-12-10_at_1.16.42_pm.png]]
- [ ] coins balance
![[Screenshot_2025-12-10_at_1.16.52_pm.png]]



---

“”*dont see the product you’re looking for? upload a photo of the item or take a photo instantly and Disco will calculate the max value you can get for it”*

---

Implement Phaser for table games 

---

prod strat 

- 2 new games (wheel and slots)
- Battles 
- cards 
- search for items 
- update carttoal to itemcontext and add to landingpage

---

[www.coolbet.com](https://www.coolbet.com/en/welcome)

has poker, and a language switching feature


---

Item Niche:

- Real estate 
- Cars 
- Watches 
- Shoes 

---

item upload

- users can upload items “for sale” for people to gamble on and win, and then they share in the profits with Disco
    - e.g. a user lists their air jordans for 300
    - users bet 5000 on that item 
    - the seller is given 450 on that item by Disco instead of 300 
- the benefit of this is that users will be able to earn substantially more than if they listed on a regular marketplace 


---

Disco paid boosts:

coinflip: respin 

Mines: re-pick tile 

Blackjack: TBA


---

Duel vs Disco Provably fair verification logic:

## **Differences**

**1. Verification approach**

**Duel's approach (outcome regeneration):**

- Regenerates the actual game outcome using the same algorithm
- For Blackjack: shows the next 50 cards that would be dealt
- For Mines: shows the exact bomb positions
- Proves fairness and shows what the outcome was

**Our current approach (HMAC verification):**

- Verifies the HMAC matches the stored value
- Proves the randomness was fair
- Does not regenerate or display the actual game outcome

**2. Why Duel has a game dropdown**

Each game uses different verification logic:

- Mines: needs minesCount and gridSize to regenerate bomb positions using Fisher-Yates shuffle
- Blackjack: uses a cursor-based approach to generate cards sequentially
- Coin Flip: simpler (just one random number)

The dropdown selects the correct verification algorithm.

**3. Our implementation differences**

**Blackjack:**

- Duel: Uses HMAC-SHA256 with cursor-based card generation (clientSeed:nonce:cursor)
- Ours: Uses HMAC-SHA512 with nonce increments (2 nonces per card: suit + value)
- Different algorithms = different verification code

**Mines:**

- Duel: Uses Fisher-Yates shuffle with HMAC-SHA256, needs minesCount and gridSize
- Ours: Uses HMAC-SHA512 with a single random number for bomb position (Heads Up) or threshold (Chance)
- Different algorithms = different verification code

## **Should we implement game-specific verification?**

Pros:

- More transparent: users see the actual outcome
- Better UX: verifies fairness and shows what happened
- Aligns with industry practice

Cons:

- Requires game-specific verification code for each game
- Must match our server-side algorithms exactly
- More complex UI (game dropdown, game-specific fields)

## **Recommendation**

Implement game-specific verification to:

21. Match Duel's transparency level
22. Provide better user experience
23. Enable full outcome verification

This would require:

24. Adding a game dropdown (Coin Flip, Mines, Blackjack)
25. Creating game-specific verification functions matching our server-side logic
26. Adding game-specific fields (e.g., minesCount for Mines)
27. Regenerating outcomes to show what actually happened

Should I implement game-specific verification matching our server-side algorithms?

---

## SSG implementation plan

```markdown
# SSG Implementation Plan - Static Site Generation for Disco PWA

**Status:** Deferred - Ready to implement when needed  
**Created:** February 2025  
**Estimated Time:** 1-1.5 hours

---

## Overview

Add Static Site Generation (SSG) for 3 static pages (`/`, `/terms`, `/privacy-policy`) while keeping Client-Side Rendering (CSR) for all other pages. This will improve initial load times and SEO for static content.

---

## Pages to Pre-Render

### Phase 1: Static Pages (SSG)
- ✅ `/` - Landing page
  - Mostly static content
  - Form handled client-side (hydration)
  - Spline 3D scene (loads client-side)
- ✅ `/terms` - Terms of Service
  - Fully static
- ✅ `/privacy-policy` - Privacy Policy
  - Fully static

### Phase 2: Keep CSR (No Changes)
- `/home/*` - All authenticated/dynamic pages
- `/home/:gameMode/result/:betId` - Dynamic result pages
- All other routes

---

## Package Selection

**Package:** `vite-react-ssg`

**Why:**
- Works seamlessly with React Router
- Supports hybrid approach (SSG + CSR)
- Minimal configuration required
- Good TypeScript support
- Active maintenance

**Installation:**
```bash
npm install -D vite-react-ssg
```

**Alternative Considered:** `vite-plugin-ssg` (less React Router support)

---

## Implementation Steps

### Step 1: Install Package
```bash
npm install -D vite-react-ssg
```

### Step 2: Update `vite.config.ts`

Add the SSG plugin and configure routes:

```typescript
import { defineConfig } from "vite";
import react from "@vitejs/plugin-react-swc";
import path from "path";
import { ssg } from "vite-react-ssg";

export default defineConfig({
  plugins: [
    react(),
    ssg({
      // Configure which routes to pre-render
      routes: ['/', '/terms', '/privacy-policy'],
      // Keep CSR for other routes
    }),
  ],
  resolve: {
    alias: {
      "@": path.resolve(__dirname, "./src"),
    },
  },
  // ... rest of existing config
});
```

### Step 3: Create SSG Entry Point

Create `src/main-ssg.tsx`:

```typescript
import { StrictMode } from 'react';
import { hydrateRoot } from 'react-dom/client';
import App from './App';

// SSG entry point - hydrates pre-rendered HTML
hydrateRoot(
  document.getElementById('root')!,
  <StrictMode>
    <App />
  </StrictMode>
);
```

### Step 4: Update `index.html`

Ensure it works for both SSG and CSR. May need to check if any changes are needed based on `vite-react-ssg` requirements.

### Step 5: Update Build Script

Modify `package.json` build script (if needed):

```json
{
  "scripts": {
    "build": "vite build && cp public/favicon.ico dist/ && node scripts/generate-sitemap.js",
    "build:preview": "vite build && vite preview"
  }
}
```

### Step 6: Handle Special Cases

#### Landing Page Form
- **Issue:** Form submits to Supabase (client-side)
- **Solution:** Form works after hydration (React handles this)
- **Test:** Ensure form is interactive after JS loads

#### Spline 3D Scene
- **Issue:** Spline loads client-side
- **Solution:** Component loads after hydration
- **Test:** Ensure 3D scene appears correctly

#### SEO Metadata
- **Current:** `react-helmet-async` adds metadata via JS
- **SSG:** Metadata should be in pre-rendered HTML
- **Solution:** Ensure Helmet renders during SSG build
- **Test:** Check HTML source has metadata

#### React Router
- **Issue:** SSG needs to work with React Router
- **Solution:** `vite-react-ssg` handles this automatically
- **Test:** Ensure routing works for both SSG and CSR pages

---

## File Structure Changes

```
src/
├── main.tsx          (existing - CSR entry, dev mode)
├── main-ssg.tsx      (new - SSG entry point)
└── pages/
    ├── LandingPage.tsx      (SSG)
    ├── TermsOfServicePage.tsx (SSG)
    └── PrivacyPolicyPage.tsx  (SSG)
```

---

## Build Output

After build, `dist/` will contain:

```
dist/
├── index.html              (pre-rendered /)
├── terms/
│   └── index.html          (pre-rendered /terms)
├── privacy-policy/
│   └── index.html          (pre-rendered /privacy-policy)
├── assets/                 (JS bundles - same as before)
└── ...                     (other files)
```

---

## Testing Strategy

### Development Testing
1. ✅ Test SSG pages in dev mode (should work as CSR)
2. ✅ Test build process (`npm run build`)
3. ✅ Verify HTML files are generated

### Build Verification
1. ✅ Check `dist/` has pre-rendered HTML files
2. ✅ Open HTML files directly (should see content)
3. ✅ Verify metadata is in HTML source
4. ✅ Check JavaScript still works (hydration)

### Production Testing
1. ✅ Test `/terms` loads fast (should see content immediately)
2. ✅ Test `/privacy-policy` loads fast
3. ✅ Test `/` landing page loads fast
4. ✅ Verify form works on landing page
5. ✅ Test other routes still work (CSR)

### SEO Testing
1. ✅ View page source (should see content, not just `<div id="root">`)
2. ✅ Test with Google Search Console
3. ✅ Test social media previews (Twitter, Facebook)
4. ✅ Run Lighthouse SEO audit

---

## Potential Issues & Solutions

### Issue 1: Hydration Mismatch
- **Problem:** Server HTML doesn't match client render
- **Solution:** Ensure components are hydration-safe
- **Mitigation:** Test thoroughly, use `suppressHydrationWarning` if needed

### Issue 2: Build Time Increase
- **Problem:** SSG adds 30-60s to build
- **Solution:** Only pre-render 3 pages (minimal impact)
- **Acceptable:** Trade-off for better performance

### Issue 3: Dynamic Imports
- **Problem:** Lazy-loaded components may not pre-render
- **Solution:** `vite-react-ssg` handles this automatically
- **Test:** Ensure lazy-loaded components work

### Issue 4: Environment Variables
- **Problem:** Some code may need `window` or browser APIs
- **Solution:** Use conditional checks (`typeof window !== 'undefined'`)
- **Test:** Ensure no SSR errors during build

---

## Rollback Plan

If issues arise:

1. Remove `vite-react-ssg` plugin from `vite.config.ts`
2. Delete `src/main-ssg.tsx` if created
3. Revert to pure CSR
4. Keep SEO metadata (still works with CSR)
5. No data loss (all content is in code)

**Rollback Time:** < 5 minutes

---

## Success Metrics

After implementation, you should see:

- ✅ `/terms` loads in < 0.5s (vs 2-3s before)
- ✅ `/privacy-policy` loads in < 0.5s
- ✅ `/` loads in < 1s (vs 2-3s before)
- ✅ Lighthouse SEO score: 95+ (vs 80-90 before)
- ✅ HTML source shows content (not empty div)
- ✅ All functionality still works

---

## Quick Start Commands

```bash
# 1. Install package
npm install -D vite-react-ssg

# 2. Update vite.config.ts (see Step 2 above)

# 3. Create main-ssg.tsx (see Step 3 above)

# 4. Build and test
npm run build

# 5. Preview build
npm run preview

# 6. Check dist/ folder for pre-rendered HTML
ls -la dist/
ls -la dist/terms/
ls -la dist/privacy-policy/
```

---

## Documentation References

- **vite-react-ssg:** https://github.com/antfu/vite-react-ssg
- **Vite SSG Guide:** https://vitejs.dev/guide/ssr.html
- **React Hydration:** https://react.dev/reference/react-dom/client/hydrateRoot

---

## Notes

- This is a **hybrid approach** - SSG for static pages, CSR for dynamic pages
- **No breaking changes** - existing functionality remains the same
- **Low risk** - easy to rollback if needed
- **High ROI** - significant performance improvement for minimal effort

---

## Current State (Before SSG)

- ✅ CSR with enhanced metadata
- ✅ Dynamic metadata via `react-helmet-async`
- ✅ JSON-LD schema markup
- ✅ Sitemap generation
- ✅ Works well for current use case
- ✅ Google can index SPAs
- ✅ Social sharing works with dynamic metadata

---

**Ready to implement when needed!** 🚀

```



---

## shareable links

context paragraph 


The app supports shareable links for game results and game modes. Result links use the format /home/:gameMode/result/:betId (e.g., /home/coinflip/result/abc123) and are generated after each game. The result page (ResultPage.tsx) includes share buttons for copy link, native share (mobile), Twitter, and Facebook, with dynamic share text that highlights wins (e.g., "Won $50.00 playing Coin Flip! 🎉"). Game mode links use /home/:gameMode (e.g., /home/coinflip) to share direct access to specific game previews. Short URLs are supported via /r/:shortId, created through a Supabase Edge Function and stored in the short_urls table with click tracking. All shares are tracked via analytics (trackShare()), and each result page includes SEO metadata (Open Graph tags, Twitter Cards, JSON-LD schema) for rich social previews. This enables viral sharing of wins, direct links to specific games, improved SEO through unique URLs, and analytics on share performance. The feature is implemented across ResultPage.tsx, shortUrlService.ts, ShortUrlRedirect.tsx, and integrated with the URL routing system (useGameRoute hook) for seamless navigation and state management.

---

an item table in supabase that record every price of an item that is reference on every future scan 


---

great, le

---

subscription based tokens

A user receives a material gain, then gets “free” tokens 

These tokens can be used to “enter” into the chance of winning an entry into winning an item on Disco. 

How do we incorporate the marketplace into this?

Can any game be used to enter into an item?

What are the unit economics of this? 
A user needs to have the option to buy more tokens some how. 

---

Transition to LMCT+ model


28. Branding: Disco - Rewards and Giveaways
29. Token implementation 
30. Subscription model (hype brand partnerships)
31. access to rewards to the homepage 
32. 


tokens are recieved from a subscription 

tokens are received for free when you go onto Disco 

tokens can be exchanged for entries. 

tokens are worth $0 

User can play games to stake their tokens on Disco games for a chance to receive more token 


Disco Tetris 

Disco Poker 

Disco Coinflip 
Disco Slots 

Disco Blackjack 

Disco 

![[Screenshot_2026-03-22_at_11.42.58_pm.png]]


Tokenomics:

The economics of the Disco Marketplace rely on a **Managed Token Economy** where Disco acts as a central bank, issuing "Loyalty Tokens" via $20 subscriptions that are then "spent" on variable-ratio entries. By decoupling the subscription value from the prize cost, Disco ensures profitability through a **Fixed Spread**: for a **$500 pair of sneakers**, Disco might require a **3,000-token reserve** (worth $600 in subscription revenue), instantly locking in a 20% margin. This scales to higher-value items by adjusting the "Token-to-Entry" ratio: **$15,000 in groceries** might cost **100 tokens per entry**, while a **$2M Sydney house** costs **1,000 tokens per entry**, forcing users to either save for months (retention) or use the **"Token Burn" (Mines/Blackjack)** to multiply their holdings. Because the house edge in these games "extinguishes" token liabilities before they ever reach the marketplace, Disco’s net profit increases every time a user loses a game, effectively subsidizing the winners with the lost tokens of the "non-winners" and the "gamblers."





---


[RaffleTix | Raffle fundraising made easy](https://www.raffletix.com.au/)

[Nihil Zero Giveaway!!! #1](https://www.dripshop.live/products/nihil-zero-g-8wmbXO)

[raffall.com](https://raffall.com/406639/enter-raffle-to-win-350k-beach-house-westward-ho-uk-or-250k-cash-hosted-by-joe-blogs)

examples of P2P lottery.raffles. 


---

steps:

33. change sweeps coins from coins to tokens 
34. work out economics of tokens to entries ratio

---


Users may have to play only games where they can play against each other, so there is a fixed number of tokens in circulation. 


---

Variable ticket price based on demand is an option (remember Aus Open tickets)

---














