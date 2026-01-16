# SolumWorld — Technical Architecture (Conceptual)

## 1. Purpose of SolumWorld

SolumWorld exists to make the on-chain life of Solum observable, interpretable, and narratable over time.

It is not designed to optimize behavior, guide users, or influence outcomes.
Its sole purpose is to expose how a rule-based economic substrate evolves once released into an open system.

SolumWorld answers a single technical question:

How does a fixed-rule smart contract behave when inhabited by a real community over time?

The focus is not price, but structure.
Not prediction, but observation.

---

## 2. Data Sources (On-chain)

SolumWorld derives all primary data directly from the Solum smart contract and its associated liquidity pool.

The system only consumes publicly available, on-chain information, including:

- Transfer events
- Buy and sell interactions via the DEX pool
- Burn events
- Liquidity changes
- Treasury flows
- Total and circulating supply
- Wallet balances and movements

No private data, no off-chain signals, and no inferred intent are used.

Key principle:
SolumWorld reads the chain.  
It does not write to it.

---

## 3. Data Interpretation Layer (Off-chain)

Raw on-chain data is not altered, but it is contextualized.

The off-chain layer exists to:

- Aggregate events over time
- Detect patterns of activity and inactivity
- Measure flows rather than snapshots
- Translate raw metrics into interpretable states

Examples of derived states (non-exhaustive):

- Activity intensity
- Persistence over time
- Contribution to system flows (burn, liquidity, treasury)
- Temporal participation patterns

These interpretations are descriptive, not prescriptive.
They describe what has happened, not what should happen.

---

## 4. Representation Layer (Conceptual UX)

SolumWorld represents system evolution through spatial and civilizational metaphors.

Core representations include:

- Solum as terrain (the economic substrate)
- Wallets as colonists (participants inhabiting the terrain)
- Liquidity and treasury as infrastructure
- Burns as irreversible transformation of the landscape
- Time as a first-class dimension

These representations are symbolic interfaces for understanding,
not gamified mechanics.

They do not alter incentives.
They do not introduce rewards.
They do not change outcomes.

They only make structure visible.

---

## 5. Neutrality and Non-Intervention

SolumWorld is strictly non-interventionist.

It does not:

- Recommend actions
- Rank wallets by “good” or “bad” behavior
- Trigger alerts
- Signal entry or exit points
- Provide trading advice
- Influence governance

There are no calls to action embedded in the system.

SolumWorld shows.
Users decide.

---

## 6. Relationship with Semina and Aitopia

SolumWorld is a subsystem within the Semina ecosystem.

- Semina defines the philosophical and structural frame
- Solum defines the economic rules
- SolumWorld observes the consequences
- Aitopia may interpret or narrate observations, but does not operate SolumWorld

No component overrides another.
No layer has discretionary control over the others.

This separation preserves system integrity.

---

## 7. Explicit Non
