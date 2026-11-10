# Agent 01 — Handoff

## Current state
Batch 2 saved. Overall mission remains IN_PROGRESS and is not complete. Four initial records were preserved and amended only where new official evidence justified it.

## Latest checkpoint
- Timestamp: 2026-11-10T00:00:52Z
- Candidates examined/recorded: 14
- VERIFIED: 10
- PROVISIONAL: 2
- CONFLICT: 0
- MISSING: 1
- DEPRECATED: 1
- VERIFIED public production networks in TXT: 10
- Official sources: 19
- Independent / non-official sources: 2
- Total source registry entries: 21

## Existing records audited
1. Arbitrum One — ETH is native gas asset; chain ID 42161; Nitro optimistic rollup.
2. Celestia — TIA native asset; Cosmos SDK PoS; Mainnet Beta remains explicitly experimental; Celenium is listed in official docs as a community explorer; VM remains UNKNOWN.
3. Solana — SOL fee asset confirmed; mainnet cluster identity; no numeric EVM chain ID.
4. ZKsync Era — ETH currency, chain ID 324, official explorer.

## New verified records in TXT
Base (8453), Linea (59144), Mantle (5000), Mode (34443), OP Mainnet (10), Scroll (534352). All use documented gas symbols: ETH except Mantle (MNT).

## Candidate records not in TXT
- Blast — PROVISIONAL: third-party docs corroborate chain ID 81457 and ETH, but first-party Blast docs were not retrieved.
- Taiko — PROVISIONAL: Taiko Labs launch announcement reports mainnet, chain ID 167000 and explorers; current first-party network configuration and gas asset need verification.
- Starknet — MISSING: official docs could not be retrieved/inspected; all technical parameters remain UNKNOWN.
- Polygon zkEVM — DEPRECATED: Polygon says sequencer sunset completed 2026-07-03 and blocks stopped.

## Exclusions
- Testnets excluded as separate records from TXT: Base Sepolia, Linea Sepolia, ZKsync Era Sepolia, Mode Sepolia, Scroll Sepolia and Arbitrum Sepolia. They are environments, not production chains.
- Private RPC endpoints are not separate chains; no private network entered TXT in this batch.
- Polygon zkEVM excluded as deprecated.
- Blast/Taiko/Starknet excluded from TXT until evidence thresholds are met.

## Files
- data/01_chains.txt
- data/01_chains_metadata.csv
- sources/source_registry.csv
- reports/research_reports/agent_01_chain_discovery.md
- agents/agent_01_chains/progress.md
- agents/agent_01_chains/handoff.md
- PROJECT_STATUS.md

## Exact resume point
First retrieve and review first-party current network parameter pages for Blast, Taiko and Starknet. Resolve their mainnet status, architecture, chain ID, native fee asset and explorer. Then continue systematic discovery of additional Ethereum L2/Rollup networks beyond the ten candidates audited in Batch 2. Do not move to EVM L1 until the expanded L2 candidate matrix has been searched and deduplicated.

## Remaining categories
- Broader Ethereum L2 / rollups and validiums.
- EVM L1.
- Additional non-EVM L1 and architectures.
- Sidechains.
- Cosmos / IBC.
- Substrate-based networks.
- Appchains / subnets.
- Separate testnet/devnet, private/permissioned, fork/renamed and deprecated catalogues.
- Cross-source conflict and duplicate review.

## Outstanding uncertainties
- Celestia general-purpose VM: UNKNOWN.
- Blast: official docs/status verification gap.
- Taiko: current first-party configuration and native gas token verification gap.
- Starknet: first-party documentation access and all technical parameters.
- Overall chain universe remains open-ended; coverage is partial.

## Handoff rule
Continue using official evidence first. Preserve UNKNOWN values, do not promote provisional/missing records without new primary evidence, keep TXT limited to VERIFIED active public production networks, and synchronize all seven outputs at each checkpoint.
