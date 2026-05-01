---

---

[[Business/Customer discovery/Business model simulations/Test 1 Control/simulation code]]


Pricing probabiilities

```javascript
const outcomes = [
  {
    name: "20% Discount",
    chance: 0.10, // Increased from 5% to 10%
    customerPays: 80,
    merchantGets: 100,
    discopayCovers: 20,
    storeCredit: 0,
  },
  {
    name: "10% Discount",
    chance: 0.15, // Increased from 10% to 15%
    customerPays: 90,
    merchantGets: 100,
    discopayCovers: 10,
    storeCredit: 0,
  },
  {
    name: "Full Price",
    chance: 0.45, // Reduced from 55% to 45%
    customerPays: 100,
    merchantGets: 100,
    discopayCovers: 0,
    storeCredit: 0,
  },
  {
    name: "10% Extra (credit)",
    chance: 0.20,
    customerPays: 110,
    merchantGets: 100,
    discopayCovers: 0,
    storeCredit: 10,
  },
  {
    name: "20% Extra (credit)",
    chance: 0.10,
    customerPays: 120,
    merchantGets: 100,
    discopayCovers: 0,
    storeCredit: 20,
  },
];
```

---

### Simulation summary (3 runs)

- Run 1: Total profit **-$140.90**, profit/transaction **-$1.41**, store credit **$410**.
- Run 2: Total profit **$23.60**, profit/transaction **$0.24**, store credit **$400**.
- Run 3: Total profit **$-299.40** across 300 transactions, average profit/transaction **-$1.00**.

Outcome mix (control baseline) is consistently around:

- Discounts: ~27%
- Store credit: ~29-31%
- Full price: ~44-49%

Qualitative interpretation:

- Control pricing creates a fun outcome mix but trends toward weak or negative profitability.
- Discount burden remains heavy relative to fee capture.
- Store credit helps engagement but does not offset losses in this baseline structure.

Quantitative snapshot:

- Total profit: **-$299.40** across 300 transactions
- Profit per transaction: **-$1.00**
- Outcome mix: 27.0% discounts, 29.3% store credit, 43.7% full price