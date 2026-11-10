# Agent 05 — Verification and Integration Instructions

**Task ID:** `AGENT-05-VERIFICATION-AND-INTEGRATION`  
**Phase:** 6 — Verification and Integration  
**Status:** `COMPLETED`  
**Canonical branch:** `main`

## Mandate

Independently audit and integrate only the repository evidence already committed by Agents 01–04. Do not restart discovery or replace historical source decisions.

## Fixed scope

- Exactly 18 canonical VERIFIED public production Mainnets from `data/01_chains.txt`.
- 30 chain-token records; 30 stablecoin deployment records.
- 20 DEX protocol identities; 25 qualified chain deployments; 82 volume snapshots; 70 candidate/exclusion rows.
- 25 technical-detail rows; 150 fee-mechanics rows across six distinct fee classes.
- 125 Source Registry rows.
- All originating Agent issue logs: Agent 01 (14), Agent 02 (32), Agent 03 (118), Agent 04 (54).

## Mandatory controls

1. Validate CSV headers, field counts, row widths, primary-key uniqueness and populated timestamp syntax.
2. Validate canonical chain scope and every populated chain, protocol, deployment, candidate, snapshot and source reference.
3. Preserve native balance assets, wrapped/bridged representations and contract-backed fee tokens as distinct classes. Keep native gas separate from DEX fee payment assets.
4. Keep protocol identity separate from chain deployment.
5. Apply the strict arithmetic boundary `volume_24h_usd > 50000`; do not promote candidate-only CONFLICT or UNVERIFIED_VOLUME evidence.
6. Keep all six fee categories separate. Never fill UNKNOWN or PROVISIONAL without independent evidence.
7. Preserve each original issue ID and origin. Use `OPEN_DEFERRED_FINAL` where the available repository evidence does not establish resolution.
8. Keep source URL traceability explicit. Do not treat URL-to-registry mapping as a live link check.

## Prohibited actions

- No new DEX discovery, volume refresh, snapshot refresh, requalification, candidate re-review or modification of Agent 03 decisions.
- No re-opening Agent 01/02 discovery.
- No retry of any source with a previously recorded retrieval failure.
- No guessed value or unsupported status upgrade.
- No deletion or destructive rewriting of Agent 01–04 source artifacts.

## Outputs

- `data/final_crypto_dex_database.csv`
- `reports/research_reports/agent_05_verification_report.md`
- `reports/research_reports/agent_05_consolidated_issues.csv`
- `reports/research_reports/agent_05_validation_results.csv`
- `agents/agent_05_verification/instructions.md`
- `agents/agent_05_verification/progress.md`
- `agents/agent_05_verification/handoff.md`

The Data Dictionary, Project Status, Master Tasks and README are synchronized with the final state.

## Closure rule

The task may be completed when every in-scope control has been run, every possible output is committed and read back from GitHub, and all remaining issues are visible with explicit status and reason. UNKNOWN, PROVISIONAL, CONFLICT and OPEN_DEFERRED_FINAL do not block procedural completion.
