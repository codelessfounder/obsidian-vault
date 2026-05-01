---

---

Payout logic:



| Safe tiles (k) | “Stake/Fair” % (and $) | **Tuned** % (and $) | Diff (Tuned − Fair) |
| --- | --- | --- | --- |
| 1 | **12.50%** ($12.50) | **10.00%** ($10.00) | −2.50 pts |
| 2 | **14.29%** ($14.29) | **11.43%** ($11.43) | −2.86 pts |
| 3 | **16.67%** ($16.67) | **13.33%** ($13.33) | −3.34 pts |
| 4 | **20.00%** ($20.00) | **18.00%** ($18.00) | −2.00 pts |
| 5 | **25.00%** ($25.00) | **22.50%** ($22.50) | −2.50 pts |
| 6 | **33.33%** ($33.33) | **31.67%** ($31.67) | −1.66 pts |
| 7 | **50.00%** ($50.00) | **49.00%** ($49.00) | −1.00 pt |
| 8 | **100.00%** ($100.00) | **100.00%** ($100.00) | 0 |

### Which I recommend (and why)

**Go with the Tuned schedule.**

- **Matches your premise:** Still pays **100% at 8**.
- **Less “free” early feel:** First pick at **10%** (vs the “fair” 12.5% and far from your old 30%) reduces the sense that one safe tile is an easy profit, which it is given 8/9 survival.
- **Better behavioral curve:** Rewards are more **back‑loaded**, nudging deeper play where tension—and perceived value—rise.
- **Operationally nicer:** The small early haircut yields a **higher realised hold** from early cash‑outs and inevitable bombs, without touching the end state.

If you want to nudge engagement a tad, you can set a **first‑pick floor** at 10–12% (display) while keeping the ledger math on the tuned curve.



Mathematical rationale:

Absolutely—here’s the math behind both schedules, in plain English with the key equations.

# 1) “Stake/Fair” schedule (guarantees 100% at 8 and is EV‑neutral at every step)

**Setup:** 9 tiles total; 8 safe, 1 bomb. If the player reaches **8 safe tiles**, they get **100% of stake** back.

At the moment the player has revealed **k** safe tiles (so there are 9−k9-k9−k tiles left, of which 8−k8-k8−k are safe):

- The probability of finishing the board **from here** (i.e., hitting all remaining 8−k8-k8−k safe tiles without the bomb) is a telescoping product:

P(finish∣k)=∏i=08−k−18−k−i9−k−i=∏m=18−kmm+1=19−k.P(\text{finish}\mid k)
= \prod_{i=0}^{8-k-1}\frac{8-k-i}{9-k-i}
= \prod_{m=1}^{8-k}\frac{m}{m+1}
= \frac{1}{9-k}.

P(finish∣k)=i=0∏8−k−19−k−i8−k−i=m=1∏8−km+1m=9−k1.

- If finishing pays **1.00× stake**, then the **EV of continuing to the end** (from k safe) is:

EVcontinue(k)=19−k×1.00 (stake).\text{EV}_{\text{continue}}(k)=\frac{1}{9-k}\times 1.00\ (\text{stake}).

EVcontinue(k)=9−k1×1.00 (stake).

To make the player **indifferent** (fair/EV‑neutral), set the **cash‑out now** equal to that EV:

CashoutFractionfair(k)=19−k\boxed{\text{CashoutFraction}_{\text{fair}}(k)=\frac{1}{9-k}}

CashoutFractionfair(k)=9−k1

This gives the table:

k=1→12.5%, 2→14.29%, 3→16.67%, 4→20%, 5→25%, 6→33.33%, 7→50%, **8→100%**.

**Interpretation:** Early steps pay little because the chance of eventually finishing is relatively high. Rewards are **back‑loaded** and the schedule is mathematically transparent and auditable.

---

# 2) “Tuned” schedule (back‑loads more, raises realised hold, still 100% at 8)

You wanted the first safe reveal to **not** feel like an easy win (e.g., your old 30% felt too generous given 8/9 survival). We therefore **haircut** the fair fractions early while keeping the endpoint fixed at 100%:

CashoutFractiontuned(k)=CashoutFractionfair(k)×(1−αk)\boxed{\text{CashoutFraction}_{\text{tuned}}(k)=\text{CashoutFraction}_{\text{fair}}(k)\times\bigl(1-\alpha_k\bigr)}

CashoutFractiontuned(k)=CashoutFractionfair(k)×(1−αk)

- αk\alpha_kαk is a **taper**: larger for small k (e.g., 20% haircut), shrinking toward **0 by k=8**.
- Example taper: α={0.20,0.20,0.20,0.10,0.10,0.05,0.02,0}\alpha=\{0.20,0.20,0.20,0.10,0.10,0.05,0.02,0\}α={0.20,0.20,0.20,0.10,0.10,0.05,0.02,0} for k=1…8.

This yields the table you liked:

k=1→10%, 2→11.43%, 3→13.33%, 4→18%, 5→22.5%, 6→31.67%, 7→49%, **8→100%**.

**What the taper does mathematically:**

- Since CashoutFractiontuned(k)<EVcontinue(k)\text{CashoutFraction}_{\text{tuned}}(k) < \text{EV}_{\text{continue}}(k)CashoutFractiontuned(k)<EVcontinue(k) for early k, the player is (slightly) **disincentivised to cash early**, which **increases depth** and **house hold**—while still preserving the promise of **100% at 8**.
- The curve remains **monotone increasing** and **bounded by 100%**, so it’s easy to reason about and safe to implement.

---

## Quick sanity checks

- **Fair at k=7:** 1/(9−7)=1/2=50%1/(9-7)=1/2=50\%1/(9−7)=1/2=50%. Tuned makes it ~49%—a modest haircut that preserves the late‑game excitement.
- **Cap at k=8:** Both schedules force 100% by construction.

---

## When to use which

- Use **Stake/Fair** if you want a **purely EV‑neutral** experience that’s maximally transparent and simple to defend.
- Use **Tuned** if you want the same end promise (**100% at 8**) but **less “free” feeling early game** and a **higher realised hold**—achieved by a small, explicit haircut that fades to zero by the end.