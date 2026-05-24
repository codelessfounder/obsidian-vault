---

---

```javascript
/**
 * Discopay Transaction Simulation – 100 Transactions (Adjusted for More Customer Wins)
 * 
 * This simulation tests the business viability of Discopay by modeling
 * different transaction outcomes and calculating expected profit.
 */

const transactions = 100;
const basketValue = 100;
const feeRate = 0.05; // Updated fee rate
const fixedFee = 0.30; // Added fixed fee of $0.30 per transaction

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

function getRandomOutcome() {
  const rand = Math.random();
  let cumulative = 0;
  for (const outcome of outcomes) {
    cumulative += outcome.chance;
    if (rand < cumulative) return outcome;
  }
  return outcomes[outcomes.length - 1];
}

let totalProfit = 0;
let totalStoreCredit = 0;
let discountCount = 0;
let creditCount = 0;
let fullPriceCount = 0;

console.log("Transaction | Outcome               | Customer Pays | DiscoPay Covers | Store Credit | DiscoPay Fee | DiscoPay Net");

for (let i = 1; i <= transactions; i++) {
  const outcome = getRandomOutcome();
  const fee = outcome.customerPays * feeRate + fixedFee;
  const net = fee - outcome.discopayCovers;

  totalProfit += net;
  totalStoreCredit += outcome.storeCredit;

  if (outcome.name.includes("Discount")) discountCount++;
  if (outcome.name.includes("Extra")) creditCount++;
  if (outcome.name.includes("Full")) fullPriceCount++;

  console.log(
    `${i.toString().padStart(11)} | ${outcome.name.padEnd(21)} | $${outcome.customerPays.toFixed(2).padStart(13)} | $${outcome.discopayCovers.toFixed(2).padStart(15)} | $${outcome.storeCredit.toFixed(2).padStart(12)} | $${fee.toFixed(2).padStart(12)} | $${net.toFixed(2).padStart(11)}`
  );
}

console.log("\nSummary Results");
console.log("==============");
console.log("Total Profit:", `$${totalProfit.toFixed(2)}`);
console.log("Profit per Transaction:", `$${(totalProfit / transactions).toFixed(2)}`);
console.log("Total Store Credit Generated:", `$${totalStoreCredit.toFixed(2)}`);
console.log(`Transactions with Discounts: ${discountCount} (${((discountCount/transactions)*100).toFixed(1)}%)`);
console.log(`Transactions with Store Credit: ${creditCount} (${((creditCount/transactions)*100).toFixed(1)}%)`);
console.log(`Transactions at Full Price: ${fullPriceCount} (${((fullPriceCount/transactions)*100).toFixed(1)}%)`);

/**
 * To run this simulation:
 * 1. In Node.js: node app/utils/discopay-simulation.js
 * 2. In browser console: copy and paste this code
 */ 
```

