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

## Agent 03 — DEX protocol registry

### File: `data/04_dex_registry.csv`

One row per DEX protocol identity. This is the qualified protocol registry only; a protocol is present only if at least one chain-specific deployment has a valid 24h USD volume observation strictly greater than USD 50,000.

| Field | Meaning |
|---|---|
| dex_id | Stable protocol-level ID, shared across the protocol's deployments only where identity evidence supports it. |
| dex_name | Provider/official display name. Do not collapse forks or same-name deployments without identity evidence. |
| website_url / official_docs_url | Official URL or UNKNOWN. |
| protocol_category / protocol_description | Discovery-stage classification; detailed AMM/order-book and fee analysis is out of scope. |
| official_source_urls | Official identity/deployment source URLs separated by semicolons; UNKNOWN if none confirmed. |
| discovery_status | QUALIFIED only for protocols with at least one qualifying chain deployment. |
| notes | Supported chain evidence and explicit identity limitations. |

### File: `data/05_dex_deployments.csv`

One row per qualified DEX deployment on one canonical chain. Protocol identity and deployment identity are different keys.

| Field | Meaning |
|---|---|
| deployment_id | Stable ID for a single DEX + chain deployment. |
| dex_id / dex_name | Parent protocol identity; dex_id refers to `data/04_dex_registry.csv`. |
| chain_name | Must match one of the 18 names in `data/01_chains.txt`. |
| deployment_name | Human-readable DEX + chain label. |
| contract_address / factory_address / router_address | Exact verified identifiers or UNKNOWN; never guess. |
| other_deployment_identifier | Other source-backed deployment identity, not an inferred contract. |
| ui_url / explorer_url | Official UI / chain explorer URL, or UNKNOWN when not evidenced. |
| activity_status | Discovery-stage observation such as ACTIVE_VOLUME_OBSERVED; not a full on-chain audit. |
| verification_status | Evidence confidence for the deployment identity and volume; partial aggregator evidence must remain explicit. |
| source_urls / last_checked_utc / notes | Evidence URLs, UTC agent retrieval time and caveats. |

### File: `data/06_dex_volume_snapshots.csv`

Each row is one independent provider observation. Do not merge snapshots captured at different times.

| Field | Meaning |
|---|---|
| snapshot_id | Unique volume observation ID. |
| deployment_id / dex_id / dex_name / chain_name | The specific chain deployment observed. |
| volume_24h_original / original_currency | Provider display amount and original unit. |
| volume_24h_usd | USD equivalent; same as source amount when original currency is USD. |
| measurement_window | Provider-reported 24h interval and its as-of label; state UNKNOWN if exact UTC boundaries are unavailable. |
| provider / source_url | Named analytics provider and exact chain-filtered source URL. |
| observed_at_utc | Agent retrieval timestamp, not a substitute for the provider's measurement cutoff. |
| volume_status | OBSERVED_24H, BELOW_THRESHOLD, STALE_PROVIDER_SNAPSHOT, CONFLICT, etc. |
| qualification_result | QUALIFIED iff volume_24h_usd > 50000; otherwise BELOW_THRESHOLD. This field is purely the numeric comparison, not a freshness or deployment-identity assertion. |
| notes | Display rounding, source freshness, conflict, and cutoff limitations. |

### Agent 03 candidates and issue log

- `agent_03_dex_candidates.csv` keeps every non-qualified, stale, conflicting, or unverified candidate and the reason it is not in the main protocol registry.
- `agent_03_retrieval_issues.csv` records retrieval errors, volume gaps, aggregate-only data, source conflicts, UNKNOWN identifiers and below-threshold exclusions.
- Controlled candidate statuses: QUALIFIED, BELOW_THRESHOLD, UNVERIFIED_VOLUME, UNKNOWN, INACTIVE, CONFLICT.
- The strict threshold is **> USD 50,000**. USD 50,000 is not eligible.
- A provider's chain aggregate is never allocated to a DEX protocol without deployment-specific evidence.
- A dated historical snapshot can compare above the threshold numerically, but it does not establish current eligibility for the main registry.


## Agent 04 — DEX technical details

### File: `data/07_dex_technical_details.csv`
One row per existing deployment. Fields: stable `technical_record_id`; protocol/deployment keys; canonical chain and chain identifier; Native Gas Token, type and validation; contract, factory, router, pool/pair and alternate technical identifiers with independent statuses; official UI and explorer URL with independent statuses; implementation notes; evidence URLs; UTC observation time; overall record status.

### File: `data/08_dex_fee_mechanics.csv`
Six rows per deployment, keyed by `fee_record_id`. Controlled `fee_type` values: `SWAP_TRADING_FEE`, `LIQUIDITY_PROVIDER_FEE`, `PROTOCOL_FEE`, `AGGREGATOR_FEE`, `NETWORK_GAS_FEE`, `BUILDER_SOLVER_FEE`. Each row captures existence, exact rate/formula, payer, recipient, stage, required/optional/conditional status, fee payment asset, alternative payment assets, deployment/pool variance, source URLs, UTC observation timestamp, validation status and notes. Native Gas Token is not a substitute for DEX Fee Payment Token.

