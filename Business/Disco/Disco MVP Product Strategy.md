---

---
27 December 2025

---

This document outlines Disco’s MVP product strategy - it defines feature builds, testable hypotheses and measurable outcomes. 

---

## Core MVP Hypotheses

- *People are willing to pay more to influence a game outcome in their favour*
- *People are willing to bet on purchases they’re making or things they own *
- *Cards increase people’s game satisfaction and perceived RTP value *

---

## OKRs

**a. Game loop**

objective: deliver an casino that delivers a fast, stable and trustworthy experience.

key results:

- game start latency < 300ms (bet → animation start)
- < 1% game error rate across all sessions
- 99.5% session completion rate once a game starts

**b. Betting on purchases **

objective: validate that users will wager real money when anchored to items they have uploaded.

key results:

- ≥ 35% of users who upload an image proceed to click “play”
- ≥ 25% of users who see a detected item value place a wager equal to or greater than that value
- ≥ 15% of image-initiated sessions complete at least one gameplay loop

**c. Cards during gameplay**

objective: validate that cards meaningfully change player behaviour and perceived control over gameplay outcomes.

key results:

- ≥ 40% of active players use at least one card per session
- ≥ 25% of games have a card applied
- ≥ 15% increase in session length for card users vs non-card users

**d. Unit economics**

objective: ensure disco remains profitable even with >100% rtp gameplay modifiers.

key results:

- net platform rtp within target band (94–97% including cards)
- ≥ 30% of paying users purchase cards
- positive gross margin per active user by day 30

---

## Core MVP Loop

1. User enters Disco
2. Selects a game
3. Selects GC or SC
4. Commits wager
5. Chooses whether to use a card (time-limited)
6. Game resolves
7. Outcome + balance update shown immediately

---

## Feature Scope (What will be built)

### i. Games 

**Included**

- Coinflip 
- Mines 
- Blackjack 
- Slots (native)
- Wheel

**Details**

- Games support GC and SC
- Games integrate with card effects
- Games resolve deterministically server-side
- Animations are clean and fast

### ii. Game Modes

- Heads up (regular gameplay)
- Chance (Sliding chance bar)
- Battles vs Bot (Different gameplay for each gameplay)

**Excluded**

- Live PvP matchmaking
- Multi-table sessions
- Parlays

### iii. Cards System 

- Card inventory per user
- Cards usable once per action
- Time-limited decision window (approx 5 seconds)
- Cards modify:
    - Probabilities (e.g. +5% win chance)
- Clear UI feedback showing card impact
- Cards are used once per play

**Tiering**

- Card & Item tiers (Common → Rare → Epic → Legendary)
- Cards only usable on matching tier items

**Excluded**

- Card fragments
- Card combinations
- Cross-tier usage
- Dozens of card variants

### iv. Shop

**Features:**

- Buy GC
- Buy SC
- Buy cards directly (all tiers)

**Excluded**

- Bundles
- Discounts
- Dynamic pricing
- Promotions
- Gifting

### v. Item System

**Included**

- Curated set of items per tier (item niche TBA)
- Fixed, known item pools
- Item inventory (redeem item for SC)
- AI item search 
- User uploaded items

### vi. Balances & Payments

**Included**

- GC balance
- SC balance
- Minimum withdrawal logic (e.g. 100 SC, played only)
- Basic withdrawal request flow

**Excluded**

- Instant withdrawals
- Advanced fraud detection
- Multiple payout methods

### vii. Authentication & Compliance

**Included**

- User accounts
- Email/password or wallet auth
- KYC auth

### viii. Admin Dashboard (Internal)

- Enable/disable games
- Enable/disable cards
- Adjust card odds
- Monitor RTP
- View user sessions

### ix. Technical & UX Constraints

- Minimal perceived lag
- Provably fair logic (internal)
- Deterministic outcomes
- Mobile-first UI
- PWA-compatible architecture
- Clean URL-based navigation

### x. Retention Mechanics 

- Signup SC bonus
- Daily free SC
- Happy Hour SC

**Excluded**

- Loyalty tiers
- XP / levels

### xi. Affiliate System

- Invite-only affiliates (manual approval, prevents abuse early on)
- Unique referral link per affiliate
- Cookie-based attribution (e.g. 30 days),  locked on first deposit
- Affiliates may offer free SC or “starter cards” to their followers
    - *“Sign up via my link and choose your first card free”*

