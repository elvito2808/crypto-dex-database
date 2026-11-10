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

Next task: `AGENT-04-DEX-TECHNICAL-DETAILS`. Do not expand the network scope.

## Phase 5 — DEX technical details
- [ ] Verify supported chains and deployment-specific availability.
- [ ] Record gas asset for single-chain deployments where relevant.
- [ ] Separate swap fee, protocol fee, LP fee, aggregator fee and network gas.
- [ ] Record fee payer and payment asset; do not infer fee token from chain native asset.
- [ ] Capture official UI and official explorer/deployment links.

Dependency: Phase 4 qualifying DEX inventory.

## Phase 6 — Verification and integration
- [ ] Deduplicate chains, assets, protocols and deployments.
- [ ] Audit source quality, timestamps, identifiers and conflicts.
- [ ] Validate CSV schemas, chain scope and referential integrity.
- [ ] Publish canonical database and audit report.

## Global exit criteria

- No guessed values presented as verified.
- Every critical claim has direct evidence and UTC audit time.
- Conflicts and unknowns remain explicit.
- Same-symbol assets remain separate unless contract, issuer and provenance evidence match.
- Output is reproducible and resumable.
