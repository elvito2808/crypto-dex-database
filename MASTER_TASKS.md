# Master Task Plan

## Phase 0 — Repository bootstrap
- [x] Define project scope and evidence policy.
- [x] Create repository structure and agent handoff templates.
- [x] Prepare Agent 01 instructions.

## Phase 1 — Chain discovery
- [x] Identify and classify the accepted canonical public networks.
- [x] Verify canonical identity and core network metadata for the 18 main-list entries.
- [x] Publish `data/01_chains.txt`, chain metadata, research report and handoff.
- [x] Close Agent 01 as COMPLETED; keep unverified/conflict/deprecated candidate records outside the main TXT.

Acceptance: met for the accepted 18-network baseline. Agent 01's deferred candidate universe stays archived for final project review; it is not part of Agent 02 or Agent 03 scope.

## Phase 2 — Native and wrapped assets
- [x] Map native balance assets and gas/fee assets separately across all 18 target chains.
- [x] Distinguish native coin balances from contract-backed fee tokens and bridged/wrapped representations.
- [x] Record available contract/mint identifiers, decimals, issuer/bridge and evidence.
- [x] Preserve UNKNOWN fields and incomplete wrapped-token catalogues in the issue register.
- [x] Publish `data/02_chain_tokens.csv` and the Agent 02 report.

Agent 02 status: COMPLETED. The asset inventory is evidence-backed but not an exhaustive on-chain token census; see the issue register.

## Phase 3 — Stablecoins
- [x] Identify issuer- or network-documented stablecoin deployments on target chains.
- [x] Separate native stablecoin issuance from bridged representations (for example USDC and USDC.e).
- [x] Record peg/backing, issuer, chain, contract/mint, decimals, origin and mechanism where evidenced.
- [x] Label yield-bearing stablecoin wrappers separately from independent issuers.
- [x] Preserve UNKNOWN fields and chain coverage gaps in the issue register.
- [x] Publish `data/03_stablecoins.csv`.

Agent 02 status: COMPLETED. Seven networks retain stablecoin-discovery evidence gaps; the lack of an entry is not interpreted as proof that no stablecoin exists.

## Phase 4 — DEX discovery
- [x] Discover DEX protocols and distinct deployments on the 18 canonical networks.
- [x] Qualify only observed 24-hour volume strictly above USD 50,000.
- [x] Record provider/source, observation timestamp UTC, volume, chain, protocol and deployment identity.
- [x] Keep below-threshold and unverified candidates in separate review/exclusion records.
- [x] Publish protocol registry, qualified deployment registry, volume snapshots, candidate log, issue log, research report and Agent 03 handoff.

Agent 03 status: COMPLETED. 20 qualified protocol identities; 25 qualified deployments; 82 volume snapshots; 70 non-qualified/unresolved candidates; 118 issue records. See `reports/research_reports/agent_03_dex_discovery.md`. Exact provider UTC window boundaries and several deployment identifiers remain UNKNOWN, documented for Agent 04.

Phase 4 / Agent 03 is closed. Its discovery decisions and deferred discovery/volume issues remain preserved; Phase 5 followed without expanding the network scope.

## Phase 5 — DEX technical details
- [x] Process the 25 existing qualified deployments only; add no new DEX, protocol, deployment or network.
- [x] Record supported deployment chain identifiers, Native Gas Token, technical identifiers, UI and explorer with evidence status.
- [x] Separate swap/trading, LP, protocol, aggregator, network gas and builder/solver fee categories.
- [x] Record fee rate/formula, payer, recipient, deduction stage and fee-payment asset where evidenced; retain UNKNOWN/PROVISIONAL otherwise.
- [x] Publish 25 technical rows, 150 fee rows, 54 issue rows, research report and Agent 04 handoff.
- [x] Align Data Dictionary and Source Registry.

Dependency: Phase 4 qualifying DEX inventory.

## Phase 6 — Verification and integration (COMPLETED; Agent 05)

Owner: `AGENT-05-VERIFICATION-AND-INTEGRATION` — Agent 05 is responsible for the independent verification and integration work below.

