# Agent 01 — Chain Discovery Research Report

- Task: AGENT-01-CHAIN-DISCOVERY
- Batch: 3 — Ethereum L2 evidence closure and expanded discovery
- Checkpoint: 2026-11-10T00:06:50Z
- Overall mission status: IN_PROGRESS (not complete)

## Scope and method

Preserved all prior canonical network records and original CSV column order. Reviewed five focal records (Mantle, OP Mainnet, Blast, Taiko, Starknet) and identified 14 additional L2 candidates from official ecosystem documentation, official registries and independent discovery indexes. Candidate identities were deduplicated by canonical network, not ticker, framework, RPC endpoint or app name. Official sources were prioritized; independent sources were only cross-checks or discovery leads. The new candidate matrix records all 28 cumulative candidates, including non-included candidates.

## Batch 3 statistics

- Candidates examined in this batch: 19 (five focal records + 14 newly identified candidates)
- Newly identified candidates: 14
- Distinct canonical networks after deduplication in this batch: 19
- Batch 3 end-state status counts: VERIFIED 10; PROVISIONAL 8; CONFLICT 1; MISSING 0; DEPRECATED 0
- Newly identified VERIFIED networks: 7
- Newly identified PROVISIONAL candidates: 7
- Newly identified CONFLICT candidates: 0
- Newly identified MISSING candidates: 0
- Newly identified DEPRECATED candidates: 0
- Existing records materially revised: 5 (Mantle, OP Mainnet, Blast, Taiko, Starknet)
- TXT records after Batch 3: 18

## Cumulative statistics (Batches 1–3)

- Unique candidate records in metadata and matrix: 28
- Unique canonical candidate networks after deduplication: 28
- VERIFIED: 18
- PROVISIONAL: 8
- CONFLICT: 1
- MISSING: 0
- DEPRECATED: 1
- Records in `data/01_chains.txt`: 18
- Official / first-party / maintained ecosystem registry sources: 60
- Independent / non-official cross-check and discovery sources: 7
- Total source registry entries: 71

Status arithmetic: 18 + 8 + 1 + 0 + 1 = 28. TXT contains only VERIFIED records.

## Focal evidence closure

### Mantle — NOT CLOSED; CONFLICT
Direct current Mantle documentation now provides Mainnet RPC, chain ID 5000, MNT currency symbol and Mantlescan explorer. Current docs describe Mantle as an EVM-compatible ZK validity rollup with modular DA and Ethereum settlement. The official archived GitHub repository README, however, describes an optimistic rollup with EVM fraud proofs and EigenDA. This is a material architecture discrepancy between official sources. The record is therefore CONFLICT and is removed from TXT pending a clear version/upgrade explanation. Fields other than architecture are supported by current official docs.

### OP Mainnet — CLOSED; VERIFIED
Current official OP Mainnet network documentation directly states Mainnet, chain ID 10, ETH currency symbol, explorer `https://explorer.optimism.io` and RPC `https://mainnet.optimism.io`. Official OP Stack docs substantiate optimistic-rollup architecture. Record remains VERIFIED.

### Blast — NOT CLOSED; PROVISIONAL
Attempted official docs root and network-information route; both returned HTTP 502. Inspected official `blast-io/blast` and `blast-io/deployment` repositories. They establish Blast's Optimism fork / OP Stack lineage, Blast execution client and mainnet node deployment path, but the inspected official README does not state chain ID, native gas symbol or canonical explorer. Third-party sources corroborate chain ID 81457, ETH and Blastscan, but are insufficient for VERIFIED. Keep PROVISIONAL and exclude from TXT. Reattempt first-party docs and inspect raw deployment config / explorer once accessible.

### Taiko — CLOSED; VERIFIED
Current official Connect-to-Taiko docs state Mainnet chain ID 167000, RPC, Taikoscan and ETH; Hoodi testnet is separately 167013. Current official protocol docs describe a Type-1 zkEVM based rollup, Ethereum L1 validator sequencing, ZK + SGX multi-proof verification and current Unzen fork. Current official contract-address docs list Mainnet L1 and Mainnet L2 protocol contracts. The official Taiko node/tooling repository provides additional current Mainnet confirmation. The prior launch-announcement-only gap is closed.

### Starknet — CLOSED; VERIFIED
The previous inaccessible-docs issue is resolved: current official Starknet docs are accessible.
- Network identifier: `SN_MAIN`, encoded as `0x534e5f4d41494e`; not an EVM chain ID.
- Architecture: official docs call Starknet a validity rollup and state that proofs and state diffs are posted to Ethereum.
- VM/runtime: Cairo VM / Cairo execution environment.
- Parent / settlement: Ethereum.
- Explorer: Starknet's official website lists Voyager and Starkscan.
- Fee token distinction: current fee documentation (v0.14+) requires STRK-denominated resource bounds and describes the fee as an atomic transfer of STRK to the sequencer. The official bridged-token registry separately lists both ETH and STRK as tokens on Starknet. ETH is therefore a bridged asset, not the current protocol fee token. No ETH fee option is asserted. Paymaster sponsorship, if used by an application, does not change the protocol's fee denomination.
Starknet is now VERIFIED and included in TXT.