### Agent 04 issue log
File: `reports/research_reports/agent_04_retrieval_issues.csv`. Fields: `issue_id,dex_id,deployment_id,protocol_name,chain_name,affected_fields,status,source_url_or_location,issue_type,details,impact_on_data_validity,recorded_at_utc,next_action`. `OPEN_DEFERRED_PHASE6` records accepted unresolved evidence gaps for Phase 6; it does not authorize unlimited retries.


## Agent 05 schema reconciliation — source CSV fields

Audit date: 2026-11-10 UTC. The Agent 05 comparison identified actual CSV fields not previously defined above. These descriptions supplement the source schemas; names and source values are unchanged.

| Field | Meaning |
|---|---|
| `asset_name` | Human-readable asset name; identity still depends on network and contract or mint context. |
| `symbol` | Ticker or symbol as recorded; not a unique identifier. |
| `origin_chain` | Origin network for a wrapped or bridged representation; UNKNOWN where not established. |
| `origin_asset` | Origin asset identity or reference ticker/contract, verbatim from source. |
| `issuer_or_bridge` | Issuer, bridge operator, or bridging protocol associated with the representation. |
| `bridge_mechanism` | Documented mechanism for the wrapped or bridged representation; UNKNOWN if not sourced. |
| `stablecoin_name` | Human-readable name of the stablecoin deployment. |
| `website_url` | Official project or protocol website URL. |
| `protocol_category` | Protocol-level DEX category or implementation family. |
| `protocol_description` | Short protocol-identity description, not a chain-specific deployment assertion. |
| `official_docs_url` | Official protocol documentation entry URL. |
| `contract_address` | Deployment-specific contract address, where directly supported. |
| `factory_address` | Factory contract address, where directly supported. |
| `router_address` | Router contract address, where directly supported. |
| `ui_url` | Deployment-specific user interface URL. |
| `explorer_url` | Explorer URL relevant to the chain or DEX deployment. |
| `volume_24h_original` | 24-hour volume in the provider's original denomination. |
| `original_currency` | Currency or denomination for volume_24h_original. |
| `provider` | Analytics provider that supplied the volume observation. |
| `source_url` | Direct evidence URL for the observation or claim. |
| `technical_record_id` | Unique Agent 04 technical-detail row identifier. |
| `chain_id_or_network_identifier` | Network-specific numeric or textual identifier as sourced. |
| `chain_id_status` | Evidence status for the network identifier. |
| `native_gas_token` | Native or protocol gas-denomination token; not automatically a DEX fee-payment asset. |
| `native_gas_token_type` | Classification of the gas token, such as native coin or contract-backed fee token. |
| `native_gas_token_status` | Evidence status for native_gas_token and its type. |
| `contract_role` | Role of the recorded contract in the DEX deployment. |
| `contract_address_status` | Evidence status for contract_address. |
| `factory_address_status` | Evidence status for factory_address. |
| `router_address_status` | Evidence status for router_address. |
| `pool_or_pair_contract` | Pool/pair contract or canonical program/state identifier, if specifically evidenced. |
| `pool_or_pair_status` | Evidence status for pool_or_pair_contract. |
| `other_technical_identifiers` | Additional program IDs, managers, core contracts, or related identifiers. |
| `other_identifiers_status` | Evidence status for other_technical_identifiers. |
| `ui_url_status` | Evidence status for ui_url. |
| `explorer_url_status` | Evidence status for explorer_url. |
| `technical_mechanics` | Relevant technical behavior or deployment mechanics. |
| `evidence_source_urls` | Semicolon-separated evidence URLs supporting technical details. |
| `record_status` | Overall technical-row status; does not override field-level statuses. |
| `fee_record_id` | Unique fee-mechanics row identifier. |
| `fee_type` | One of the six separate fee categories recorded by Agent 04. |
| `fee_exists` | Whether evidence establishes this fee category; UNKNOWN is not equivalent to NO. |
| `rate_or_formula` | Documented rate or calculation formula; UNKNOWN where unsupported. |
| `payer` | Party economically or mechanically paying the fee, if evidenced. |
| `recipient` | Fee recipient or beneficiary, if evidenced. |
| `calculation_or_deduction_stage` | Stage where the fee is calculated, deducted, or settled. |
| `mandatory_optional_or_conditional` | Whether the fee is general, optional, or conditional. |
| `fee_payment_asset` | Asset actually used to pay/deduct this fee, if evidenced; distinct from gas token. |
| `alternative_fee_payment_assets` | Other evidenced fee-payment assets or explicit UNKNOWN. |
| `deployment_or_pool_variance` | Known deployment, version, or pool variation and caveats. |
| `validation_status` | Evidence status for the fee-mechanics row. |
| `source_id` | Stable local identifier in the Source Registry. |
| `source_name` | Publisher, site, or document label in the Source Registry. |
| `source_type` | Source category recorded by the research process. |
| `related_chain` | Chain context for a source, or UNKNOWN if no single chain is assigned. |
| `access_date_utc` | Recorded UTC time when the source was accessed. |
| `reliability` | Qualitative source reliability assessment; rationale belongs in notes. |
| `candidate_id` | Field retained verbatim from its source dataset; preserve UNKNOWN and PROVISIONAL rather than inferring a value. |
| `candidate_status` | Agent 03 candidate/exclusion classification; not an Agent 05 requalification. |
| `volume_24h_reported` | Provider-reported 24-hour volume as originally captured. |
| `volume_as_of` | Provider-stated observation date/time; may not expose exact UTC window boundaries. |
| `exclusion_reason` | Recorded reason a candidate was not included in the qualified deployment registry. |
| `issue_id` | Original issue identifier within its originating Agent issue log. |
| `detected_at_utc` | UTC detection or formal logging time of an Agent 01 issue. |
| `network_name` | Agent 01 network or candidate name associated with an issue. |
| `exact_location` | Specific source URL, route, page, or location where an issue occurred. |
| `error_type` | Agent 01 retrieval or evidence issue category. |
| `http_status` | Recorded HTTP status for a failed request; blank where not applicable. |
| `error_description` | Recorded retrieval or evidence failure details. |
| `affected_fields` | Fields impacted by the issue. |
| `impact_on_verification` | How the issue limits verification. |
| `action_taken` | Action documented by the originating Agent. |
| `asset_or_record` | Agent 02 asset or record label associated with an issue. |
| `affected_field` | Single Agent 02 field affected, where identified. |
| `source_url_or_location` | Source URL or descriptive source location associated with an issue. |
| `issue_type` | Original issue classification; preserve the exact source label. |
| `details` | Original issue details, including uncertainty and evidence limitations. |
| `recorded_at_utc` | UTC timestamp when the originating Agent issue was recorded. |
| `error_details` | Agent 03 recorded retrieval, volume, or deployment issue details. |
| `protocol_name` | Agent 04 protocol label associated with a technical or fee issue. |
| `impact_on_data_validity` | Agent 04 explanation of the issue's effect on data validity. |
| `next_action` | Agent 04 handoff note; not authority for out-of-scope rediscovery. |

