# Agent 01 — Chain Discovery Research Report

- Task: AGENT-01-CHAIN-DISCOVERY
- Checkpoint: 2026-11-09T23:46:00Z
- Scope status: Initial evidence-backed batch; research is not complete.

## Methodology
Reviewed the repository README, project status, master task plan, research methodology, data dictionary, and Agent 01 instructions before discovery. Candidate discovery was performed by architecture/ecosystem and checked against official network documentation. Aggregator listings were treated as leads only. Main-list records were included only where official documentation supports distinct public production identity and mainnet status. Unknown fields remain UNKNOWN.

## Categories covered
- Ethereum L2 / rollups: Arbitrum One; ZKsync Era.
- Non-EVM L1 / modular networks: Solana; Celestia.
- All other categories remain open and have not been comprehensively surveyed.

## Counts at this checkpoint
- Total candidates recorded: 4
- VERIFIED: 4
- PROVISIONAL: 0
- CONFLICT: 0
- MISSING: 0
- DEPRECATED: 0
- VERIFIED public production networks in `data/01_chains.txt`: 4
- Source registry entries: 4

## Verified records and evidence
| Network | Classification | Key evidence |
|---|---|---|
| Arbitrum One | Ethereum L2, Nitro optimistic rollup | [Official chain information](https://docs.arbitrum.io/chain-info) states chain ID 42161, Ethereum as underlying chain, Nitro Rollup, and explorer. |
| Celestia | L1 / data-availability network | [Official Mainnet Beta docs](https://docs.celestia.org/operate/networks/mainnet-beta/) state chain ID `celestia`, genesis hash, and describe a live, stable Mainnet Beta while noting experimental status. |
| Solana | Non-EVM L1 | [Official cluster docs](https://solana.com/docs/references/clusters) identify Mainnet as a permissionless, persistent cluster and distinguish testnet/devnet. |
| ZKsync Era | Ethereum L2, ZK rollup | [Official network details](https://docs.zksync.io/zksync-network/zksync-era/network-details) state Mainnet chain ID 324 and distinguish Sepolia testnet chain ID 300. |

## Unresolved issues and limitations
- This is a small initial batch, not a comprehensive chain census.
- Celestia documentation explicitly describes Mainnet Beta as experimental; its live production identity is documented, but operational-risk caveats should remain visible.
- Celestia official explorer and VM/runtime were not established from the source reviewed and remain UNKNOWN.
- Solana does not use an EVM chain ID; no chain ID was invented. Its mainnet cluster identity is recorded instead.
- Native symbols, runtime/architecture details, official explorers, and parent/security relationships need further verification where marked UNKNOWN or where the evidence base is thin.
- No testnet, private, permissioned, or deprecated candidates have yet been catalogued; absence from this batch is not evidence of absence.

## Coverage assessment
Low coverage / early-stage. Two categories received initial sampling; all other EVM L1, non-EVM L1, rollup, sidechain, Cosmos/IBC, Substrate, appchain/subnet, private/test, and deprecated-network categories require further discovery. The four records are evidence-backed initial entries, not a claim of ecosystem completeness.

## Exact continuation point
Continue Ethereum L2 / rollup discovery beyond Arbitrum One and ZKsync Era, cross-check each candidate against its own official documentation, then move to EVM L1 networks. Expand the candidate matrix to Cosmos/IBC, Substrate, sidechains, appchains/subnets, other non-EVM architectures, and separately classified test/private/deprecated networks. Reconcile duplicate identities and identifiers before promotion.