## Newly identified candidates

### VERIFIED and added to TXT (7)
1. Arbitrum Nova — chain 42170; ETH; Nitro AnyTrust (DAC), distinct from Arbitrum One Rollup; official Arbitrum docs list Nova and explorer.
2. Ink — chain 57073; ETH; Ethereum OP Stack L2; official Ink docs identify public Mainnet and explorer.
3. Fraxtal — chain 252; FRAX; modular OP Stack rollup; official docs explicitly name FRAX as native gas token.
4. Soneium — chain 1868; ETH; Ethereum OP Stack optimistic rollup; official docs provide Mainnet parameters and Blockscout explorer.
5. Unichain — chain 130; ETH; OP Stack Stage 1 Ethereum rollup; official Uniswap developer docs provide network parameters and Uniscan.
6. Zircuit — chain 48900; ETH; OP Stack-derived ZK rollup / zkVM proving; official docs provide Mainnet RPC, explorer, chain ID and ETH.
7. Abstract — chain 2741; ETH; ZKsync Elastic Network / Ethereum DA; official Abstract docs repository provides Mainnet network parameters, and official ZKsync registry lists Abstract Mainnet.

### PROVISIONAL and excluded from TXT (7)
1. Blast — chain 81457 and ETH corroborated independently; first-party docs returned 502 and inspected official repos do not close key network fields.
2. Immutable zkEVM — legacy official docs list chain 13371, IMX and explorer, but the docs are deprecated and current operational status needs verification.
3. Sophon Mainnet — official ZKsync registry lists chain 50104, SOPH and Avail DA; project-specific RPC, explorer and current operational status not verified.
4. Lens Chain — official ZKsync registry lists chain 232, GHO and Avail DA; project-specific RPC, explorer and current operation need first-party confirmation.
5. Cronos zkEVM — official ZKsync registry lists chain 388, zkCRO and NoDA; current project-specific runtime, explorer and operation not verified.
6. Manta Pacific — official Manta network-info site lists Mainnet RPC, chain 169 and explorer; ETH and OP Stack/Celestia architecture are presently corroborated by third parties rather than the retrieved first-party page.
7. World Chain — Etherscan-operated WorldScan confirms Mainnet and chain 480; Alchemy corroborates ETH and Optimism framework, but a World first-party network reference was not retrieved.

### Zora — PROVISIONAL and excluded from TXT
Zora is included in the seven above? Yes: Zora is the seventh provisional candidate; official Optimism Superchain Registry lists it as a mainnet L2, chain 7777777, Ethereum DA, RPC and explorer. The Graph corroborates ETH gas and OP Stack. First-party Zora network parameters were not retrieved, so it remains PROVISIONAL.

## Candidate categories covered

- Optimistic / OP Stack: OP Mainnet, Base, Mode, Ink, Soneium, Unichain, Fraxtal, Zora, Blast (provisional), Zircuit (OP-derived ZK), and other OP-family candidates in the matrix.
- Arbitrum Orbit / Nitro: Arbitrum One and Arbitrum Nova; Orbit chains beyond these remain open.
- ZK rollups: Linea, Scroll, ZKsync Era, Taiko, Starknet, Zircuit, Abstract, Immutable zkEVM (provisional).
- Validium / external DA / modular ZK: Sophon, Lens Chain and Cronos zkEVM from the official ZKsync Elastic Network registry; DA categories recorded as Avail / NoDA. Manta Pacific's Celestia DA description is not promoted beyond PROVISIONAL because current direct first-party evidence was incomplete.
- App-specific / ecosystem rollups: Ink, Unichain, Soneium, Fraxtal, Abstract, Sophon, Lens, and others. Their framework/brand is not treated as a network identity without independent mainnet evidence.

## Deduplication decisions

- Arbitrum One and Arbitrum Nova remain separate networks: official Arbitrum docs assign different chain IDs and different Nitro modes (Rollup vs AnyTrust).
- Taiko Mainnet and Taiko Hoodi are one production network plus a testnet, not two production entries.
- Ink Mainnet and Ink Sepolia are one production network plus testnet.
- Soneium Mainnet and Minato are one production network plus testnet.
- Unichain Mainnet and Unichain Sepolia are one production network plus testnet.
- Zircuit Mainnet and Garfield are one production network plus testnet.
- Abstract Mainnet and Abstract Testnet are one production network plus testnet.
- ZKsync Elastic Network is an ecosystem of multiple chains; Abstract, Sophon, Lens Chain and Cronos zkEVM are not merged into ZKsync Era.
- OP Stack is a framework, not itself a network; OP Mainnet, Ink, Soneium, Unichain, Fraxtal and Zora remain separate chains.
- Testnet aliases, RPC endpoints, bridges, applications and explorers are not separate networks.

## Exclusions

