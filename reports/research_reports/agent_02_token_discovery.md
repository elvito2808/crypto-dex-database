# Agent 02 — Native Tokens, Wrapped Tokens & Stablecoins Discovery

**Task:** `AGENT-02-TOKEN-DISCOVERY`  
**Status:** `COMPLETED`  
**Last checked:** 2026-11-10T15:50:00Z  
**Repository:** https://github.com/elvito2808/crypto-dex-database

## Executive summary

The task covered all 18 canonical public production Mainnets read directly from `data/01_chains.txt`. The deliverable separates native balances, network gas/fee denomination, contract-backed protocol-fee tokens, wrapped/bridged assets, and stablecoins issued natively or represented through bridges.

The saved inventory contains 30 chain-token records and 30 stablecoin deployment records. It includes 32 documented open evidence gaps, UNKNOWN fields and inventory limitations. No Agent 02 retrieval error was observed. The absence of a stablecoin or wrapped-token row for a chain does **not** prove that no such tokens exist there.

This is a curated, evidence-backed inventory and not a complete on-chain enumeration of every contract, live supply/solvency audit, or liquidity audit. Records may be `VERIFIED` for the documented fields while active market liquidity remains untested.

## Scope

The only target names were:
- Abstract
- Arbitrum Nova
- Arbitrum One
- Base
- Celestia
- Fraxtal
- Ink
- Linea
- Mode
- OP Mainnet
- Scroll
- Solana
- Soneium
- Starknet
- Taiko
- Unichain
- Zircuit
- ZKsync Era

No other chain, testnet, devnet, private network or Agent 01 candidate was added. Blast and Mantle were not investigated. The previous Agent 01 failed URLs were not requested again. Agent 01's retrieval issue CSV was left untouched.

## Method and evidence

1. Read repository file structure, `data/01_chains.txt`, existing `docs/data_dictionary.md`, source registry, Agent 01 progress and project-management documents before setting the schemas.
2. Preferred network docs for native network/gas attributes; issuer docs for token origin/backing and supported networks; maintained bridge/token registries for exact chain-specific contracts; independent sources only for clearly labeled cross-checks.
3. Recorded each contract/mint as a distinct chain-scoped deployment. Matching names or tickers were never treated as proof of identical assets.
4. Native assets without contracts use `NATIVE_NO_CONTRACT`; native SOL uses `NATIVE_NO_MINT`.
5. Unknown issuer, origin chain, bridge route, decimals, fee use or incomplete chain-wide token coverage are explicitly marked `UNKNOWN` and/or `PROVISIONAL`, and are listed in the issue register.
6. Appended 18 additional sources to the existing 72-row source registry, bringing the total to 90.
7. No live RPC calls, token balance reads, contract bytecode checks, total-supply checks or liquidity screens were performed. Deployment evidence is not interpreted as proof of liquidity or redeemability.

## Native assets versus fee assets

For 14 EVM chains (Abstract, Arbitrum Nova, Arbitrum One, Base, Ink, Linea, Mode, OP Mainnet, Scroll, Soneium, Taiko, Unichain, Zircuit and ZKsync Era), ETH is documented as both the native chain balance and the gas/transaction-fee denomination. It is recorded as `NATIVE_NO_CONTRACT`, 18 decimals.

Other networks:
- **Celestia:** TIA is the native asset and pays protocol transaction and blobspace fees. The display unit is TIA; the Cosmos SDK base denomination is utia (6 decimals).
- **Fraxtal:** FRAX is the actual native monetary asset and gas token. Current Frax docs describe FRAX as a commodity asset, not a USD stablecoin. frxUSD is recorded separately as the USD stablecoin.
- **Solana:** SOL is the native lamport asset and transaction-fee currency; it has no SPL mint. Wrapped SOL is a distinct token and is not substituted for SOL.
- **Starknet:** STRK is a contract-backed protocol fee token, not a native coin. ETH is a separate Ethereum-origin bridged token contract on Starknet. Current fee docs establish STRK-denominated resource bounds; whether ETH is also accepted for fees under the present protocol configuration remains unresolved.

## Wrapped and bridged tokens

The token CSV includes 11 wrapped/bridged examples:
- Fraxtal: WFRAX, frxETH and sfrxETH.
- Starknet: WBTC, WETH, wstETH and rETH from the maintained Starknet bridge-token registry; ETH is separately represented as a potential fee asset.
- Mode: WETH and WBTC are listed by the official Mode token-address catalogue. Provenance and/or decimals are incomplete, so these rows are PROVISIONAL.
- Unichain: WETH and wstETH are listed by Uniswap's official deployment table; issuer/origin/bridge detail is incomplete, so these rows are PROVISIONAL.

The wrapped-token list is not exhaustive. The issue register records where a complete authoritative token registry was not validated.

## Stablecoins

The stablecoin CSV includes 30 chain-specific deployment records:
- Representation field: 14 NATIVE, 11 BRIDGED, 5 UNKNOWN.
- Verification status: 22 VERIFIED and 8 PROVISIONAL; 0 CONFLICT, 0 MISSING and 0 DEPRECATED.