**Commission Structure **

- Affiliate earns X% of net platform revenue (Excludes bonuses and free SC)
- Paid only on real-money activity

**Payout Rules**

- $100 Minimum payout threshold 
- Bi-weekly payouts
- Supported payout methods:
    - Crypto (USDC/ETH)
    - PayPal / Bank (optional)

**Dashboard **

- Total referred users
- Total deposits from referrals
- Net revenue generated
- Commission earned
- Payout status (pending / paid)

**Risk Controls**

- KYC required before first affiliate payout
- Self-referrals blocked
- Duplicate IP/device checks
- Manual payout approval in V1

---

## Future products

- Lottery
- Native crypto token
- Player levels
- Card fragments
- Live PvP

---

## [project.md](http://project.md/) file:

```markdown
Purpose
Disco is a Progressive Web Application (PWA) that provides a gaming experience where users play casino-style games (coin flip, blackjack, mines) to win items they want. Users can either scan items they have (using photos) or play for items listed on Disco. Users wager sweepstakes coins (Gold Coins or Sweeps Coins) on games, and if they win, they receive the item; if they lose, the sweepstakes coins are retained by Disco.

Users can upload images of items they want (photos of products, receipts, or items) which are analyzed using AI (OpenAI Vision API) to automatically extract product information and prices. Users can also select from items listed on Disco or previously analyzed items stored in their session history. The PWA features sweepstakes coin wagering, multiple game interfaces (coin flip, blackjack, mines), and a seamless, accessible UI matching the Disco brand design language.

## Tech Stack

### Core Framework
- **Vite** - Build tool and dev server
- **TypeScript** - Type-safe JavaScript
- **React 18** - UI framework
- **React Router DOM** - Client-side routing

### UI & Styling
- **Tailwind CSS** - Utility-first CSS framework
- **shadcn/ui** - Component library built on Radix UI primitives
- **Framer Motion** - Animation library
- **Lucide React** - Icon library
- **SpotifyMix** - Custom brand font family

### State Management & Data
- **TanStack React Query** - Server state management and data fetching
- **React Hook Form** - Form state management
- **Zod** - Schema validation

### Blockchain & Wallets
- **Ethers.js** - Ethereum/EVM integration (for payment methods, not wagering)
- **Solana Web3.js** - Solana integration (for payment methods, not wagering)
- **@metamask/detect-provider** - MetaMask detection (for payment methods, not wagering)
- **@solana/wallet-adapter-phantom** - Phantom wallet adapter (for payment methods, not wagering)

### Backend & Database
- **Supabase** - Backend-as-a-Service (database, auth, storage)

### Media & Effects
- **Howler.js** - Audio management
- **Lottie** - Animation playback
- **Canvas Confetti** - Celebration effects
- **Spline** - 3D graphics

### Development Tools
- **ESLint** - Code linting (TypeScript ESLint, React hooks)
- **PostCSS** - CSS processing
- **Autoprefixer** - CSS vendor prefixing

## Project Conventions

### Code Style

#### Naming Conventions
- **Components**: PascalCase (e.g., `DiscoSidebar.tsx`, `HomePage.tsx`)
- **Hooks**: camelCase with `use-` prefix (e.g., `useSound.ts`, `useCoinFlipGame.ts`)
- **Utilities**: camelCase (e.g., `utils.ts`, `soundManager.ts`)
- **Types/Interfaces**: PascalCase (e.g., `SoundName`, `ButtonProps`)
- **Files**: kebab-case for utilities, PascalCase for components

#### Path Aliases
- `@/` maps to `src/` directory
- Use `@/components`, `@/hooks`, `@/lib`, `@/pages` for imports

#### TypeScript Configuration
- Relaxed strictness: `noImplicitAny: false`, `strictNullChecks: false`
- `skipLibCheck: true` for faster compilation
- Unused variables/parameters warnings disabled

#### Formatting
- ESLint with React hooks rules enforced
- React Refresh plugin for HMR
- TypeScript ESLint recommended config

### Architecture Patterns

#### Directory Structure
```
src/
├── components/ui/     # shadcn/ui components and custom UI components
├── hooks/             # Custom React hooks
├── lib/               # Utility functions and services
├── pages/             # Route components
├── services/          # Business logic services (database, game)
├── types/             # TypeScript type definitions
└── game/              # Game-specific logic (blackjack, etc.)
```

#### Component Architecture
- **UI Components**: Located in `src/components/ui/`, following shadcn/ui patterns
- **Page Components**: Route-level components in `src/pages/`
- **Custom Hooks**: Encapsulate reusable logic (e.g., `useCoinFlipGame`, `useSound`)
- **Service Layer**: Business logic separated into services (`databaseService.ts`, `gameService.ts`)

#### State Management
- **React Query**: Server state, caching, and data synchronization
- **React Hook Form**: Form state and validation
- **Local State**: React `useState` for component-specific state
- **Custom Hooks**: Encapsulate complex stateful logic

#### Design System
- **Design Tokens**: Royal Imperial Palette - flat color system defined in `tailwind.config.ts` and `src/index.css`
  - **Royal Imperial Palette** (current, preferred):
    - `royal-primary`: `#3b0764` - Elevated cards, main content areas
    - `royal-primary-dark`: `#280542` - Navigation, sidebars, headers (for depth)
    - `royal-background`: `#1A032D` - Main background (deepest layer)
    - `royal-action`: `#FBBF24` - CTAs, bet buttons, deposit, sign up (amber gold)
    - `royal-action-hover`: `#EAB308` - Darker gold for hover states
    - `royal-secondary`: `#8B5CF6` - Active highlights, secondary buttons (violet)
    - `royal-secondary-hover`: `#7C3AED` - Darker violet for hover states
    - `royal-text`: `#FFFFFF` - Primary text color
    - `royal-muted`: `#C4B5FD` - Less important text (terms, footers)
  - **Design Philosophy**: Flat colors, no borders, depth created through color contrast
  - **Utility Classes**: Available in `src/index.css`:
    - Backgrounds: `bg-royal-primary`, `bg-royal-primary-dark`, `bg-royal-background`, `bg-royal-action`, `bg-royal-secondary`
    - Text: `text-royal-text`, `text-royal-muted`
    - Cards: `card-royal-elevated`, `card-royal-flat`
    - Buttons: `btn-royal-action`, `btn-royal-secondary` (also available as shadcn/ui button variants: `variant="royal-action"`, `variant="royal-secondary"`)
  - **Legacy Brand Colors** (kept for backward compatibility during migration):
    - Primary: `#9A81DF` (purple)
    - Secondary: Purple, Pink, Orange variants
    - Card background: `#0C0524`
