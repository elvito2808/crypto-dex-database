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

Agents 01–05 and Phase 6 are complete. The integrated output is `data/final_crypto_dex_database.csv` (807 rows); the full audit is `reports/research_reports/agent_05_verification_report.md`; 232 unresolved originating issues remain preserved (Agent 01–04: 218; Agent05: 14) in `reports/research_reports/agent_05_consolidated_issues.csv` with `OPEN_DEFERRED_FINAL` status. See `reports/research_reports/agent_05_validation_results.csv`, `PROJECT_STATUS.md`, `MASTER_TASKS.md` and `agents/agent_05_verification/handoff.md`.


## Final integrated database

- Canonical networks: 18 VERIFIED public production Mainnets.
- Integrated export: `data/final_crypto_dex_database.csv` — 807 rows, 25 columns, 807 unique record IDs and original payloads and traceable identifiers.
- Validation: `reports/research_reports/agent_05_validation_results.csv`.
- Open issue archive: `reports/research_reports/agent_05_consolidated_issues.csv` — 232 originating issues retained, including AG5-ISS-URL-0001 through AG5-ISS-URL-0014; completion does not imply resolution.


## Agent 05 bounded final correction

- Final integrated database: 807 data rows, 25 columns, 807 unique `record_id` values.
- Consolidated issue register: 232 rows — Agent01 14; Agent02 32; Agent03 118; Agent04 54; Agent05 14.
- Agent05 has logged the 14 existing used-but-unregistered URLs as `AG5-ISS-URL-0001` through `AG5-ISS-URL-0014`, each `SOURCE_REGISTRY_TRACEABILITY_GAP` and `OPEN_DEFERRED_FINAL`.
- Validation Results contains 33 controls; SR-03 explicitly references these 14 issues and remains `OPEN_DEFERRED_FINAL`.
- The original 218 Agent01–04 issues and `sources/source_registry.csv` are unchanged. No source was retrieved or retried.
