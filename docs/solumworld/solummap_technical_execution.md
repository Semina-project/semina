# SolumMap — Technical Execution Plan (On-chain → World → Tiles)

SolumMap is the *map renderer* of Solum’s on-chain reality.
It turns token and pool activity into a coherent, navigable territory.

This document describes *how we will build it*:
protocols, data flow, indexing, storage, rendering, and update strategy.

---

## 1) Scope and contract reality

SolumMap reads *real* state transitions from the chain and expresses them visually.

- **Source of truth:** Base L2 (Solum token contract + Uniswap V2 pair)
- **SolumMap output:** a square territory representing the system over time
- **SolumWorld vs SolumMap:**
  - **SolumWorld** = web platform / dashboards / narratives / deep analytics
  - **SolumMap** = territory-only visualization (no overlays that block the map)

SolumMap must be faithful to chain data **without becoming visually chaotic**.

---

## 2) Data sources (protocol-level)

SolumMap needs two data streams:

### A) Solum token events
From the Solum contract logs:
- `Transfer(address from, address to, uint256 value)` (core)
- Any custom events (burn accounting, treasury, etc.) *only if emitted on-chain*

**We do not infer state from narratives. We infer from logs.**

### B) Uniswap V2 pool events (SOLUM/WETH on Base)
From the pair contract logs:
- `Swap(...)`
- `Mint(...)` / `Burn(...)` (LP changes)
- `Sync(...)` (reserve updates)

This allows:
- detecting buys vs sells
- mapping pool “dormant Solum” vs circulating “active Solum”
- tracking liquidity evolution at a technical level

---

## 3) Ingestion architecture (RPC → Indexer)

### Recommended approach (production-grade)
**Dedicated indexer service + database.**

- **RPC provider:** Base mainnet endpoint (provider or self-hosted node later)
- **Indexer:** Node.js/TypeScript (or Go) service that:
  - scans blocks
  - subscribes to new blocks
  - decodes logs
  - writes normalized records to DB

**Why:** we cannot rely on the front-end to query chain logs directly at scale.

### Optional later layer
- The Graph / Subgraph (nice-to-have)
  - Great for queries
  - Still requires careful schema design
  - Not mandatory for v0 if we control our own indexer

---

## 4) Storage model (events → state → map)

### Database
- **PostgreSQL** for canonical indexed data
- Optional **Redis** for hot caches (latest aggregates, tile snapshots)

### Core tables (minimum)
- `blocks` (number, hash, timestamp)
- `solum_transfers` (tx_hash, log_index, from, to, amount, block_number, timestamp)
- `amm_swaps` (tx_hash, log_index, buyer/seller, amount_in/out, reserves, block_number, timestamp)
- `wallet_state` (wallet, active_solum, last_seen, tags/flags)
- `map_cells` (cell_id, biome_type, intensity, last_updated, derived_metrics)
- `tile_snapshots` (zoom, x, y, image_url, generated_at, checksum)

**Important:** we store *raw events* and *derived state* separately.

---

## 5) World model (how chain data becomes territory)

SolumMap represents a fixed, square territory with a defined total area.

### Territory definition
- **Total territory:** fixed square world
- **World area basis:** `100T` Solum represented as “territory units”
- **Cell concept:** the world is divided into cells (tiles at different zooms)
- A cell does not represent “a wallet.”  
  A cell represents **state derived from on-chain flow**.

### Dormant vs Active Solum (pool semantics)
- **Solum in the liquidity pool** = *dormant / inactive / infertile availability*
- **Solum leaving the pool** = becomes *active territory* (colonizable)
- **Solum returning to the pool** = becomes *dormant again* (availability restored)

This preserves the logic:
the pool is always the “inventory” of uncolonized / infertile ground.

### Visual grammar (example mapping)
- **Dormant (in pool):** barren / sterile ground
- **Active circulation:** fields / villages / roads appear with stability
- **Burned Solum:** permanent fertility markers (forests, rivers, lakes)
- **Redistributed to holders:** “harvest” effect (subtle, not spammy)
- **Treasury:** tracked in SolumWorld dashboards, **not rendered as a map region**
  - Treasury is visible as data, but not embodied as territory

---

## 6) Rendering approach (retro, 4-bit / 16-color)

SolumMap is intentionally *simple and readable*, with a retro aesthetic.

### Rendering stack options
**Option A (2D pixel world — recommended for SolumMap)**
- Front-end renderer: **PixiJS** (WebGL 2D) or Canvas 2D
- Tiles: pre-rendered sprite sheets + tile textures
- Map navigation: pan/zoom, minimap, coordinates

**Option B (3D globe / Earth-like later)**
- MapLibre + custom raster tiles (2D)
- Or Three.js for a true sphere
- This is optional and later; v0 should ship as 2D square world first

**Key rule:** the map must remain legible at every zoom.

---

## 7) Tiling system (zoom levels)

SolumMap must support:
- “see the whole world” view
- smooth zoom into regions
- stable user experience (no flicker)

### Tile pyramid
- Zoom 0: entire world in one view
- Zoom 1..N: progressively smaller tiles (standard web map model)

We generate tiles as:
- **raster** (PNG/WebP) for simplicity and performance
- optionally **vector** later for advanced styling

### Tile generation pipeline
- A worker process aggregates new chain events into `map_cells`
- Another worker generates updated tiles affected by those cells
- Store tiles in:
  - object storage (S3-compatible) or simple static hosting initially
  - CDN in front for scale

---

## 8) Update cadence (truthful but not chaotic)

SolumMap must show everything that happens,
but it must not look like a slot machine.

### Strategy: “truthful batching”
- Index events continuously
- Update map state continuously in DB
- **Publish map visuals on a cadence**
  - e.g. every **5–15 minutes** at v0
  - configurable per zoom:
    - Zoom 0–1: slower refresh (coherent “world view”)
    - Zoom 2–4: medium
    - Zoom 5+: faster if needed, but still bounded

### Session stability
When a user is viewing a region:
- keep their rendered view stable
- apply updates as “ticks” (soft transitions)
- never replace the entire scene every few seconds

---

## 9) Scaling plan (if Solum activity grows)

High activity means:
- more events per hour
- more derived updates
- more tile regen pressure

We scale by:
- append-only event ingestion
- partitioned tables (by block ranges)
- background aggregation jobs
- tile invalidation by region (only update what changed)
- caching tile snapshots aggressively (CDN)

### Infra baseline (practical)
- **Hetzner VPS** for indexer + DB + workers
- Start small, scale vertically first
- Add:
  - Redis
  - separate worker nodes
  - managed Postgres later if needed

---

## 10) Minimal deliverable (v0 execution sequence)

### v0.1 — ingestion + canonical DB
- Solum transfers indexed
- Pool swaps indexed
- Simple API endpoints

### v0.2 — world state + cell model
- Active/dormant logic working
- Burn → fertility persistence
- Redistribute → harvest metric

### v0.3 — tile renderer + web viewer
- Pan/zoom, minimap
- Retro 16-color tiles
- Scheduled updates (not live spam)

### v0.4 — performance and credibility
- deterministic tile generation
- checksums for snapshots
- reproducible builds for the map state

---

## Non-goals (for clarity)

- No “price prediction”
- No gamified rewards implied
- No moral judgment layer (“good wallets / bad wallets”) in SolumMap
  - SolumWorld may *label patterns* analytically, but SolumMap stays territorial

SolumMap is a visualization of consequence, not intention.
It exists to be observed.
```0
