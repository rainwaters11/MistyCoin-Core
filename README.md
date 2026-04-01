# 🌊 MistyCoin-Core ($WATERS)
**Enterprise-Grade Web3 Ecosystem | Solidity Smart Contract Excellence**

> *"Building the systems that replace trust with mathematical certainty."* 🥂✨

---

## 🏗️ The Developer's Vision

As a **Web3 Developer and Solidity Smart Contract Expert**, I engineered MistyCoin-Core to demonstrate the peak of decentralized finance (DeFi) and autonomous governance. This repository is a masterclass in EVM architecture, featuring a modular, security-first approach to blockchain engineering.

From **constant product AMMs** to **oracle-driven insurance primitives**, every line of code here is built to be scalable, gas-optimized, and battle-tested.

This ecosystem was built as part of the **30 Days of Solidity** challenge — 30 days, 30 contracts, 100% code-complete.

---

## 🚀 Technical Architecture & Core Modules

### 🏦 Misty Bank — Decentralized Lending Pool
*Path: [`/modules/lending`](./modules/lending)*

Collateral-based lending with 5% APR simple interest and 75% Loan-to-Value enforcement.
- **Expert Insight:** Implements the **Basis Point Standard** (10,000 divisor) for precise integer interest math. `lastInterestAccrualTimestamp` is updated on both `borrow()` and `repay()` — preventing interest from being reset or double-counted. A silent accounting bug that trips up most junior developers.

---

### 🔐 Misty Treasury — Multi-Sig Wallet
*Path: [`/modules/multisig`](./modules/multisig)*

High-security shared custody with M-of-N confirmation logic.
- **Expert Insight:** Uses a **mapping-of-mappings** (`isConfirmed[txId][owner]`) for O(1) vote tracking — no loops, no gas spikes. The `executed` flag is set **before** the external call (Checks-Effects-Interactions), making reentrancy structurally impossible without a `nonReentrant` modifier.

---

### 📈 MistySwap — Automated Market Maker
*Path: [`/modules/amm`](./modules/amm)*

Decentralized exchange built on the **$x \cdot y = k$ Constant Product Formula**.
- **Expert Insight:** Includes a **0.3% LP fee** retained in the pool on every swap (fee grows `k`, rewarding long-term LPs). Features the **Babylonian square root** for gas-efficient geometric-mean LP token minting. All swaps include a `minOut` slippage guard enforced at the EVM level.

---

### 🛍️ Misty Market — Non-Custodial NFT Marketplace
*Path: [`/modules/marketplace`](./modules/marketplace)*

A universal NFT exchange supporting **any ERC-721 collection** — no re-deployment required for new collections.
- **Expert Insight:** Built on the **Approval Pattern** — the NFT never leaves your wallet until the buyer pays. `buyItem()` uses strict C-E-I: the listing is **deleted before** the NFT transfer and ETH payment. This is the reentrancy kill-shot that most "NFT marketplace tutorials" get wrong.

---

### 🌾 Misty Farm — Yield Farming Platform
*Path: [`/modules/yield-farming`](./modules/yield-farming)*

Per-second reward accrual with Curve veCRV-style lock-duration boost tiers.
- **Expert Insight:** Implements **4 boost multipliers** (1.0× flexible → 2.0× 365-day lock). Re-stakes snapshot existing earnings into `pendingRewards` before resetting the accrual window — preserving all historical earnings without double-counting. Includes an on-chain `calculateAPY()` view and `checkRewardSolvency()` to monitor pool health.

---

### 🗳️ Decentralized Governance (DAO)
*Path: [`/modules/governance`](./modules/governance)*

A complete governance layer for the $WATERS ecosystem.
- **Expert Insight:** Implements a **Timelock Controller** and **Quorum** requirements. Uses weighted voting power based on ERC-20 token snapshots to prevent flash-loan governance attacks.

---

### 🌾 CropGuard — Oracle Insurance Primitive
*Path: [`/modules/insurance`](./modules/insurance)*

Provably fair parametric insurance backed by Chainlink oracles.
- **Expert Insight:** Leverages **Chainlink Data Feeds** to pull off-chain data trustlessly. If the oracle reports conditions below the threshold, the contract triggers an automatic payout to policyholders — no human intermediary, no dispute process.

---

## 📅 30 Days — 30 Contracts

| Day | Contract | Module |
|-----|----------|--------|
| 01–10 | ERC-20, ERC-721, Voting, Staking, Lottery | Foundation |
| 11–20 | DEX, Flash Loans, Vaults, Insurance | DeFi Primitives |
| 21–22 | NFT Standards, Lottery VRF | Advanced Standards |
| 23 | SimpleLending | Misty Bank |
| 24 | SimpleMultiSig | Misty Treasury |
| 25 | AutomatedMarketMaker | MistySwap DEX |
| 26 | NFTMarketplace | Misty Market |
| 27 | YieldFarming | Misty Farm |
| 28 | DecentralizedGovernance | DAO |
| 29 | SimpleStablecoin (SUSD) | Algorithmic Stablecoin |
| 30 | MiniDexPair + Factory | Full DEX Integration |

---

## 🧪 The Expert Stack

| Tool | Purpose |
|------|---------|
| **Solidity ^0.8.20** | Latest security standards, checked arithmetic |
| **Foundry (Forge/Cast)** | Testing, deployment, fuzzing |
| **OpenZeppelin** | ERC-20, ERC-721, ReentrancyGuard, Ownable |
| **Chainlink VRF & Data Feeds** | Provably random numbers, oracle price feeds |

---

## 🛡️ Security Manifesto

In this ecosystem, **Code is Law**. Every module implements the industry's most rigorous security patterns:

| Pattern | Description |
|---------|-------------|
| **Checks-Effects-Interactions** | State mutations before ALL external calls — neutralizes reentrancy vectors |
| **Mutex Locks** | `nonReentrant` modifiers on every value-transfer function |
| **Integer Safety** | Solidity 0.8+ checked arithmetic — overflow/underflow impossible |
| **Immutable Variables** | Critical addresses hardcoded at deploy — reduced attack surface + gas savings |
| **Basis Point Precision** | 10,000 BPS divisor for all fee/rate math — no floating point, no precision loss |

---

## 🛠️ Installation

```bash
# Clone the repository
git clone https://github.com/rainwaters11/MistyCoin-Core.git
cd MistyCoin-Core

# Build all modules (Foundry required)
# Navigate to the module of interest, then:
forge build

# Run tests
forge test
```

---

## 🤝 Connect

**Misty Waters**
Web3 Developer | Solidity Smart Contract Expert

[![GitHub](https://img.shields.io/badge/GitHub-rainwaters11-181717?style=flat&logo=github)](https://github.com/rainwaters11)

---

*30 Days. 30 Contracts. 100% Code-Complete.* 🌊
