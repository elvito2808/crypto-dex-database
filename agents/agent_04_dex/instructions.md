# Agent 04 — DEX Technical Details

**Task ID:** `AGENT-04-DEX-TECHNICAL-DETAILS`  
**Status:** `COMPLETED`  
**Branch:** `main`

## Fixed scope
Use only the 20 protocol IDs in `data/04_dex_registry.csv`, 25 deployment IDs in `data/05_dex_deployments.csv`, and 18 networks in `data/01_chains.txt`. Never add DEXs, protocols, deployments or chains.

## Rules
1. Keep protocol identity and chain deployment separate.
2. Use only direct official documentation, official repositories or trusted explorer evidence for technical addresses.
3. Addresses must be specific to the exact network; never copy from a sibling-chain deployment.
4. Keep UNKNOWN, PROVISIONAL, CONFLICT, MISSING and NOT_APPLICABLE separate.
5. Keep Native Gas Token distinct from DEX Fee Payment Token.
6. Store SWAP_TRADING_FEE, LIQUIDITY_PROVIDER_FEE, PROTOCOL_FEE, AGGREGATOR_FEE, NETWORK_GAS_FEE and BUILDER_SOLVER_FEE as separate rows.
7. Record rate/formula, payer, recipient, deduction stage, requirement, payment token, variance, source URL and UTC timestamp.
8. Preserve Agent 03 files and decisions. Do not revisit volume, snapshots, candidates or qualification.
9. Do not retry a source already marked as retrieval failure in earlier phases.
10. Document unresolved cases and defer them to Phase 6; do not perform endless research.

## Outputs
See `data/07_dex_technical_details.csv`, `data/08_dex_fee_mechanics.csv`, `reports/research_reports/agent_04_retrieval_issues.csv`, `reports/research_reports/agent_04_dex_technical_details.md`, and handoff.
