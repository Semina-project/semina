# SolumWorld — Technical Structure (Genesis)

## Purpose of this document

This document describes the **technical intent and structural design** of SolumWorld.

It is written to:
- communicate seriousness and direction to advanced users
- clarify architectural decisions
- explicitly state what is public and what remains private at this stage

This is not a roadmap.
This is not an implementation guide.
It is a structural declaration.

---

## Architectural Position in Semina

SolumWorld is a **read-only observational layer** built on top of Solum.

It does not:
- execute transactions
- modify contract behavior
- influence on-chain rules

SolumWorld observes.
Solum enforces.

This separation is intentional and irreversible.

---

## Core Data Sources

SolumWorld is derived exclusively from **on-chain data**:

Primary sources:
- Solum smart contract events
- Liquidity pool state
- Treasury movements
- Burn events
- Wallet interaction history

No off-chain assumptions.
No oracle interpretation.
No predictive modeling in genesis.

---

## Conceptual Layers

### 1. Data Ingestion Layer
- Indexes Solum contract events
- Tracks pool, treasury, burn, and transfers
- Time-ordered, immutable history

### 2. Interpretation Layer
- Translates raw data into semantic states
- Examples:
  - fertility (liquidity depth)
  - activity (transaction density)
  - contribution (tax flows)
- No scoring with economic consequences

### 3. Visualization Layer
- Terrain-based representation
- Civilization / colonization metaphor
- State evolution over time

This layer is expressive, not gamified.

---

## Wallet Representation (Colonists)

Wallets are represented as **actors**, not accounts.

SolumWorld does not label wallets as:
- good
- bad
- malicious
- trusted

It exposes:
- behavior
- duration
- interaction patterns

Interpretation is left to the observer.

---

## Reputation and Status (Non-Enforced)

Any reputation or status signal in SolumWorld is:
- informational
- non-binding
- non-transferable
- without protocol privilege

No wallet gains rights.
No wallet is restricted.

Visibility is not control.

---

## Security and Integrity

SolumWorld has **no signing authority**.

- No private keys
- No execution permissions
- No upgrade authority over Solum

Failure of SolumWorld does not affect Solum.
Failure of Solum affects SolumWorld visibility only.

---

## Development Boundary

At genesis:

- Concept and structure are public
- Codebase is private
- Infrastructure decisions are internal
- No API guarantees are made

This is intentional.

SolumWorld will be exposed progressively once:
- data integrity is proven
- representation is coherent
- misinterpretation risk is reduced

---

## Closing

SolumWorld is not a product feature.
It is an epistemic layer.

It does not optimize behavior.
It reveals consequences.

This document defines *how it will be built*,
not *when it will be delivered*.