Key identity distinctions:
- **Arbitrum One:** Circle native USDC and canonical bridged USDC.e have different addresses and provenance. USDT0 is a separate LayerZero OFT deployment.
- **Base, Ink, Linea, OP Mainnet, Starknet, Unichain and Solana:** Circle documents native USDC deployments. Linea's previous Circle Bridged USDC Standard contract was upgraded to native USDC; it is not double-counted as a separate live address. Starknet retains a separate legacy USDC.e bridge deployment.
- **Ink, OP Mainnet, Arbitrum One and Unichain:** USDT0 records use the official per-chain LayerZero OFT deployment list and remain distinct from generic USDT / USDC records.
- **Solana:** official Solana docs list USDC, USDT, PYUSD and USDG mints. PayPal/Solana docs provide PYUSD's Paxos issuer, backing and six decimals. USDG's decimals were not present in the official page and remain UNKNOWN.
- **Starknet:** the maintained official bridge token registry lists bridged USDT, DAI and LUSD in addition to USDC.e. Native Circle USDC is a different contract.
- **Fraxtal:** frxUSD is recorded as the USD-pegged, cash-equivalent/tokenized-US-Treasury-backed fiat-redeemable stablecoin. sfrxUSD is labeled as a yield-bearing receipt wrapper, not a separate issuer.
- **Mode:** official Mode token docs list USDC, USDT and DAI contract addresses, but do not establish exact issuer, backing, source chain, bridge method or decimals. These entries are PROVISIONAL.
- **Unichain:** USDS and sUSDS occur in the official Uniswap contract catalogue, but the catalogue does not prove exact issuer, provenance, decimals or activity. These entries remain PROVISIONAL.
- **ZKsync Era:** Circle confirms both native USDC and a separate bridged USDC.e form, but the accessible Circle page masks full addresses. Full addresses were cross-checked independently, so both records remain PROVISIONAL pending direct first-party address confirmation.

No stablecoin deployment was authoritatively catalogued in this pass for **Abstract, Arbitrum Nova, Celestia, Scroll, Soneium, Taiko or Zircuit**. These seven coverage gaps are explicitly logged; the dataset does not claim that those chains have no stablecoins.

## Counts

### `data/02_chain_tokens.csv`

| Measure | Count |
|---|---:|
| Native chain assets (`is_native_chain_asset=TRUE`) | 17 |
| Contract-backed protocol fee token (STRK on Starknet) | 1 |
| Separate bridged ETH fee-candidate record on Starknet | 1 |
| Wrapped/Bridged examples | 11 |
| **Total chain-token records** | **30** |

The Starknet ETH row (`CT-STARKNET-ETH-BRIDGED`) is a separate Ethereum-origin bridged token contract. It is not the native Starknet asset and must not be merged with STRK or with any native-asset record. Its current acceptance for paying Gas is `UNKNOWN`; it is recorded as a separate bridged ETH fee-candidate record. STRK remains the distinct contract-backed protocol fee token.

| Verification status | Count |
|---|---:|
| VERIFIED | 26 |
| PROVISIONAL | 4 |
| CONFLICT | 0 |
| MISSING | 0 |
| DEPRECATED | 0 |

### `data/03_stablecoins.csv`

| Measure | Count |
|---|---:|
| Stablecoin deployment rows (includes yield-bearing wrappers explicitly labeled) | 30 |
| NATIVE representation | 14 |
| BRIDGED representation | 11 |
| UNKNOWN representation | 5 |
| VERIFIED | 22 |
| PROVISIONAL | 8 |
| CONFLICT / MISSING / DEPRECATED | 0 / 0 / 0 |

### Sources and unresolved matters

- Source registry: 90 rows total (72 existing + 18 newly added).
- Agent 02 retrieval errors: 0.
- Unresolved UNKNOWN/evidence/inventory issues: 32 rows.
- Token conflicts identified: 0. Missing/deprecated token rows: 0.
- Agent 01 retrieval issue CSV: unchanged.

## Output files created

- `data/02_chain_tokens.csv`
- `data/03_stablecoins.csv`
- `reports/research_reports/agent_02_token_discovery.md`
- `reports/research_reports/agent_02_retrieval_issues.csv`
- `agents/agent_02_tokens/instructions.md`
- `agents/agent_02_tokens/progress.md`
- `agents/agent_02_tokens/handoff.md`

## Output files updated

- `sources/source_registry.csv`
- `docs/data_dictionary.md`
- `agents/agent_01_chains/progress.md` — final status aligned to COMPLETED; no new Agent 01 research.
- `PROJECT_STATUS.md`
- `MASTER_TASKS.md`

`reports/research_reports/agent_01_retrieval_issues.csv` was deliberately not modified.

## Limitations / next action

The 32 issue-register rows document incomplete stablecoin coverage, incomplete wrapped-token registry coverage, unknown issuer/bridge/decimals, and the limited current-fee evidence on Starknet. They are accepted outstanding research items, not reasons to stop or retry the same sources.

**Next phase: Agent 03 — DEX Discovery.** Restrict work to the same 18 chains; register distinct DEX deployments and qualify only observations with 24-hour volume strictly greater than USD 50,000, recording the source/provider and an observation timestamp in UTC for each result.