- **Typography**: SpotifyMix font family with responsive clamp sizing
- **Dark Mode**: Class-based dark mode support
- **Responsive**: Mobile-first approach with Tailwind breakpoints

### Testing Strategy
- Test files located in `__tests__/` directories (e.g., `src/pages/__tests__/`)
- Jest/React Testing Library setup (based on existing test file)
- Focus on component and integration testing

### Git Workflow
[To be determined by team - no specific conventions documented]

## Domain Context

### Game Mechanics
- **Coin Flip**: Double-or-nothing wagering on item value
- **Blackjack**: Card game with dealer logic
- **Mines**: Grid-based game with safe/bomb reveals
- Games use sweepstakes coin wagering (Gold Coins and Sweeps Coins)

### User Flow
1. **Landing**: User visits landing page and can sign up for waiting list
2. **Home**: User navigates to home page (authenticated or demo mode)
3. **Item Selection**: User either:
   - Scans an item they have by uploading an image (photo of product, receipt, or item), OR
   - Selects an item from items listed on Disco, OR
   - Selects from previously analyzed items (saved from previous uploads)
4. **AI Analysis**: If image uploaded:
   - Image is sent to OpenAI Vision API for analysis
   - AI identifies products, detects visible prices, and determines if web search is needed
   - For branded products without visible prices, web search is performed to find current retail prices
   - Item data is extracted: product name, price, and value
   - Item record is saved to Supabase database
   - Image is uploaded to Supabase storage
5. **Currency Selection**: User selects between Gold Coins (GC) and Sweeps Coins (SC) for wagering
6. **Game Selection**: User selects a game mode (coin flip, blackjack, or mines)
7. **Wager Placement**: User places wager amount (typically equal to item value, adjustable via slider). User can toggle between GC and SC for wagering
8. **Game Execution**: Game runs with win/loss outcome determined by game logic
9. **Result**: User sees win/loss result. If they win, they receive the item; if they lose, the sweepstakes coins are retained

