---

---

## **Must Have (MVP-critical)**

| Feature | Description |
| --- | --- |
| **Cart Total & Item Display** | UI shows cart total + basic item info (name + price) scraped from eCommerce site |
| **Crypto Wallet Connection** | UI to connect wallet (MetaMask / WalletConnect) and show balance |
| **Flip Game Interface** | Coin selector (heads/tails), flip trigger button, and result screen (win/loss) |
| **Win/Loss Feedback Screens** | Clear display of outcome + next steps (e.g., “proceed to checkout” or “you lost”) |
| **Crypto Purchase Prompt** | UI to direct user to buy crypto if balance is insufficient (e.g., link to Transak or Ramp) |
| **Core Disclaimer Display** | Legal disclaimer below flip trigger (e.g., “Crypto is at risk. Entertainment use only.”) |
| **Basic Error Handling** | Fallback UI for unsupported sites or cart detection failure |
| **Responsive Popup Layout** | UI fits within 400x600px extension popup and adapts to different screen sizes |

---

## 🔄 **Should Have (Important for usability, not MVP-blocking)**

| Feature | Description |
| --- | --- |
| **Flip Animation (Lottie or Framer Motion)** | Visual coin flip animation with suspense timing |
| **Cart Item Breakdown Expand/Collapse** | Toggleable list to show/hide full item details |
| **Wallet Balance Indicator** | UI badge showing user’s connected wallet balance (ETH/USDC/etc.) |
| **Cooldown UI State** | If implementing cooldown logic per user/session, show a timer or locked message |
| **Transaction Summary Screen** | Mini summary screen after outcome: cart total, flip result, what to do next |
| **Terms of Use Modal** | First-time user confirmation screen with full terms & disclaimers |
| **Connection Status Feedback** | UI elements to show loading states, failed connection, etc. during wallet link or API calls |

---

## 💡 **Could Have (Nice-to-have, add after stable MVP)**

| Feature | Description |
| --- | --- |
| **Audio Feedback** | Win/loss sounds or flip sound effects for engagement |
| **Theme Toggle (Light/Dark)** | Optional UI switcher for light vs dark mode |
| **Leaderboard or Global Stats Teaser** | "X users have won their carts this week" for FOMO |
| **Flip Outcome History** | Local history showing last 3–5 flip results for that wallet/session |
| **Custom Odds Variant Selector** | UI to let user choose higher risk (e.g. 33% to 3x) or lower risk (e.g. 66% to 1.5x) |
| **Saved Carts Preview** | Persist previously detected cart for replay even after tab closes |
| **In-Popup Crypto Buy Widget** | Embedded Transak/Ramp iframe instead of redirecting to external site |

---

## ❌ **Won’t Have (Excluded for now)**

| Feature | Reason |
| --- | --- |
| **Full Web Dashboard** | The experience is extension-first; no need for a standalone site yet |
| **Merchant Integration UI** | Model is explicitly merchant-agnostic; no in-store discount logic |
| **Fiat Payment Handling** | Discopay doesn't touch fiat or facilitate checkout directly |
| **Token/Reward System** | No proprietary token system is planned — only trusted crypto (ETH, USDC) is used |
| **Withdrawal Flows** | No cashout features — crypto stays in user’s wallet or Discopay handles wins instantly |