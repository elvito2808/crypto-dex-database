# Agent 01 — Chain Discovery Research Report

- Task: AGENT-01-CHAIN-DISCOVERY
- Batch: 2 — existing-record audit and Ethereum L2 / rollup discovery
- Checkpoint: 2026-11-10T00:00:52Z
- Overall mission status: IN_PROGRESS (not complete)

## Method and scope

Re-read repository instructions, data dictionary, methodology, status, handoff, and current data files before extending the existing dataset. Preserved the four original canonical records; audited their native fee assets and core fields against official documentation. For the L2 batch, checked ten named candidates: Optimism (OP Mainnet), Base, Linea, Scroll, Starknet, Mantle, Polygon zkEVM, Mode, Blast, and Taiko. Official network documentation, maintained official repositories, and official status notices were preferred. Third-party sources were used only as corroboration, never as sole evidence for VERIFIED status.

All timestamps below are UTC. Unknown values remain UNKNOWN. Main TXT includes only VERIFIED public production networks.

## Results and counts

- Networks/candidates examined in this batch: 14 (4 pre-existing records re-audited + 10 Ethereum L2 candidates)
- Networks/candidates identified and recorded: 14
- VERIFIED records: 10
- PROVISIONAL records: 2
- CONFLICT records: 0
- MISSING records: 1
- DEPRECATED records: 1
- Records in `data/01_chains.txt`: 10
- Official sources in registry: 19
- Non-official / independent sources in registry: 2
- Total source registry entries: 21

Status arithmetic: 10 + 2 + 0 + 1 + 1 = 14.

## New candidates recorded

### VERIFIED and included in TXT
- Base — chain ID 8453; ETH gas; official Base docs identify Basescan.
- Linea — chain ID 59144; ETH gas; official Linea docs identify Lineascan.
- Mantle — chain ID 5000; MNT currency; official Mantle repository and network materials.
- Mode — chain ID 34443; ETH gas; official Mode docs.
- OP Mainnet — chain ID 10; ETH gas; official Optimism Superchain Registry and OP Stack architecture docs.
- Scroll — chain ID 534352; ETH gas; official Scroll docs identify Scrollscan and zkEVM compatibility.

### Not promoted to TXT
- Blast — PROVISIONAL. Chain ID 81457 and ETH are corroborated by independent infrastructure/integration documentation, but Blast's own docs could not be retrieved in this pass. Need direct first-party confirmation of current mainnet status, network architecture, and canonical explorer.
- Taiko — PROVISIONAL. Taiko Labs launch announcement reports mainnet launch, chain ID 167000 and explorer, but current official network parameter docs could not be retrieved. Need first-party verification of native fee asset and current status.
- Starknet — MISSING. Candidate was checked, but its official documentation page could not be retrieved/inspected during this batch; no unsupported network parameters were filled.
- Polygon zkEVM — DEPRECATED. Polygon's official sunset notice says the Mainnet Beta sequencer sunset completed on 2026-07-03 and the network no longer produces blocks. Deliberately excluded from TXT.

## Existing records audited / amended

- Arbitrum One: changed `chain_symbol` from UNKNOWN to ETH. Official Arbitrum FAQ and developer troubleshooting docs explicitly state ETH is the gas/native currency on Arbitrum One. Retained chain ID 42161 and Nitro rollup identity.
- Celestia: changed `chain_symbol` from UNKNOWN to TIA. Official docs establish TIA as the native asset and denomination for PayForBlobs. Recorded Cosmos SDK proof-of-stake architecture; VM remains UNKNOWN because a general-purpose execution VM is not established by reviewed docs. Added Celenium as an explorer explicitly listed by Celestia docs, with a note that it is community-operated rather than a Celestia-operated explorer. Mainnet Beta's experimental warning is preserved verbatim in substance.
- Solana: reaffirmed SOL as the fee asset from official fee docs; retained cluster identity rather than inventing an EVM chain ID.
- ZKsync Era: rechecked official Mainnet chain ID 324, ETH currency and explorer; Sepolia chain ID 300 remains clearly separate.

## Sources and evidence highlights