### Sweepstakes Mode
Sweepstakes mode is the primary wagering system using virtual coins (Gold Coins and Sweeps Coins). This mode is controlled by a feature flag and can be toggled in the application.

#### Dual Currency System
- **Gold Coins (GC)**: 
  - Integer-based currency (e.g., 70,000,000 GC initial balance)
  - For entertainment purposes only
  - Cannot be redeemed for cash or discounts
  - Used for wagering in games
- **Sweeps Coins (SC)**:
  - Decimal-based currency (e.g., 2,000.00 SC initial balance)
  - Can be redeemed for cash or discount codes
  - Used for wagering in games
  - Subject to redemption minimums and processing times

#### Features
- **Coin Toggle**: Users can switch between GC and SC when placing bets (disabled during active gameplay)
- **Balance Display**: Real-time balance display with animations for balance changes
- **Balance Management**: 
  - Balances reset to initial values on page refresh
  - Balance updates exposed via global window functions for game integration
  - Balance validation before placing bets
- **Sweepstakes Modal**: Provides access to:
  - **Buy Coins**: Purchase packages of GC with bonus SC (supports card, PayPal, crypto payment methods)
  - **Redeem**: Convert SC to cash (bank account/PayPal) or discount codes (minimum 100 SC)
  - **History**: View transaction history
  - **Bonuses**: Sign-up bonus (100 SC) and daily bonus (10 SC)
  - **Mail-In Request**: Request free SC via mail (no purchase necessary)

#### Game Integration
- All games (coin flip, blackjack, mines) support both GC and SC wagering
- Bet placement decreases balance immediately
- Wins add winnings to balance (original bet + multiplier)
- Losses retain the wagered amount (already deducted)
- Mines game uses percentage-based winnings calculation

#### Implementation Details
- **Component**: `SweepstakesBalanceDisplay.tsx` - Main balance display and coin toggle UI
- **Modal**: `SweepstakesModal.tsx` - Coin purchase, redemption, and history interface
- **Utilities**: `sweepstakesBalanceUtils.ts` - Balance validation, bet placement, and result processing functions
- **Global State**: Balance and coin selection exposed via `window` object for cross-component communication
- **Feature Flag**: Controlled in `Header.tsx` via `sweepstakesMode` state (defaults to `true`)

### Session Management
- Item sessions tracked and stored
- Session history and analytics
- Recent items and game tracking

### Sound System
- Centralized sound management via `soundManager.ts`
- Game-specific sounds (coinflip, blackjack, mines, item)
- Mute/unmute functionality
- Sound preloading for performance

## Important Constraints

### Technical Constraints
- **PWA Requirements**: Must work as a Progressive Web App (offline capability, installable)
- **Browser Compatibility**: Must support modern browsers
- **Performance**: Optimized for fast load times and smooth animations
- **Accessibility**: Must maintain consistent, accessible UI/UX standards

### Business Constraints
- **Item-Based Gaming**: Users play games to win items they want (scanned items or items listed on Disco)
- **Wagering System**: Uses sweepstakes coin wagering (Gold Coins and Sweeps Coins)
- **Design Consistency**: All UI must align with Disco brand design language

### Regulatory Constraints
- **Gambling Regulations**: May be subject to regional gambling laws
- **Sweepstakes Regulations**: Must comply with sweepstakes and gaming regulations
- **Privacy**: Privacy policy page required (`/privacy-policy`)

## External Dependencies

### Supabase
- **Purpose**: Backend database, authentication, and storage
- **Configuration**: Environment variables `VITE_SUPABASE_URL` and `VITE_SUPABASE_ANON_KEY`
- **Usage**: User sessions, game history, analytics, item data storage

### APIs & Services
- **OpenAI API**: 
  - **Vision API (GPT-4o)**: Analyzes uploaded item images to identify products, detect visible prices, and determine pricing strategy
  - **Web Search (Responses API)**: Performs web searches for branded products without visible prices to find current retail pricing
  - **Fallback Pricing**: Uses model knowledge to estimate prices for generic items when no visible price or web search results are available
  - Implementation: `api/analyse-image.ts` endpoint handles the complete analysis pipeline

### Deployment
- **Vercel**: Hosting platform (based on `vercel.json` presence)

