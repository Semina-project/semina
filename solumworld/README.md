# SolumWorld — Genesis (Public Spec)

SolumWorld is a monitoring and transparency layer for the Solum ecosystem.

Conceptually:
- **Solum is the terrain** (the on-chain economic substrate).
- **Wallets are colonists** (participants interacting with that terrain).
- SolumWorld is the *map* — a way to observe the ground evolving in real time.

This is not a “marketing site”.  
It is a technical interface for visibility, analysis, and long-horizon participation.

---

## Status

**Public repository:** documentation/spec only (Genesis).  
**Development:** private repository (beta closed).  
Reason: reduce noise while the core architecture stabilizes.

The moment the system is stable enough to be audited productively, code will be exposed.

---

## Goals

SolumWorld exists to provide:

1. **Transparency**
   - On-chain activity, clearly represented.
   - Pool evolution over time (price, liquidity, flow).
   - Tax-derived system contributions (where applicable).

2. **A Solum-native UX**
   - The UI should reflect Solum’s philosophy: ground, colonization, slow emergence.
   - Think “SimCity-style” readability, not a trader terminal.

3. **Community visibility**
   - Wallets as “colonists” (purely descriptive).
   - Optional *status / reputation* signals for analysis, not judgment.

---

## Non-goals (important)

- SolumWorld does **not** tell users what to do.
- SolumWorld does **not** label wallets as “good/bad” as a moral statement.
- SolumWorld does **not** promise outcomes or price behavior.
- SolumWorld is not a replacement for reading the contract and docs.

---

## Canonical sources

SolumWorld only treats these as authoritative:

- **Semina GitHub (contracts + docs)**  
  https://github.com/Semina-project/semina
- **Semina Medium (interpretation / narrative)**  
  https://medium.com/@semina.core
- **Web (alpha surface)**  
  https://www.aitopia.cloud
- **X/Twitter (announcements)**  
  https://twitter.com/AiTopia_Cloud

If something isn’t in those sources, SolumWorld must present it as **model / estimate**, not fact.

---

## Architecture (v0)

SolumWorld is built as three components:

### 1) Indexer (Base / EVM)
- Watches chain events from a known start block
- Consumes logs (examples):
  - `Swap`, `Sync` (AMM pool)
  - `Transfer` (token movements)
- Writes normalized data into Postgres
- Reorg-safe (confirmation depth + rollback strategy)

### 2) API (read-only)
- Serves clean endpoints for the UI and external reading
- Typical outputs:
  - current / historical price (derived from pool)
  - pool reserves over time
  - swaps (buy/sell classification where possible)
  - holder distribution snapshots
  - system contribution estimates (tax-derived, when applicable)
- Rate-limited and cacheable

### 3) UI (Solum-native)
A dashboard designed around readability:
- **Terrain view:** pool state and evolution
- **Events view:** swaps/transfers timeline
- **Colonists view:** wallets, distribution, behavior patterns
- **Metrics view:** burns / liquidity reinforcement / treasury flow (when derivable)

---

## “Reputation / Status” (informational)

SolumWorld may provide a *status layer* for wallets, but with strict constraints:

- It is **non-binding** and **non-authoritative**
- It is **behavioral**, not moral
- It must acknowledge that:
  - selling is not “bad”
  - transfers are not “bad”
  - these actions can contribute to liquidity, treasury, and holder dynamics depending on contract rules

This layer exists to make information visible, not to create social coercion.

---

## Infrastructure choice (beta closed)

Initial deployment target:
- **Hetzner VPS**
- Dockerized services:
  - Postgres
  - Indexer
  - API
  - Next.js frontend
- Public access via:
  - **solumworld.aitopia.cloud** (when enabled)

---

## Release philosophy

No fixed dates.

SolumWorld will be exposed publicly when:
- indexing is stable
- data is consistent under reorgs
- the UI communicates clearly without misrepresenting the system

Until then:
- this repo holds the public spec
- development remains private

---

## Next public milestone

A minimal “read-only alpha”:
- pool overview
- event timeline
- basic colonist list
- basic metrics

Everything else grows from there.

SolumWorld is not a product pitch.  
It is an instrument panel for a system that intends to last.