Official sources (19):
- Arbitrum gas asset: https://docs.arbitrum.io/get-started/faq and https://docs.arbitrum.io/build-decentralized-apps/troubleshooting-building
- Celestia TIA and DA fee mechanics: https://docs.celestia.org/learn/TIA/overview/ and https://docs.celestia.org/learn/TIA/paying-for-blobspace/
- Celestia Mainnet Beta status, experimental caveat and explorer directory: https://docs.celestia.org/operate/networks/mainnet-beta/
- Solana fees: https://solana.com/docs/core/fees
- OP Mainnet configuration: https://github.com/ethereum-optimism/superchain-registry/blob/main/superchain/configs/mainnet/op.toml
- OP Stack architecture: https://docs.optimism.io/op-stack/architecture
- Base: https://docs.base.org/get-started/connect-to-base
- Linea: https://docs.linea.build/get-started/build/network-info/
- Scroll: https://docs.scroll.io/en/developers
- Mantle: https://github.com/mantlenetworkio/mantle
- Mode: https://docs.mode.network/user-guides/network-details
- Polygon sunset: https://polygon.technology/polygon-zkevm and https://support.polygon.technology/support/solutions/articles/82000927750-recovering-funds-from-polygon-zkevm-the-claims-interface
- Taiko Labs announcement: https://paragraph.com/@taiko-labs/taiko-is-live-on-ethereum-mainnet

Independent corroboration (2):
- Blast network support details: https://thegraph.com/docs/en/supported-networks/blast/
- Blast gas asset / chain ID corroboration: https://docs.chain.link/resources/link-token-contracts?parent=chainlinkFunctions

The four previously registered official source entries remain in the registry; the count of 19 official entries includes those four plus new first-party sources. Taiko's announcement is attributed to Taiko Labs but hosted on Paragraph; it is conservatively assigned medium reliability and does not independently close the current-docs gap.

## Exclusions and classifications

- Testnet: Base Sepolia (84532), Linea Sepolia (59141), ZKsync Era Sepolia (300), Mode Sepolia (919), Scroll Sepolia (534351), and Arbitrum Sepolia are test environments, not separate production entries; excluded from TXT.
- Deprecated: Polygon zkEVM Mainnet Beta; sequencer sunset 2026-07-03; excluded from TXT and recorded DEPRECATED.
- Private: no private network was added to the primary inventory in this batch. Private RPC endpoints mentioned in documentation are infrastructure access endpoints, not separate chains.
- Forks/renames: no additional fork or renamed network was established in this batch.
- Not sufficiently verified: Blast and Taiko remain PROVISIONAL; Starknet remains MISSING; all excluded from TXT.

## Unresolved issues

1. Blast: retrieve first-party Blast network docs and independently verify chain ID, gas asset, architecture, status and explorer.
2. Taiko: retrieve accessible official network configuration docs and verify native fee token and active production state.
3. Starknet: obtain accessible first-party network reference and verify mainnet status, chain ID, fee currencies, VM/runtime and explorer.
4. Celestia: VM/general-purpose execution semantics remain UNKNOWN; current explorer is community-operated and listed by official docs, not an official Celestia-operated explorer.
5. Broader inventory: the L2 sample is not exhaustive. Continue discovery of additional OP Stack chains, ZK rollups, validiums, app-specific rollups and other Ethereum L2s; then cover EVM L1, other L1, Cosmos/IBC, Substrate, sidechains, appchains/subnets, private networks and deprecated chains.
6. Revisit all records for duplicate identities and current operational status in the final audit.

## Coverage assessment

This batch materially extends the Ethereum L2 sample, but does not complete Ethereum L2 discovery or Phase 1. Six additional L2 candidates are VERIFIED and included. Two remain provisional, one is missing evidence, and one is deprecated. The overall network universe remains open-ended and coverage is still partial.

## Exact handoff / next action

Resume at `agents/agent_01_chains/handoff.md`: first close the evidence gaps for Blast, Taiko and Starknet using accessible first-party documentation; then continue systematic Ethereum L2 discovery beyond the ten candidates in this batch. Do not begin EVM L1 until the L2 candidate matrix has been expanded and deduplicated. Continue updating all seven required outputs at each coherent checkpoint. Overall status remains IN_PROGRESS.
