# Semina

Semina is a long-term experiment in building autonomous systems where rules matter more than operators.

It is not a product.
It is not a promise.
It is an environment.

This repository is the **canonical public source** for all documented elements of the Semina ecosystem.

---

## Project status

Semina is currently in **early Alpha / Beta**, with controlled exposure.

This means:
- active development
- evolving documentation
- intentional constraints
- no guarantees of outcome

This is not a failure state.
It is a deliberate design decision.

---

## Ecosystem overview

Semina is structured in layers:

### 1. Semina — the system
The conceptual and architectural foundation.

Semina defines how decentralized systems, AI processes, and human participation can coexist over time with minimal discretionary control.

It focuses on persistence, constraints, and observability rather than optimization or speed.

---

### 2. Solum — the ground
Solum is the economic substrate of Semina.

It is a fixed-rule token contract designed to behave predictably from launch.
Solum does not optimize for price or sentiment.
It defines the rules under which value can enter, move, and exit the system.

At this stage:
- the Solum contract is **defined and frozen**
- it has been **audited**
- it is intended to be deployed on **Base**, paired with **WETH** via **Uniswap V2**
- it is **not yet deployed** until the explicit launch event

Once deployed, the contract rules apply equally to all participants.

---

### 3. SolumWorld — on-chain civilization
SolumWorld is a transparency and interpretation layer.

It treats Solum as a living terrain:
- Solum is the ground
- wallets are colonists
- liquidity, treasury, and burn are visible structures
- history is cumulative and readable

SolumWorld is currently in **genesis phase**:
- publicly documented
- privately developed
- no live infrastructure yet

Its purpose is not speculation, but understanding.

---

## Canonical sources

Semina recognizes the following sources, in strict priority order:

1. **GitHub (this repository)**  
   Technical and documentary source of truth.  
   Code, contracts, and public design documents live here.

2. **Medium — Semina Core**  
   Conceptual explanations and system rationale.  
   Medium does not override the contract.

3. **X / Twitter**  
   Public communication and announcements.  
   Informational only, not normative.

4. **Web**  
   Public-facing surface, evolving with the project.  
   Summarizes, but does not define.

Rule:
If something is not written in GitHub or Medium, it is not treated as a promise.

---

## Key documents

### Genesis and structure
- Genesis: https://github.com/Semina-project/semina/tree/main/docs
- Semina overview: https://medium.com/@semina.core

### Solum
- Solum phase 1 overview: https://github.com/Semina-project/semina/blob/main/docs/solum-token-phase-1.md
- Solum contract (frozen): https://github.com/Semina-project/semina/blob/main/contract/SolumToken.sol

### SolumWorld
- SolumWorld documentation: https://github.com/Semina-project/semina/tree/main/docs/solumworld

---

## What “launch” means in Semina

For Solum, launch means only this:

- the contract is deployed
- initial liquidity is seeded (≈ 100 USD equivalent in ETH)
- the Uniswap V2 pool is opened

There are:
- no hidden phases
- no discretionary switches
- no post-launch tuning

From that moment, the system behaves exactly as coded.

---

## Disclaimer

This project is experimental.
Crypto systems involve risk.
Nothing here constitutes financial advice.

Semina does not promise outcomes.
It defines constraints.