- Testnets excluded from primary TXT: Arbitrum Sepolia (421614), Taiko Hoodi (167013), Mantle Sepolia (5003), OP Sepolia (11155420), Ink Sepolia (763373), Soneium Minato (1946), Unichain Sepolia (1301), Zircuit Garfield (48898), Abstract Testnet (11124), and ZKsync Era Sepolia (300). These remain environment variants, not separate production records.
- Private RPC endpoints are infrastructure access points, not private networks.
- Polygon zkEVM remains DEPRECATED following official sequencer sunset on 2026-07-03; excluded from TXT.
- Mantle is excluded pending resolution of the architecture conflict.
- Blast, Immutable zkEVM, Sophon, Lens Chain, Cronos zkEVM, Manta Pacific, World Chain and Zora are excluded pending evidence closure.

## Sources

The source registry now contains 60 official / first-party / maintained ecosystem-registry entries and 7 independent sources (66 total). Official sources are linked to individual claims in metadata and the candidate matrix. Independent sources are clearly marked as research or explorer sources and are never treated as project-owned documentation.

Key direct sources:
- Mantle current network parameters: https://docs.mantle.xyz/network/for-users/how-to-guides/connecting-wallet-to-mantle-network
- Mantle current architecture: https://docs.mantle.xyz/network/introduction/overviews
- Mantle legacy repo (architecture discrepancy): https://github.com/mantlenetworkio/mantle
- OP Mainnet: https://docs.optimism.io/op-mainnet/network-information/connecting-to-op
- Blast official repositories: https://github.com/blast-io/blast and https://github.com/blast-io/deployment
- Taiko network parameters: https://docs.taiko.xyz/quickstart/connect
- Taiko current protocol: https://docs.taiko.xyz/protocol/overview
- Starknet fees: https://docs.starknet.io/learn/protocol/fees
- Starknet rollup/data availability: https://docs.starknet.io/learn/protocol/data-availability
- Starknet official Mainnet token registry: https://github.com/starknet-io/starknet-addresses/blob/master/bridged_tokens/mainnet.json
- Arbitrum Nova: https://docs.arbitrum.io/chain-info
- Ink: https://docs.inkonchain.com/general/network-information
- Fraxtal: https://docs.frax.com/fraxtal/network/network-information
- Soneium: https://docs.soneium.org/docs/builders/sfa
- Unichain: https://developers.uniswap.org/docs/unichain/technical-information/network-information
- Zircuit: https://docs.zircuit.com/build/start
- Abstract: https://github.com/Abstract-Foundation/abstract-docs/blob/main/connect-to-abstract.mdx
- ZKsync ecosystem candidate registry: https://docs.zksync.io/zksync-network/environment
- Manta: https://pacific-info.manta.network/
- Zora: https://github.com/ethereum-optimism/superchain-registry/blob/main/chainList.json

## Unresolved issues

1. Mantle architecture discrepancy: current docs say ZK validity rollup; archived official repo says optimistic rollup. Need a versioned protocol migration explanation or an authoritative statement that identifies the active Mainnet architecture.
2. Blast: official docs retrieval failed with 502; obtain current docs and inspect official mainnet config, live RPC chain ID, fee asset and canonical explorer.
3. Immutable zkEVM: determine whether Mainnet remains actively supported and obtain non-deprecated current docs.
4. Sophon, Lens Chain, Cronos zkEVM: obtain project-owned current network docs, RPC, explorer, VM/runtime and current activity; ZKsync ecosystem listing alone is not enough.
5. Manta Pacific: obtain first-party direct confirmation of native gas token and architecture/DA, and current operating status.
6. World Chain: obtain World-owned network configuration and OP Stack/settlement details; current values rely on explorer/provider corroboration.
7. Zora: obtain current Zora-owned network parameter page and gas token confirmation; registry and third-party evidence are not enough for VERIFIED.
8. Expand candidate discovery further across Arbitrum Orbit, additional OP Stack chains, ZK Stack, Validium, Volition and app-specific rollups; the candidate list remains a scoped sample, not an exhaustive universe.
9. Reconcile Mantle architecture and review all candidates for duplicates/status before expanding beyond Ethereum L2.

## Coverage assessment and next handoff

Batch 3 closed the direct-evidence gaps for OP Mainnet and Taiko, upgraded Starknet from MISSING to VERIFIED, and improved but did not close Blast and Mantle. Seven new networks were verified and added to TXT. Seven additional candidates remain provisional. This is not comprehensive coverage of all Ethereum L2s and makes no claim of completeness.

Exact next action: resume from `agents/agent_01_chains/handoff.md`. First resolve Mantle architecture and retry Blast first-party docs; then close the seven provisional candidates, especially Immutable, Sophon, Lens Chain, Cronos zkEVM, Manta Pacific, World Chain and Zora. Continue systematic OP Stack, Arbitrum Orbit, ZK Rollup, Validium/Volition and app-specific rollup discovery. Do not move to EVM L1 until L2 candidate coverage and deduplication have been further expanded. Overall mission remains IN_PROGRESS.