- [x] Deduplicate and integrate canonical chains, assets, protocols, deployments and source-linked records.
- [x] Audit source quality, timestamps, identifiers, status boundaries and conflicts; document source URL registry gaps.
- [x] Validate CSV schemas, canonical chain scope, volume threshold arithmetic and referential integrity.
- [x] Preserve all 218 originating Agent 01–04 issues and append 14 Agent05 source registry traceability issues; all unresolved records use OPEN_DEFERRED_FINAL.
- [x] Publish integrated database, validation results, consolidated issue register, audit report and Agent 05 handoff.

Agent 04 handoff to Agent 05: keep all 54 records in `reports/research_reports/agent_04_retrieval_issues.csv` unresolved and available for Phase 6 review. Do not delete, downgrade or report them as resolved without independent evidence. Agent 04 remains `COMPLETED`; these are accepted open issues, not a reopened Agent 04 task.

## Global exit criteria

- No guessed values presented as verified.
- Every critical claim has direct evidence and UTC audit time.
- Conflicts and unknowns remain explicit.
- Same-symbol assets remain separate unless contract, issuer and provenance evidence match.
- Output is reproducible and resumable.


Agent 04 status: `COMPLETED`. All 20 registered protocol identities and 25 deployments are represented. Unresolved technical and fee evidence gaps are documented in the Agent 04 issue log and deferred to Phase 6; no further rediscovery or retry is part of this phase.

## Agent 04 closeout / Agent 05 handoff

- Agent 04 status: `COMPLETED`.
- Preserved Agent 04 final counts: 20 protocols, 25 deployments, 150 fee records, 54 unresolved issues and 125 Source Registry records.
- All Phase 5 tasks above are complete. Remaining Agent 04 UNKNOWN/PROVISIONAL matters stay visible for Agent 05 in Phase 6.
- Next active task: `NONE` — Agent 05 completed Phase 6; remaining evidence gaps are archived in the consolidated issue register.


## Phase 6 / Agent 05 closeout

- Task `AGENT-05-VERIFICATION-AND-INTEGRATION`: `COMPLETED`.
- Integrated export after bounded final correction: 807 data rows, 25 columns and 807 unique type-prefixed record IDs.
- Issue consolidation: 232 rows: original Agent01 14 + Agent02 32 + Agent03 118 + Agent04 54 (218 retained unchanged), plus Agent05 14 source traceability issues. All 232 remain `OPEN_DEFERRED_FINAL`.
- Canonical network scope remains the exact 18 VERIFIED Mainnets in `data/01_chains.txt`.
- DEX inventory remains 20 protocol identities and 25 qualified deployments. No additional discovery, volume refresh or requalification was performed.
- Fee categories remain six independent types with 25 records each; UNKNOWN and PROVISIONAL values remain.
- Data Dictionary extended for all 128 unique source CSV fields and Agent 05 export schemas.
- Source Registry issues (three duplicate URL groups, 14 used-but-unregistered URLs and six unreferenced entries) are disclosed; the 14 unregistered URLs are individually logged as AG5-ISS-URL-0001..0014. SR-03 remains OPEN_DEFERRED_FINAL. No source was retried and no speculative registry entries were added.
- Original Agent 01–04 artifacts remain unchanged. Phase 6 is closed; remaining evidence gaps are handed off for archival awareness, not as new discovery authorization.


## Agent 05 bounded final correction — 14 Source Registry traceability issues

- [x] Append `AG5-ISS-URL-0001` through `AG5-ISS-URL-0014` to the consolidated issue register.
- [x] Add matching `AGENT_ISSUE` records to the final integrated database.
- [x] Preserve all 218 original Agent 01–04 issue rows unchanged; consolidated count is 232.
- [x] Validate 807 master rows, 25 columns, and 807 unique `record_id` values.
- [x] Update SR-03 to reference all 14 new issues while retaining `OPEN_DEFERRED_FINAL`.
- [x] Synchronize the report, progress, handoff, validation register, project status and README.
- [x] Keep `sources/source_registry.csv` unchanged; perform no source fetch, retry or speculative URL registration.
