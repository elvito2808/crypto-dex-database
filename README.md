# Crypto DEX Database

A source-traceable research database of public blockchain networks, native and wrapped assets, stablecoins, and active decentralized exchanges.

## Project goals

1. Build a documented inventory of blockchain networks.
2. Identify native and wrapped tokens for each network.
3. Inventory native/ecosystem and bridged stablecoins.
4. Discover DEXs with verified 24-hour trading volume strictly greater than **USD 50,000**.
5. Record DEX chain coverage, fee mechanics, fee-payment assets, official UI and explorer links.
6. Preserve evidence, timestamps, uncertainty, and handoff checkpoints so work can be resumed safely.

## Data principles

- Evidence before inclusion; never infer missing facts.
- Every material claim must be traceable to a source.
- Distinguish mainnets, testnets, private networks, deprecated networks, and forks.
- Keep source observations and derived conclusions distinguishable.
- Record volume observation time and source. The DEX threshold is a discovery filter, not a claim of permanent eligibility.
- Use `UNKNOWN` when a value cannot be established.
- Use the project status vocabulary: `VERIFIED`, `PROVISIONAL`, `CONFLICT`, `MISSING`, `DEPRECATED`.
- Never overwrite uncertainty with a guessed value.

## Repository map

- `PROJECT_STATUS.md` — current project state and decisions.
- `MASTER_TASKS.md` — phases, dependencies, and acceptance criteria.
- `docs/` — research methodology, schema, and quality rules.
- `data/` — normalized deliverables.
- `agents/` — agent instructions, progress, and handoffs.
- `reports/` — research and audit reports.
- `sources/source_registry.csv` — source catalogue.

## Execution order

1. Chain discovery.
2. Native and wrapped token research, plus stablecoin research (parallel after chain baseline).
3. DEX discovery using the 24h volume threshold.
4. DEX technical details and fee research.
5. Independent verification and deduplication.
6. Integration into the canonical database.

## Checkpoint / handoff rule

At every meaningful checkpoint, an agent must save its data, update its `progress.md` and `handoff.md`, and register sources. An agent must prioritize a resumable checkpoint over continuing unsaved research.

## Current phase

Agent 01 — Chain Discovery: `COMPLETED`. Agent 02 — Token and Stablecoin Discovery: `COMPLETED`. Agent 03 — DEX Discovery: `COMPLETED`. The current phase is Phase 5 — DEX Technical Details; next task: `AGENT-04-DEX-TECHNICAL-DETAILS` (not yet started). See `PROJECT_STATUS.md` and `agents/agent_03_dex/handoff.md`.
