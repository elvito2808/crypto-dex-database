# Project Status

- Project: Crypto DEX Database
- Repository: https://github.com/elvito2808/crypto-dex-database
- Status: `BOOTSTRAPPED`
- Current phase: Phase 1 — Chain Discovery
- Active task: `AGENT-01-CHAIN-DISCOVERY`
- Last checkpoint: 2026-11-09
- Current data status: No chain records researched or verified yet.

## Completed

- [x] Repository purpose and data principles documented.
- [x] Phase plan and acceptance criteria documented.
- [x] Agent 01 instructions created.
- [x] Initial data templates and source registry created.
- [x] Progress and handoff checkpoint files initialized.

## In progress

- [ ] Agent 01 researches and populates the chain inventory.
- [ ] Manager reviews coverage, evidence, duplicates, and status assignments.

## Decisions

1. The primary chain list contains only `VERIFIED` public mainnets.
2. Testnets, devnets, private/permissioned networks, and deprecated networks must be classified separately in metadata; they must not be silently mixed into the primary TXT list.
3. "All networks" is treated as a research objective, not a provable finite universe. Reports must state scope, coverage, exclusions, and limitations.
4. A chain is not automatically a separate network merely because it has a token, explorer, RPC endpoint, or EVM chain ID. Confirm independent network identity and operational evidence.
5. The DEX volume threshold applies to a measured 24-hour volume observation and must include source and UTC timestamp.

## Next action

Execute `agents/agent_01_chains/instructions.md`. Do not start downstream token or DEX inventory from unverified chain assumptions.
