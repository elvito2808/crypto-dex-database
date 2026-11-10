# Data Dictionary

## Chain metadata

File: `data/01_chains_metadata.csv`

| Field | Meaning |
|---|---|
| chain_name | Canonical public name of the network |
| chain_symbol | Common network/native-asset symbol when applicable; not an identity key |
| chain_type | L1, L2, rollup, sidechain, appchain, subnet, etc. |
| architecture | Consensus/network architecture or ecosystem |
| vm | EVM, WASM, MoveVM, Solana runtime, custom, etc. |
| ecosystem | Parent ecosystem or technology family |
| parent_chain | Parent/settlement/security relationship, if applicable |
| mainnet_status | Active, paused, sunset, unknown, etc. |
| chain_id | Chain ID where applicable; otherwise UNKNOWN |
| network_identifier | Other canonical identifier (genesis hash, network ID, etc.) |
| official_website | Official website |
| official_docs | Official documentation |
| official_explorer | Official explorer |
| status | Project verification status |
| last_checked_utc | UTC date/time of last verification |
| source_urls | Source URLs supporting the record; separate multiple URLs with `;` |
| notes | Caveats, aliases, parent/child details, conflicts |

## Source registry

File: `sources/source_registry.csv`

- `source_id`: stable local identifier (SRC-000001 style).
- `source_name`: publisher/site/document name.
- `source_url`: direct URL.
- `source_type`: official_docs, official_website, explorer, repository, registry, analytics, research, community.
- `related_chain`: canonical chain name or UNKNOWN.
- `access_date_utc`: UTC date/time accessed.
- `reliability`: high, medium, low, or disputed, with rationale in notes.
- `notes`: what the source substantiates and limitations.

## CSV conventions

- UTF-8 encoding; one header row.
- Quote fields containing commas, quotes, or newlines according to RFC 4180.
- Use `UNKNOWN` for unavailable values; do not leave ambiguous blanks.
- Multiple URLs in a field are separated by semicolons.
- Dates/times use ISO 8601 UTC (e.g. `2026-11-09T12:00:00Z`).
- Do not use ticker/symbol as a unique key.

## Agent 02 — chain token inventory

### File: `data/02_chain_tokens.csv`

Each row represents one chain-specific asset deployment or native asset. Ticker is never a unique key. Record IDs use `CT-<CHAIN_SLUG>-<SYMBOL>-<ROLE>`; role suffixes disambiguate native assets, protocol tokens and bridged forms.

| Field | Meaning |
|---|---|
| record_id | Stable unique row ID. |
| asset_name / symbol | Display name and ticker; neither is an identity key. |
| asset_category | Controlled vocabulary: NATIVE_GAS_ASSET, NATIVE_GAS_AND_STAKING_ASSET, NATIVE_GAS_AND_MONETARY_ASSET, PROTOCOL_FEE_TOKEN, BRIDGED_ASSET_AND_POTENTIAL_FEE_ASSET, WRAPPED_OR_BRIDGED_ASSET. Meanings are defined below. |
| chain_name | Must match a canonical chain in `data/01_chains.txt`. |
| native_or_bridged | NATIVE, BRIDGED, WRAPPED or UNKNOWN. |
| is_native_chain_asset | TRUE only for the actual native balance asset; FALSE for a contract/mint token. |
| is_gas_fee_asset | TRUE/FALSE/UNKNOWN according to explicit network/protocol evidence. |
| gas_fee_asset_relationship | SAME_AS_NATIVE_ASSET, PROTOCOL_FEE_TOKEN_NOT_NATIVE_COIN, UNKNOWN_CURRENT_FEE_SUPPORT or NOT_APPLICABLE. |
| origin_chain / origin_asset | Provenance for a bridged/wrapped representation; UNKNOWN where not established. |
| contract_or_mint_address | Exact chain-scoped address. Use NATIVE_NO_CONTRACT for native assets without contracts and NATIVE_NO_MINT for native SOL; never fabricate an address. |
| token_standard | ERC-20, SPL Token, Token-2022, Cosmos SDK bank denomination, native coin, Starknet token contract, etc. |
| decimals | Integer precision or UNKNOWN. |
| issuer_or_bridge / bridge_mechanism | Issuer, bridge, OFT, StarkGate, etc.; UNKNOWN where not established. |
| activity_status | Deployment/listing evidence status; does not assert liquidity or active trading. |
| verification_status | VERIFIED, PROVISIONAL, CONFLICT, MISSING or DEPRECATED. |
| source_urls | Direct support URLs separated by semicolons. |
| last_checked_utc | ISO 8601 UTC timestamp. |
| notes | Caveats, identity distinctions and provenance limitations. |


#### `asset_category` controlled values

| Value | Meaning |
|---|---|
| `NATIVE_GAS_ASSET` | Native chain balance asset used to pay transaction/network gas; no token contract is implied. |
| `NATIVE_GAS_AND_STAKING_ASSET` | Native chain asset used for gas and also for staking, delegation or protocol security. |
| `NATIVE_GAS_AND_MONETARY_ASSET` | Native chain monetary asset that also serves as the network gas/fee denomination. |
| `PROTOCOL_FEE_TOKEN` | Contract-backed or protocol-issued token used to pay protocol execution fees; it is not necessarily the chain's native coin. |
| `BRIDGED_ASSET_AND_POTENTIAL_FEE_ASSET` | Bridged token representation that may be accepted for fees, but current fee eligibility is not conclusively established. |
| `WRAPPED_OR_BRIDGED_ASSET` | Wrapped, bridged or otherwise represented asset deployed as a token contract/mint, rather than the chain's native balance asset. |