```



---

## Build checklist

## P0 — Core MVP (Non-negotiable to Launch)

### 1. Foundations & Architecture

- [x] Deterministic, server-side game resolution engine
- [x] Internal provably-fair logic (seeded, auditable)
- [x] GC / SC balance ledger (atomic updates)
- [x] PWA-ready app shell (mobile-first)
- [x] Clean URL-based routing/ 
- [ ] SEO/ CSR to SSG
- [x] Low-latency client ↔ server round-trip (<300ms perceived)

---

### 2. Authentication & Compliance

- [x] User accounts
- [x] Email/password auth **or** wallet auth
- [ ] KYC flow (blocking withdrawals + affiliate payouts)
- [ ] Basic session management
- [ ] Account state flags (verified / restricted / banned)
- [ ] Security test (playwright)
- [ ] CAPTCHA

---

### 3. Games (Minimum Viable Set)

- [x] Coinflip (GC + SC)
- [x] Mines (GC + SC)
- [x] Blackjack (GC + SC)
- [ ] Wheel (GC + SC)
- [ ] Slots (Hypedrop style)
- [x] Deterministic outcome calculation
- [x] Fast, clean animations (no blocking delays)
- [ ] Shared game interface for card effects
- [ ] persistent session if a user leaves the page mid game
- [ ] Balance display (heads up, chance)

---

### 4. Core Game Modes

- [x] Heads-up (default gameplay)
- [x] Chance mode (sliding probability bar)
- [ ] Bot battles (distinct logic per game)

---

### 5. Card System (Slim V1)

- [ ] User card inventory
- [ ] One-card-per-action enforcement
- [ ] 5-second decision window
- [ ] Card effect engine (probability modifiers only)
- [ ] Clear UI showing *before vs after* odds
- [ ] Card consumption on use
- [ ] Tier enforcement (card ↔ item tier match)

---

### 6. Item System (Minimal Viable)

- [x] Fixed item pools per tier
- [x] Known item odds per tier
- [x] Item inventory
- [ ] Redeem item → SC
- [x] User-uploaded items (basic validation only)
- [x] AI item search (text or image, not both initially)
- [ ] Item-scan tier determine 
- [ ] 

---

### 7. Payments & Balances

- [ ] Buy GC
- [ ] Buy SC
- [ ] Withdrawal request flow
- [ ] Minimum withdrawal enforcement
- [ ] “Played-only” SC logic
- [ ] Admin-reviewed withdrawals

---

## 🟧 P1 — Launch+ (Retention & Revenue Leverage)

### 8. Shop Expansion

- [ ] Buy cards directly
- [ ] Tiered card pricing
- [ ] Inventory-aware purchase limits

---

### 9. Retention Mechanics

- [ ] Signup SC bonus
- [ ] Daily free SC claim
- [ ] Abuse throttling (cooldowns, caps)

---

### 10. Affiliate System (Controlled Rollout)

- [ ] Invite-only affiliate creation
- [ ] Unique referral links
- [ ] Cookie-based attribution (30-day, first deposit lock)
- [ ] Affiliate-granted free SC
- [ ] Affiliate-granted starter card selection
- [ ] Net revenue calculation (exclude bonuses)
- [ ] Commission ledger
- [ ] Minimum payout enforcement
- [ ] Manual payout approval

---

### 11. Affiliate Dashboard

- [ ] Referred users count
- [ ] Referral deposit totals
- [ ] Net revenue generated
- [ ] Commission earned
- [ ] Payout status tracking

---

## 🟨 P2 — Operational Control & Hardening

### 12. Admin Dashboard (Internal)

- [ ] Enable/disable games
- [ ] Enable/disable cards
- [ ] Adjust card odds
- [ ] RTP monitoring (global + per game)
- [ ] User session viewer
- [ ] Manual user balance adjustments (audited)

---

### 13. Risk Controls & Integrity

- [ ] Self-referral blocking
- [ ] Duplicate IP/device detection
- [ ] Affiliate KYC enforcement
- [ ] Manual flags for suspicious accounts
- [ ] Basic anomaly alerts (RTP drift, abuse patterns)

---

### 14. UX Polish (Post-Launch)

- [ ] Odds clarity tooltips
- [ ] Card impact animations
- [ ] Loss-mitigation UX (soft language, transparency)
- [ ] Error states with recovery paths
- [ ] Mobile performance optimisation



**jfmjvwlulegvahnk**


use upbank or revolut for payments (mike)