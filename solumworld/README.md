# SolumWorld — Technical Architecture (Genesis)

> Status: Genesis  
> Exposure: Public (documentation only)  
> Development: Private repository  

SolumWorld is a **read-only, interpretative layer** built on top of the Solum smart contract.
It does not alter protocol behavior, governance, or token mechanics.

Its purpose is **observation, transparency, and interpretation** — not control.

---

## 1. Conceptual Role

SolumWorld treats:

- **Solum** as the terrain (economic substrate)
- **Wallets** as colonists
- **Transactions** as movements across the terrain
- **Taxes, limits, burns** as environmental forces

SolumWorld does not judge behavior.
It exposes behavior.

---

## 2. System Boundary (Non-Negotiable)

SolumWorld is:

- ❌ NOT a governance layer
- ❌ NOT a trading interface
- ❌ NOT a wallet
- ❌ NOT a price optimization tool
- ❌ NOT a recommendation engine

SolumWorld is:

- ✅ Read-only
- ✅ Deterministic
- ✅ Reconstructible from on-chain data
- ✅ Transparent by design

---

## 3. High-Level Architecture

SolumWorld is designed as a **three-layer system**:

### Layer 1 — On-chain Data Source
- Solum smart contract (Base / EVM)
- DEX pool (Uniswap V2 compatible)
- Standard ERC-20 events:
  - Transfer
  - Swap
  - Sync
  - Burn / Fee redistribution (if applicable)

**Source of truth:** Blockchain only.

---

### Layer 2 — Indexing & Interpretation
- Event indexing (block-by-block)
- Wallet state reconstruction
- Historical balance evolution
- Interaction classification:
  - Hold
  - Buy
  - Sell
  - Transfer
- Contribution accounting:
  - Burn contribution
  - Liquidity reinforcement
  - Treasury inflow
  - Reflection effects (if applicable)

No predictions.
No simulations.
Only observed effects.

---

### Layer 3 — Presentation & UX
- Terrain-based visualization
- Wallets represented as entities (colonists)
- Time-aware views (evolution, not snapshots)
- Status layers:
  - Activity level
  - Interaction profile
  - Persistence over time

UX is informational, not persuasive.

---

## 4. Reputation & Status (Informational Only)

SolumWorld may expose **status indicators**, not scores:

- Based on observable behavior only
- No moral labeling (“good” / “bad”)
- No financial advice implications

Examples:
- Long-term holder
- High-frequency mover
- Liquidity contributor (via taxes)
- Net burner contributor

Status ≠ privilege  
Status ≠ reward  
Status ≠ governance

---

## 5. Data Integrity Principles

- Every displayed metric must be reproducible from raw on-chain data
- No hidden weighting
- No AI-driven scoring in Genesis
- No off-chain heuristics without explicit disclosure

If a metric cannot be reconstructed independently, it is not displayed.

---

## 6. Development Policy

- Public repository contains **documentation only**
- Active development occurs in a **private repository**
- Code will be exposed progressively, when:
  - architecture is stable
  - invariants are proven
  - attack surfaces are understood

This is intentional and explicit.

---

## 7. Why This Exists

SolumWorld exists to answer one question:

> “What is actually happening on-chain, if we stop narrating and start observing?”

It is built for:
- analysts
- builders
- researchers
- serious participants

Not for hype.
Not for persuasion.
Not for shortcuts.

---

## Genesis Note

This document defines **direction, boundaries, and intent**.
It is not a promise of features or timelines.

SolumWorld will evolve when the terrain itself proves stable enough to observe meaningfully.