### File: `data/03_stablecoins.csv`

Stablecoin entries are keyed by chain + contract/mint, not ticker. Record IDs use `SC-<CHAIN_SLUG>-<SYMBOL>-<ROLE>`.

| Field | Meaning |
|---|---|
| record_id | Stable unique row ID. |
| stablecoin_name / symbol | Display name and ticker; neither is unique. |
| stablecoin_model | Controlled vocabulary: FIAT_BACKED, FIAT_BACKED_UNDERLYING, FIAT_BACKED_TOKENIZED_TREASURY_BACKED, CRYPTO_BACKED, COMMODITY_BACKED, ALGORITHMIC, TOKENIZED_TREASURY_BACKED, YIELD_BEARING_STABLECOIN_WRAPPER, UNKNOWN. Meanings are defined below. |
| peg_or_reference | Peg target or reference asset, if evidenced. |
| issuer | Entity responsible for issuance; UNKNOWN if not established for this deployment. |
| deployment_chain | Canonical chain from `data/01_chains.txt`. |
| native_or_bridged | NATIVE, BRIDGED or UNKNOWN. |
| origin_chain / origin_asset | Source chain and underlying source asset for bridged representations. |
| contract_or_mint_address | Exact token contract/mint on deployment chain. |
| token_standard / decimals | Implementation and decimal precision; UNKNOWN where unsupported. |
| bridge_or_issuer_mechanism | Native issuer/CCTP, canonical bridge, LayerZero OFT, StarkGate, etc. |
| activity_status | Deployment evidence only; token-list entry is not proof of liquidity or redeemability. |
| verification_status | VERIFIED, PROVISIONAL, CONFLICT, MISSING or DEPRECATED. |
| source_urls / last_checked_utc / notes | Direct evidence, UTC audit timestamp and important limitations. |


#### `stablecoin_model` controlled values

| Value | Meaning |
|---|---|
| `FIAT_BACKED` | Stablecoin issued against fiat currency or cash-equivalent reserves and targeting a fiat peg. |
| `FIAT_BACKED_UNDERLYING` | Bridged or represented token whose underlying source asset is a fiat-backed stablecoin; the row describes the representation, not a new issuer. |
| `FIAT_BACKED_TOKENIZED_TREASURY_BACKED` | Fiat-pegged stablecoin backed wholly or partly by tokenized U.S. Treasury instruments or comparable government-debt reserves, as described by its issuer. |
| `CRYPTO_BACKED` | Stablecoin collateralized by cryptoassets, typically with overcollateralization or liquidation mechanisms. |
| `COMMODITY_BACKED` | Token whose target value is linked to a commodity such as gold or another physical commodity. |
| `ALGORITHMIC` | Peg maintained primarily through protocol mechanisms, supply adjustments or market incentives rather than conventional fully reserved collateral. |
| `TOKENIZED_TREASURY_BACKED` | Token representing or backed by tokenized Treasury securities; use when the Treasury exposure is the defining product and a separate fiat-backed classification is not more precise. |
| `YIELD_BEARING_STABLECOIN_WRAPPER` | Receipt, vault or savings wrapper that accrues yield on an underlying stablecoin; not a separate reserve-backed stablecoin issuer. |
| `UNKNOWN` | Available evidence does not establish the stablecoin's backing or mechanism sufficiently for classification. |

The controlled vocabulary is forward-compatible: a value may be defined here before any row uses it. Values actually present in `data/03_stablecoins.csv` must always have an explicit definition.
### File: `reports/research_reports/agent_02_retrieval_issues.csv`

Fields: `issue_id,chain_name,asset_or_record,affected_field,source_url_or_location,issue_type,details,recorded_at_utc,impact_on_verification,status`.

- Retrieval failures (HTTP, DNS, TLS, timeout, API/read errors) are distinct from evidence gaps, unknown fields and incomplete inventory coverage.
- Use the actual event time only when known; otherwise `recorded_at_utc` is the UTC time the issue was logged.
- Every materially unknown issuer, origin, bridge, decimals, fee attribute or scope-coverage gap must have an issue entry.
- `OPEN_DOCUMENTED` means the uncertainty is accepted and recorded; it does not authorize endless retries.

### Agent 02 identity, status and scope rules

- A contract/mint is a chain-specific asset identity. Never merge same-symbol contracts without evidence of same issuer and provenance.
- Native asset, gas/fee denomination and contract-backed protocol-fee token are independent attributes.
- A native EVM gas currency is recorded without an ERC-20 address; native assets use sentinels only where no contract/mint exists.
- A token catalogue alone does not prove issuer, reserves, source chain, bridge mechanism, decimals or live status. Retain UNKNOWN and PROVISIONAL when evidence is incomplete.
- A VERIFIED record confirms only the claims supported by its cited sources; it does not imply exhaustive chain token coverage, liquidity, solvency or active market trading.
- Yield-bearing receipt tokens are labeled as wrappers rather than independent reserve-backed issuers.
- Only the 18 names in `data/01_chains.txt` are in scope. No testnet, devnet, private network or other chain is permitted.
