# Semina

Semina is an early-stage experiment: a framework for building long-lived systems that remain coherent while progressively reducing human centrality.

This repository is intentionally **technical and minimal**:
- The **contract** is the source of truth.
- The **docs** explain constraints, boundaries, and intent.
- No marketing. No promises. No roadmap. Only a horizon.

---

## Status

Semina is in **Alpha / early Beta** by design.

What this means:
- controlled exposure
- evolving surfaces
- incomplete UX in some areas
- concepts and structure documented openly

What does **not** change during early stages:
- the canonical technical reference lives here on GitHub
- the Solum contract and its early-phase rules are treated as stable

---

## Canonical sources (priority order)

1) **GitHub (this repo)** — canonical technical source  
   The contract, parameters, and documented invariants live here.

2) **Medium** — canonical conceptual narrative (interpretation, not authority)  
   https://medium.com/@semina.core

3) **X / Twitter** — public updates (informational, not normative)  
   https://x.com/AiTopia_Cloud

4) **Web** — evolving public surface  
   https://www.aitopia.cloud

Rule: if anything conflicts, **GitHub prevails** for technical truth.

---

## Start here (recommended reading order)

1) **Architecture**  
   `docs/architecture.md`

2) **Genesis**  
   `docs/GENESIS.md`

3) **Abstract**  
   `docs/abstract.md`

4) **Solum (contract + notes)**  
   `contract/SolumToken.sol`  
   `contract/README.md`

5) **SolumWorld (observability layer)**  
   `docs/solumworld/README.md`

---

## Components

### Solum (token contract)
Solum is the economic substrate of Semina.
It defines constraints and on-chain behavior, not outcomes.

- Source: `contract/SolumToken.sol`
- Technical notes: `contract/README.md`

### SolumWorld (observability layer)
SolumWorld is a user-facing world/interface designed to make Solum legible:
a coherent visual narrative built from on-chain facts.

- Docs: `docs/solumworld/README.md`

### SolumMap (territorial representation)
SolumMap is the **map layer**: territory only.
It visualizes the system’s “ground” and colonization dynamics.

- Spec: `docs/solumworld/solummap.md`

Note: treasury is not rendered inside SolumMap’s territory view; it belongs to SolumWorld metrics.

---

## Documentation map

- `docs/README.md` — full documentation index (table of contents)
- `docs/architecture.md` — boundaries and structure
- `docs/GENESIS.md` — founding constraints and rationale
- `docs/abstract.md` — short conceptual summary
- `docs/aitopi.md` — Aitopi interface definition (if present/used)
- `docs/solumworld/` — SolumWorld + SolumMap

---

## What Semina is NOT

Semina is not:
- a promise of returns
- a marketing funnel
- a roadmap-driven product
- a system that relies on continuous human intervention

Semina is:
- a constrained experiment
- a public technical artifact
- a set of rules that can be observed over time

---

## Official links

- Web: https://www.aitopia.cloud  
- Medium: https://medium.com/@semina.core  
- X / Twitter: https://x.com/AiTopia_Cloud
