# Agent 01 — Handoff

## Current state
Batch 3 research was saved and subsequently finalized under the finalization order. Agent 01 status is now COMPLETED; no further chain discovery is requested.

## Latest checkpoint
- UTC: 2026-11-10T00:06:50Z
- Batch 3 candidates examined: 19
- New candidates: 14
- Batch 3 unique canonical networks after dedup: 19
- Batch 3 end-state: 10 VERIFIED, 8 PROVISIONAL, 1 CONFLICT, 0 MISSING, 0 DEPRECATED
- Cumulative unique candidates: 28
- Cumulative: 18 VERIFIED, 8 PROVISIONAL, 1 CONFLICT, 0 MISSING, 1 DEPRECATED
- VERIFIED records in TXT: 18
- Official / first-party / maintained ecosystem registry sources: 60
- Independent sources: 11
- Total sources: 71

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
2. Blast retrieval failures and remaining evidence gaps are archived for final project review; do not retry the failed sources.
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
Preserve canonical records and CSV column order. Keep TXT limited to VERIFIED active public production networks. Do not infer unknown values. All unresolved Agent 01 cases are archived for final project review. Agent 01 is COMPLETED.


## Permanent retrieval policy and Batch 3 correction (2026-11-10T15:30:00Z)
- Do not retry any source after any retrieval failure (HTTP, timeout, DNS/SSL, access, load or read error). Record each independent failure with exact URL/location and UTC logging time in `reports/research_reports/agent_01_retrieval_issues.csv`.
- Blast's two previously reported HTTP 502 failures are logged as RET-000001 (docs root) and RET-000002 (network-information route). No further request to either URL is permitted. The original failure timestamps were not available; log timestamp is explicitly identified as formal detection/logging time.
- Blast stays PROVISIONAL. Canonical chain symbol, chain ID, network identifier, current Mainnet status and official explorer are UNKNOWN where unverified by first-party evidence; third-party values remain non-canonical notes. Exclude from TXT.
- Mantle stays CONFLICT because current official docs and archived official repo make materially different architecture claims. This is an evidence conflict, not a retrieval error.
- TXT policy: only VERIFIED active public Mainnets. Current count is 18. No testnets, devnets, private/permissioned networks, experimental environments, deprecated networks or uncertain candidates.
- Reconciled counts: 28 candidates; 18 VERIFIED, 8 PROVISIONAL, 1 CONFLICT, 0 MISSING, 1 DEPRECATED; 18 TXT names; 2 retrieval issue rows; 72 source registry entries.

## Historical unresolved details (archived for final project review; no immediate action)

## FINAL HANDOFF — AGENT-01 COMPLETED (2026-11-10T15:30:00Z)

Agent 01 — Chain Discovery is `COMPLETED`. No further chain research, retries, repeated source checks or resolution of archived issues is requested under this task.

### Final reconciled inventory
- Candidate records: 28
- VERIFIED: 18
- PROVISIONAL: 8
- CONFLICT: 1
- MISSING: 0
- DEPRECATED: 1
- Active public VERIFIED Mainnets in `data/01_chains.txt`: 18
- Source registry: 72 entries
- Candidate matrix: 28 data rows
- Retrieval issue register: 14 rows total (2 retrieval failures + 12 unresolved evidence/field cases)

Only VERIFIED public operational Mainnets remain in TXT. PROVISIONAL and CONFLICT networks remain excluded; the DEPRECATED Polygon zkEVM record remains outside the active list. All unresolved cases and UNKNOWN fields are retained in `reports/research_reports/agent_01_retrieval_issues.csv` for final project review. They are not assigned as immediate resolution work to the next agent.

### Next project phase
The next phase is discovery and registration of **Native Tokens, Wrapped Tokens and Stablecoins** associated with the 18 VERIFIED networks. The next agent should begin that token inventory using the verified network list as its scope. This is a new phase, not a continuation of Agent 01 chain research.

### Closure rule
Do not reopen Agent 01 or retry previously failed sources unless a project manager explicitly authorizes a separate later review. Agent 01 status is `COMPLETED`.
