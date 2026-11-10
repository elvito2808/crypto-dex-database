# Agent 01 — Handoff

## Current state
Batch 3 saved. Overall mission remains IN_PROGRESS and is not complete. Prior records were preserved; five focal records were re-audited and 14 additional candidates were added to the candidate matrix.

## Latest checkpoint
- UTC: 2026-11-10T00:06:50Z
- Batch 3 candidates examined: 19
- New candidates: 14
- Batch 3 unique canonical networks after dedup: 19
- Batch 3 end-state: 10 VERIFIED, 8 PROVISIONAL, 1 CONFLICT, 0 MISSING, 0 DEPRECATED
- Cumulative unique candidates: 28
- Cumulative: 18 VERIFIED, 8 PROVISIONAL, 1 CONFLICT, 0 MISSING, 1 DEPRECATED
- VERIFIED records in TXT: 18
- Official / first-party / maintained ecosystem registry sources: 59
- Independent sources: 7
- Total sources: 66

## Focal record results
1. Mantle — CONFLICT. Current docs provide MNT, chain ID 5000 and Mantlescan, but current docs call it a ZK validity rollup while archived official repo README calls it optimistic rollup / fraud proofs / EigenDA. Excluded from TXT.
2. OP Mainnet — VERIFIED. Official current network docs: Mainnet, chain ID 10, ETH, explorer.optimism.io; OP Stack architecture.
3. Blast — PROVISIONAL. Official docs route repeatedly 502; official repos confirm OP Stack fork and mainnet deployment process but not chain ID/gas/explorer. Independent sources report 81457 / ETH / Blastscan; not sufficient for VERIFIED.
4. Taiko — VERIFIED. Current official docs: chain ID 167000, ETH, Taikoscan, Mainnet RPC; current Unzen based Type-1 zkEVM rollup and mainnet contracts; Ethereum L1 settlement.
5. Starknet — VERIFIED. SN_MAIN = 0x534e5f4d41494e; STRK is current protocol fee token; ETH is a bridged token, not the fee token under current v0.14+ docs; Cairo VM; validity rollup settling to Ethereum; Voyager listed by Starknet.

## New verified networks in TXT
- Abstract (2741, ETH)
- Arbitrum Nova (42170, ETH; Nitro AnyTrust)
- Fraxtal (252, FRAX)
- Ink (57073, ETH)
- Soneium (1868, ETH)
- Unichain (130, ETH)
- Zircuit (48900, ETH)

## Provisional candidates excluded from TXT
- Blast
- Immutable zkEVM
- Sophon Mainnet
- Lens Chain
- Cronos zkEVM
- Manta Pacific
- World Chain
- Zora

## Deprecated / conflict
- Polygon zkEVM — DEPRECATED; official sequencer sunset 2026-07-03.
- Mantle — CONFLICT; current and archived official architecture statements disagree.

## Deduplication decisions
- Arbitrum One and Arbitrum Nova are distinct (42161 Rollup vs 42170 AnyTrust).
- Mainnet and corresponding testnet variants are not split into multiple production records.
- OP Stack and ZKsync Elastic Network are frameworks/ecosystems, not single network records. Each independently configured Mainnet is kept separate.
- Applications, tokens, bridges, RPC endpoints and explorers are not separate networks.

## Testnet exclusions
Arbitrum Sepolia (421614), Taiko Hoodi (167013), Mantle Sepolia (5003), OP Sepolia (11155420), Ink Sepolia (763373), Soneium Minato (1946), Unichain Sepolia (1301), Zircuit Garfield (48898), Abstract Testnet (11124), ZKsync Era Sepolia (300). These are environment variants, not production network entries.

## Files
- data/01_chains.txt
- data/01_chains_metadata.csv
- sources/source_registry.csv
- reports/research_reports/agent_01_chain_discovery.md
- reports/research_reports/agent_01_l2_candidate_matrix.csv
- agents/agent_01_chains/progress.md
- agents/agent_01_chains/handoff.md
- PROJECT_STATUS.md

## Exact resume point
1. Resolve Mantle architecture discrepancy with an authoritative versioned statement explaining current Mainnet architecture vs archived optimistic-rollup repo.
2. Retry Blast official docs after the 502 issue; inspect official deployment config and live RPC chain ID; seek first-party gas-token and explorer confirmation.
3. Close provisional evidence gaps in Immutable zkEVM, Sophon, Lens Chain, Cronos zkEVM, Manta Pacific, World Chain and Zora.
4. Continue expanding systematic candidate discovery across OP Stack, Arbitrum Orbit, ZK Rollups, Validiums/Volitions, and app-specific rollups. Keep the matrix updated and deduplicated.
5. Only after the L2 candidate matrix has been further expanded and reviewed, move to EVM L1 discovery.

## Unresolved details
- Mantle architecture: CONFLICT.
- Blast official docs inaccessible in this pass; critical fields remain provisional.
- Immutable current operations not established from non-deprecated official docs.
- Sophon / Lens / Cronos zkEVM need first-party current endpoints, explorer, VM and operational evidence.
- Manta needs first-party native fee and architecture confirmation.
- World Chain needs World-owned network documentation.
- Zora needs Zora-owned network parameters and fee-token confirmation.
- Broader Ethereum L2 universe remains open-ended; no completeness claim.

## Handoff rule
Preserve all canonical records and CSV column order. Keep TXT limited to VERIFIED active public production networks. Do not infer fee tokens or current activity from popularity. Record unknowns and conflicts explicitly. Synchronize all eight deliverables at each coherent checkpoint. Overall mission remains IN_PROGRESS.