## Agent 05 integrated export

File: `data/final_crypto_dex_database.csv`. One row represents one preserved source record. CHAIN rows contain only the 18 VERIFIED names from `data/01_chains.txt`; excluded chain candidates remain in their Agent 01 source files.

| Field | Meaning |
|---|---|
| `record_type` | Entity or issue type in the integrated export. |
| `record_id` | Deterministic type-prefixed export key; original primary key remains separately available. |
| `source_file` | Repository path of the original source record. |
| `chain_name` | Canonical chain name associated with the row, where applicable. |
| `chain_record_id` | Deterministic `CHAIN:<name>` key for a canonical network. |
| `token_id` | Original chain-token record ID. |
| `stablecoin_record_id` | Original stablecoin record ID. |
| `dex_id` | Original DEX protocol identity ID. |
| `deployment_id` | Original DEX deployment or candidate deployment reference. |
| `snapshot_id` | Original volume snapshot ID. |
| `candidate_id` | Original Agent 03 candidate ID. |
| `technical_record_id` | Original Agent 04 technical-detail ID. |
| `fee_record_id` | Original Agent 04 fee-record ID. |
| `source_id` | Original Source Registry ID. |
| `issue_origin` | Originating Agent issue log. |
| `issue_id` | Original issue ID within its origin. |
| `source_urls` | Original evidence URL string; multiple URLs remain semicolon-separated. |
| `source_ids` | Exact URL matches to Source Registry IDs; duplicate exact matches retain all IDs. |
| `source_link_status` | URL-to-registry mapping outcome; not an HTTP reachability test. |
| `original_status` | Original status/classification from the source record. |
| `consolidated_status` | Agent 05 disposition; retained issues use `OPEN_DEFERRED_FINAL`. |
| `observed_at_utc` | Original observation/access/check timestamp when present. |
| `volume_24h_usd` | Original 24-hour USD volume value, where present. |
| `fee_type` | Original fee category, where applicable. |
| `payload_json` | JSON object with the complete original source row, retaining its columns and values. |

## Agent 05 consolidated issue export

File: `reports/research_reports/agent_05_consolidated_issues.csv`. The export retains origin, source issue ID, source file, original issue fields, original status, and complete `payload_json`. Every unresolved issue is assigned `OPEN_DEFERRED_FINAL`; completion of Phase 6 does not mean issue resolution.