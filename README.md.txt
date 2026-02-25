# 🐢 SlowFi Habit Tracker
### *Compound your discipline. Stack sats. Build on Bitcoin.*

> **OP_NET Vibecoding Challenge Entry** — Bitcoin Layer 1 | OP_NET Smart Contracts | No bridges. No excuses.

---

## What is SlowFi?

SlowFi is the antithesis of DeFi degen culture. No 1000x promises. No rug pulls. Just patience, discipline, and the quiet confidence of a Bitcoin maxi who has never once checked the price today.

**SlowFi Habit Tracker** turns your HODL convictions into on-chain commitments — stake BTC or $MOTO on your habits, check in daily, and earn yield for staying the course. Break your streak? The Impatience Tax hits you. The community pool thanks you.

---

## ✨ Features

| Feature | Description |
|---|---|
| 🔒 **Habit Vaults** | Commit BTC or $MOTO to a streak (7 / 30 / 100 days) |
| ✅ **Daily Check-ins** | On-chain check-in once per ~144 blocks (~1 day) |
| 💰 **Yield for Winners** | Complete streak → get stake back + community pool yield |
| ⚡ **Impatience Tax** | Break streak → 15% penalty to SlowFi community pool |
| 🏆 **Leaderboard** | Top 10 longest active streaks, fully on-chain |
| 🎖️ **Soulbound NFT Badges** | 7-day: *SlowFi Initiate* • 30-day: *SlowFi Master* • 100-day: *Bitcoin Monk* |
| 🏎️ **MotoCat Miles** | Streak days × 10 = bonus racing miles in MotoCat |
| 📊 **SlowFi Pool Stats** | Live pool balance, yield rate, total "Impatience Tax" collected |

### Habit Options
- 🟠 HODL This Week
- 🚫 No Selling BTC
- 🪙 Stake More $MOTO
- ⛓️ Engage OP_NET Daily
- 🖥️ Run a Full Node

---

## 🏗️ Architecture

```
slowfi-habit-tracker/
├── contracts/
│   ├── HabitVault.ts        # Core commitment + check-in + reward logic
│   ├── SlowFiPool.ts        # Community yield pool + penalty redistribution
│   ├── SlowFiBadge.ts       # OP_721 soulbound NFT milestone badges
│   └── SlowFiLeaderboard.ts # On-chain top-10 streak leaderboard
├── frontend/
│   └── src/
│       ├── components/      # Wallet, HabitCard, Dashboard, Leaderboard, BadgeShelf
│       ├── hooks/           # useHabitVault, useStreak, useSlowFiPool
│       └── constants/       # quotes.ts • habits.ts • badges.ts
├── scripts/
│   └── deploy.ts
├── tests/
│   └── habitvault.test.ts
└── README.md
```

### Smart Contract Summary

**`HabitVault.ts`** — The heart of SlowFi. Users commit BTC or $MOTO to a habit + streak duration. Daily check-ins are gated by block height (~144 blocks per day). On streak completion, stake + pro-rata yield is returned. On failure, 15% is slashed to the SlowFi Pool and 85% is returned.

**`SlowFiPool.ts`** — Accumulates penalty fees. Distributes yield to successful completions. Partially seeded by Motoswap trading fees via a read-only fee hook.

**`SlowFiBadge.ts`** — OP_721 non-transferable (soulbound) badges. Minted automatically at milestone streaks. Earned, not bought.

**`SlowFiLeaderboard.ts`** — Fully on-chain top-10 by longest active streak and total BTC committed.

---

## 🚀 Deploy & Test (Testnet)

### Prerequisites
```bash
node >= 18
npm install -g @op-net/cli
```

### 1. Clone & Install
```bash
git clone https://github.com/yourhandle/slowfi-habit-tracker
cd slowfi-habit-tracker
npm install
```

### 2. Configure Wallet
```bash
cp .env.example .env
# Add your Bitcoin testnet private key and OP_NET RPC endpoint
```

### 3. Compile Contracts
```bash
npm run build
# Compiles AssemblyScript contracts to WASM
```

### 4. Deploy to OP_NET Testnet
```bash
npm run deploy:testnet
# Deploys HabitVault → SlowFiPool → SlowFiBadge → SlowFiLeaderboard
# Prints contract addresses — save these for .env
```

### 5. Run Tests
```bash
npm test
# Runs habitvault.test.ts: commit, check-in, streak complete, streak broken, badge mint
```

### 6. Run Frontend
```bash
cd frontend
npm install
npm run dev
# Open http://localhost:5173
# Connect Xverse or UniSat wallet (testnet mode)
```

### 7. Test a Full Streak Flow
1. Connect wallet on testnet
2. Select "HODL This Week" → set 7-day streak → stake 0.0001 BTC
3. Check in once per day (or advance blocks on testnet)
4. Observe streak counter, fire animation 🔥, leaderboard position
5. At day 7: claim reward — stake + yield returned
6. "SlowFi Initiate" badge auto-minted to your wallet

---

## 🎨 UI Preview

- **Dark Bitcoin-orange theme** — `#F7931A` primary • `#1a1a2e` background
- Circular progress ring for streak (e.g., *Day 18 of 30*)
- Fire animation 🔥 on successful daily check-in
- Rotating motivational quotes:
  - *"Patience is the key to HODLing"*
  - *"Slow money wins the race"*
  - *"Stack sats, stack discipline"*
  - *"HODL is a lifestyle, not a trade"*
- Badge shelf • Leaderboard • MotoCat miles counter

---

## 🔗 Integrations

- **$MOTO** — Accept $MOTO as stake alternative via OP_20 transfer
- **MotoCat** — Write bonus miles to MotoCat integration interface (streak days × 10)
- **Motoswap** — Read-only fee hook seeds SlowFi Pool yield

---

## 💡 Why SlowFi on Bitcoin?

Because discipline is the rarest DeFi primitive. Anyone can ape in. HODLing through the dip, the doubt, and the noise — that takes conviction. SlowFi Habit Tracker makes that conviction programmable, verifiable, and rewarded. On Bitcoin Layer 1. Trustlessly. With no bridges, no wrappers, and no excuses.

*SlowFi — compound your discipline.*

---

## 🏅 Vibecoding Challenge

Built for the **OP_NET Vibecoding Challenge** using **Bob** (OP_NET's AI developer assistant) via MCP integration with Claude Code.

> `claude mcp add opnet-bob --transport http https://ai.opnet.org/mcp`

**Team:** [Your Name / Handle]
**Category:** DeFi • Productivity • Bitcoin Native
