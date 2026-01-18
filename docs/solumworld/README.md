# SolumWorld

SolumWorld is the public-facing web platform that visualizes Solum as a living on-chain environment: **the terrain**, the **colony**, and the **history** of its evolution.

This documentation is intentionally **audit-friendly**:
- it defines what SolumWorld is (and is not),
- how it maps on-chain events into a coherent world,
- and where to find the canonical sources of truth.

> Implementation note: the SolumWorld codebase is being developed in a **private repository** at this stage.  
> This public repo remains the **canonical documentation + contract reference**.

---

## What SolumWorld is

SolumWorld turns on-chain facts into a visual narrative:
- the **pool** is represented as the available “inactive terrain” (uncultivated / infertile ground),
- circulating Solum becomes “active territory” held by colonists (wallets),
- burns and other structural flows become visible changes over time (fertility, recovery, growth),
- the system remains **neutral**: actions are not moralized. They are interpreted as dynamics.

SolumWorld exists to provide:
- transparency,
- observability,
- and a user-facing way to understand Solum without needing explorers or raw logs.

---

## SolumMap vs SolumWorld

### SolumWorld (platform)
A full product surface:
- dashboards, narratives, UX layers, optional “live” metrics
- explanations and guided interpretation
- multiple views (overview + deep dives)

### SolumMap (map-only visualization)
A dedicated map layer:
- shows *only the territory* and its transformations
- can support zoom levels and time-based snapshots
- is designed to remain readable and coherent (not chaotic)

SolumMap is a **representation**, not a game.  
It must remain faithful to on-chain reality while presenting changes in a way that humans can follow.

---

## Design principles

1) **On-chain truth first**  
SolumWorld is derived from blockchain data. If a state cannot be computed from chain data, it must be marked as an assumption or excluded.

2) **Audit posture**  
Everything important should be explainable from:
- the contract code,
- public docs in this repo,
- and publicly released articles.

3) **Neutral interpretation**  
Buying, selling, transferring, holding: none of these are “good” or “bad” by default. They are system dynamics.

4) **Coherent UX over raw realtime chaos**  
SolumWorld may show realtime metrics when it improves understanding.  
SolumMap must prioritize readability: updates can be batched (e.g., snapshots) so the map remains stable and meaningful at each zoom level.

---

## Document index

- **SolumMap (concept + mapping rules)**  
  `docs/solumworld/solummap.md`

- **SolumWorld (foundational concept)**  
  `docs/solumworld/solumworld_onchain_civilization.md`  
  (If this file does not exist yet, it is the intended canonical home for the concept.)

- **System architecture (Semina-wide)**  
  `docs/architecture.md`

- **Solum contract (source of truth)**  
  `contract/SolumToken.sol`

---

## Official links (informational)

These links are provided for transparency and discovery.  
Some may be minimal or under construction during early stages.

- X (Twitter): `@AiTopia_Cloud`
- Medium: `https://medium.com/@semina.core`
- Web: `https://www.aitopia.cloud`

---

## Status

SolumWorld is in early active development.
Documentation evolves openly; implementation ships progressively under controlled exposure.

If you are reviewing this as a developer:
- start from `docs/architecture.md`,
- then read `contract/SolumToken.sol`,
- then return here for SolumWorld and SolumMap mapping rules.
```0
