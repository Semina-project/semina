# SolumMap

SolumMap is the graphical and semantic representation of Solum territory.
It is not a dashboard, not a metrics panel, and not a UI for financial data.
SolumMap exists to visualize the state of land inside the Semina ecosystem.

It represents Solum as territory.
Nothing more. Nothing less.

---

## Core Concept

SolumMap displays the entire Solum territory as a finite, shared surface.

- Total surface: 100 trillion square meters (100T m²)
- Each unit represents 1 m² of Solum
- The map is deterministic and global
- The map evolves over time based on on-chain activity

SolumMap does not represent value, price, or performance.
It represents **state**.

---

## Territory States

Solum exists in different states depending on its position in the system.

### 1. Dormant Territory (Liquidity Pool)

Solum held inside the liquidity pool is considered **dormant land**.

- It is inactive
- It is infertile
- It represents uncolonized territory
- It is always available for future colonization

The liquidity pool is the reserve of unused land.

---

### 2. Active Territory (Wallets)

Solum held by wallets becomes **active land**.

- It is colonized
- It can evolve
- It reflects the history and behavior of its holder
- It changes state over time

Wallets are settlers.
Their land reflects participation, persistence, and interaction.

---

### 3. Transformed Territory (Burn)

Burned Solum is permanently transformed.

- It leaves circulation
- It becomes fertile land
- It represents irreversible contribution to the system
- It increases overall environmental richness

Burn is not destruction.
It is transformation.

---

## Wallets as Settlements

Wallets are represented as settlements on the map.

Their form and evolution depend on:

- Amount of Solum held
- Duration of holding
- Interaction frequency
- Historical behavior

Possible representations include:

- Fields
- Farms
- Villages
- Cities

There is no moral judgment.
Selling, transferring, or holding are all valid actions.

---

## Technical Execution Model

SolumMap is built as a deterministic visualization layer on top of blockchain data.

### Data Source

- Primary source: Solum smart contract events
- Secondary source: indexed blockchain state
- No off-chain interpretation of meaning
- No manual overrides

All map transformations are derived from verifiable on-chain data.

---

### Indexing Layer

SolumMap relies on an indexing process that:

- Processes transfers, burns, and liquidity movements
- Aggregates state changes per wallet and per territory unit
- Produces periodic snapshots of the global land state

This layer is designed to be:

- Stateless between snapshots
- Reproducible from genesis
- Verifiable by third parties

---

### Rendering Model

The map is rendered from snapshots, not live transactions.

- Each snapshot represents a coherent world state
- Visual changes are applied atomically
- No partial or intermediate states are shown

This avoids visual noise and preserves narrative continuity.

---

### Update Cadence

SolumMap is not rendered in real time.

To preserve coherence and user experience:

- Updates occur at fixed intervals
- Rapid on-chain oscillations are smoothed
- Large state changes are aggregated

The objective is interpretability, not immediacy.

---

### Scalability Considerations

The system is designed to scale with activity:

- Snapshot frequency is configurable
- Rendering resolution adapts to zoom level
- Historical states can be replayed or compared

High activity increases richness, not instability.

---

## What SolumMap Does Not Show

SolumMap deliberately excludes:

- Treasury balances
- Financial metrics
- Real-time transaction feeds
- Price data

These elements are transparent and accessible,
but they belong to **SolumWorld**, not SolumMap.

---

## Purpose

SolumMap exists to:

- Provide a shared, intuitive mental model
- Turn abstract blockchain data into visible territory
- Allow observation without speculation
- Make system evolution understandable over time

SolumMap is land.
SolumWorld is the world built on top of it.
