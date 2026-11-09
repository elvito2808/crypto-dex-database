# Master Task Plan

## Phase 0 — Repository bootstrap
- [x] Define project scope and evidence policy.
- [x] Create repository structure and agent handoff templates.
- [x] Prepare Agent 01 instructions.

## Phase 1 — Chain discovery
- [ ] Identify candidate public mainnets across EVM and non-EVM ecosystems.
- [ ] Classify L1, L2/rollup, sidechain, appchain, subnet, and other network types.
- [ ] Separately record testnets/devnets, private networks, forks, and deprecated networks.
- [ ] Verify canonical identity, status, official documentation, explorer, and identifiers.
- [ ] Produce `data/01_chains.txt`, `data/01_chains_metadata.csv`, research report, and handoff.

Acceptance: all main-list entries are VERIFIED, deduplicated, source-backed, and have a clear network identity. Uncertain records remain outside the main TXT list.

## Phase 2 — Native and wrapped assets
- [ ] Map native gas/fee asset(s) per chain.
- [ ] Distinguish native issuance from bridged/wrapped representations.
- [ ] Capture contract/mint identifiers, decimals, issuer/bridge, and evidence.
- [ ] Record ambiguous or chain-specific representations without conflating tickers.

Dependency: Phase 1 chain baseline.

## Phase 3 — Stablecoins
- [ ] Identify fiat-backed, crypto-backed, commodity-backed, and algorithmic stablecoins.
- [ ] Distinguish native deployments from bridged representations.
- [ ] Record issuer, peg, deployment chain, contract/mint address, decimals, status, and evidence.
- [ ] Avoid assuming that same-symbol assets share issuer, backing, or contract.

Dependency: Phase 1 chain baseline; can run alongside Phase 2.

## Phase 4 — DEX discovery
- [ ] Discover DEX protocols and distinct deployments.
- [ ] Measure 24h volume and retain only observations strictly above USD 50,000 for the qualifying inventory.
- [ ] Record provider/source, observation timestamp UTC, volume, chain, and protocol/deployment identity.
- [ ] Keep below-threshold and unverified candidates in a separate excluded/review log where useful.

Dependency: chain baseline; token and stablecoin work provides context but is not a hard prerequisite.

## Phase 5 — DEX technical details
- [ ] Verify supported chains and deployment-specific availability.
- [ ] Record gas asset for single-chain deployments where relevant.
- [ ] Separate swap fee, protocol fee, LP fee, aggregator fee, and network gas.
- [ ] Record fee payer and payment asset; do not infer fee token from chain native token.
- [ ] Capture official UI and official explorer/deployment links.

Dependency: Phase 4 qualifying DEX inventory.

## Phase 6 — Verification and integration
- [ ] Deduplicate chains, assets, protocols, and deployments.
- [ ] Audit source quality, timestamps, identifiers, and conflicting claims.
- [ ] Validate CSV schemas and referential integrity.
- [ ] Publish canonical database and audit report.

## Global exit criteria

- No guessed values presented as verified.
- Each critical claim has evidence and retrieval date.
- Conflicts and unknowns remain explicit.
- Data is reproducible and resumable from the latest checkpoint.
