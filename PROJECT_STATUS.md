# Project Status

- Project: Crypto DEX Database
- Repository: https://github.com/elvito2808/crypto-dex-database
- Status: `IN_PROGRESS`
- Current phase: Phase 1 — Chain Discovery
- Active task: `AGENT-01-CHAIN-DISCOVERY`
- Last checkpoint: 2026-11-09T23:46:00Z
- Current data status: 4 initial candidate records researched and marked VERIFIED; broader discovery remains incomplete.

## Completed
- [x] Repository purpose and data principles documented.
- [x] Phase plan and acceptance criteria documented.
- [x] Agent 01 instructions and methodology reviewed.
- [x] Initial data templates and source registry reviewed.
- [x] First evidence-backed chain batch saved (4 records; 4 official documentation sources).

## In progress
- [ ] Complete candidate discovery across EVM and non-EVM ecosystems.
- [ ] Separately classify testnets/devnets, private networks, forks, and deprecated networks.
- [ ] Manager review of coverage, evidence, duplicates, and status assignments.

## Decisions
1. The primary chain list contains only `VERIFIED` public mainnets.
2. Testnets, devnets, private/permissioned networks, and deprecated networks must be classified separately in metadata; they must not be silently mixed into the primary TXT list.
3. "All networks" is treated as a research objective, not a provable finite universe. Reports must state scope, coverage, exclusions, and limitations.
4. A chain is not automatically a separate network merely because it has a token, explorer, RPC endpoint, or EVM chain ID. Confirm independent network identity and operational evidence.
5. The DEX volume threshold applies to a measured 24-hour volume observation and must include source and UTC timestamp.

## Next action
Continue Ethereum L2 / rollup discovery beyond Arbitrum One and ZKsync Era, then research EVM L1 networks. Do not start downstream token or DEX inventory from unverified chain assumptions.
