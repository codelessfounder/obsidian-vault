---

---
Discopay is a **Firefox browser extension** that scrapes eCommerce cart totals, prompts users to risk an equal amount in crypto, and offers a double-or-nothing coin flip mechanic. The user wins crypto or loses it, then decides whether to proceed with their purchase independently.

---

## 🔄 UX Flow Summary

1. **User on Checkout Page**
2. **Extension activates → reads cart total & items**
3. **Prompt to play appears → “Try to get your cart for free”**
4. **User connects wallet or tops up crypto**
5. **User places wager → chooses heads or tails**
6. **Animated coin flip plays**
7. **Win: +100% payout → user uses crypto to pay for cart manually**
8. **Loss: -100% → user chooses whether to still buy items or not**

---

## 🧱 Development Plan by Component

### 1. **Extension Shell & Cart Detection**

- Build manifest + background worker for Firefox
- Content script to scrape cart total + item data from common platforms (Shopify, WooCommerce, etc.)
- Store scraped data in extension state

**Milestone:** Extension shows cart total in popup

---

### 2. **Popup Interface (Core UI)**

- Initial screen: “Your cart is $X. Want to play to win it for free?”
- Show scraped items + total
- CTA: "Connect Wallet" / "Buy Crypto"

**States:**

- Unconnected
- Connected but insufficient funds
- Connected and ready to play

**Milestone:** Popup fully responsive and reactive to user + wallet state

---

### 3. **Wallet Integration**

- Use **WalletConnect** or **MetaMask** (injectable or via iframe bridge)
- Show wallet address + balance in popup
- Read balance to confirm if user has enough to play

**Milestone:** Wallet connects + verifies sufficient crypto for wager

---

### 4. **Flip Game UI**

- Coin flip animation (use Lottie or Framer Motion in popup)
- Prompt to choose heads or tails
- Server call to flip endpoint (returns win/loss based on provably fair hash)

**States:**

- Flip in progress
- Win: show "You won $X"
- Loss: show "You lost $X"

**Milestone:** Full animated flip with outcome UI and state management

---

### 5. **Backend Game Logic**

- API to receive wager, return outcome (win/loss)
- Seed with provably fair hash
- Log outcomes for audit + support

**Milestone:** Secure, verifiable backend flip service live

---

### 6. **Payment Recommendation Screen**

- After outcome:
    - If win: "Congrats! You now have $X in your wallet – proceed to checkout on [site name]."
    - If loss: "You lost the wager. You can still choose to buy your items if you’d like."
- Include copy-paste summary of cart for reference

**Milestone:** Final user state flow complete, including outcome guidance

---

### 7. **Fail Safes + Edge Cases**

- No cart detected: fallback prompt or error message
- Insufficient crypto: redirect to buy page or show guidance
- Loss streaks: cool-down timer or dynamic odds placeholder (future-proofing)

**Milestone:** UX is resilient and instructive under all failure modes

---

### 8. **Legal & Disclaimer UX**

- Clear Terms of Use prompt before first flip
- “Crypto at risk. Entertainment only.” warning before playing
- Small-print disclaimer below all CTA buttons

**Milestone:** Disclaimers embedded into every relevant UX moment

---

## 🗓 Suggested Timeline (Agile 2–3 week sprint blocks)

| Sprint | Goal |
| --- | --- |
| Week 1 | Cart scraping + extension shell + popup wireframe |
| Week 2 | Wallet connection + balance logic |
| Week 3 | Flip game animation + backend flip result |
| Week 4 | Win/loss handling + final user guidance |
| Week 5 | Fail states + edge cases + polish + disclaimers |
| Week 6 | Internal testing + limited release via unlisted Mozilla add-on |

---

Would you like this turned into a task board format (e.g. for Notion, Trello, or Linear)? Or should we move on to sketching the wallet + flip logic in detail?


## X Flow with Mapped Features

---

### **1. User lands on checkout page**

- ✅ **Cart Total & Item Display** (Must)
    - Cart data is scraped via content script and displayed in the popup.
- ✅ **Basic Error Handling** (Must)
    - If unsupported or undetectable cart, show fallback UI: “We couldn’t detect your basket.”

---

### **2. User opens the Discopay extension**

- ✅ **Responsive Popup Layout** (Must)
    - Ensures UI works across screen sizes in the popup window.
- ✅ **Wallet Connection UI** (Must)
    - User is prompted to connect MetaMask/WalletConnect.

---

### **3. Cart data is displayed**

- ✅ **Cart Item Breakdown Expand/Collapse** (Should)
    - Users can optionally toggle to view individual items and prices.
- ✅ **Wallet Balance Indicator** (Should)
    - Badge shows crypto balance relevant to wager requirement.

---

### **4. User is prompted to flip for a chance to win**

- ✅ **Flip Game Interface** (Must)
    - User chooses heads/tails, places wager.
- ✅ **Core Disclaimer Display** (Must)
    - Shown beneath flip button: “Crypto is at risk. Entertainment use only.”
- ✅ **Terms of Use Modal** (Should)
    - First-time users must accept terms before being allowed to flip.
- ✅ **Crypto Purchase Prompt** (Must)
    - If balance is insufficient, user sees guidance to purchase crypto (link to Transak/Ramp).

---

### **5. User initiates flip**

- ✅ **Flip Animation** (Should)
    - Visual suspense and excitement via Lottie or Framer Motion.
- ✅ **Connection Status Feedback** (Should)
    - Loader or message while backend flip result is being determined.

---

### **6. Flip result is shown**

- ✅ **Win/Loss Feedback Screens** (Must)
    - Distinct states for win/loss, with celebratory or fallback visuals.
- ✅ **Transaction Summary Screen** (Should)
    - Shows cart total, wager amount, win/loss outcome, and suggested next step.
- ✅ **Cooldown UI State** (Should)
    - Optional: if user hits a play limit, display cooldown timer or lockout message.

---

### **7. Post-flip user guidance**

- ✅ **User Prompt to Checkout**
    - If win: “Use your crypto to pay for your items now on [site name].”
    - If loss: “You can still choose to complete your purchase.”
- ✅ **Connection Status Feedback** continues to handle error or replay attempts.

---

## 🧩 Summary of What Will Be Implemented

All features below are now part of the development scope:

| Feature Category | Features |
| --- | --- |
| Core UX | Cart detection, wallet connection, wager prompt, flip result, post-outcome guidance |
| UI Detail | Flip animation, responsive popup, balance display, toggleable item view |
| Risk Messaging | Terms modal, legal disclaimers, win/loss framing |
| Recovery UX | Cooldown logic, crypto top-up redirect, graceful failure handling |