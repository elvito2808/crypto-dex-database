# Agent 04 — DEX Technical Details and Fee Mechanics

**Task:** `AGENT-04-DEX-TECHNICAL-DETAILS`  
**Status:** `COMPLETED`  
**Observed at:** 2026-11-10T18:32:00Z  
**Scope:** fixed Agent 03 inventory only.

## Final result

- Protocol IDs in input registry: 20; unique: 20.
- Qualified deployment IDs in input: 25; unique: 25.
- Canonical chains: 18.
- Technical detail rows: 25 (one per deployment).
- Fee mechanic rows: 150 (six distinct categories per deployment).
- Agent 04 issue rows: 54.
- Source registry rows: 125 (115 prior + 10 Agent 04 records).

## Scope and integrity

Every deployment's `dex_id` resolves to `data/04_dex_registry.csv`; every deployment chain is in `data/01_chains.txt`. Deployment coverage spans 9 canonical chains: Arbitrum One, Base, Ink, Scroll, Solana, Soneium, Starknet, Unichain, ZKsync Era. No new protocol, DEX, deployment, or network was added.

No Agent 03 registry, deployment, snapshot, candidate, qualification, or discovery issue file was modified. No volume rediscovery, volume snapshot refresh, re-qualification, candidate review, BisonFi/Meteora conflict reconciliation, or prior failed-source retry was performed.

## Technical evidence

`data/07_dex_technical_details.csv` contains field-level statuses:

| Field | Counts |
|---|---|
| chain_id_status | VERIFIED: 25 |
| native_gas_token_status | VERIFIED: 25 |
| contract_address_status | VERIFIED: 6; UNKNOWN: 19 |
| factory_address_status | VERIFIED: 2; UNKNOWN: 21; NOT_APPLICABLE: 2 |
| router_address_status | VERIFIED: 3; UNKNOWN: 22 |
| pool_or_pair_status | VERIFIED: 6; UNKNOWN: 18; PROVISIONAL: 1 |
| other_identifiers_status | PROVISIONAL: 6; UNKNOWN: 17; VERIFIED: 2 |
| ui_url_status | VERIFIED: 10; UNKNOWN: 15 |
| explorer_url_status | VERIFIED: 25 |

Native gas assets reconciled from Agent 01/02:
- Arbitrum One, Base, Ink, Scroll, Soneium, Unichain and ZKsync Era: ETH.
- Solana: SOL.
- Starknet: STRK current fee token. Agent 02 describes this as a contract-backed protocol fee token, not a native balance coin; it is not conflated with a DEX fee token.

Official technical identifiers recorded:
- Uniswap: the official deployment directory lists the v4 PoolManager on Arbitrum One, Base, Ink, Soneium and Unichain. The Arbitrum official v2 directory also lists a V2 Factory and Router02. Other version-specific factory/router fields stay UNKNOWN where the source did not support the exact pair.
- Kyo Finance on Soneium: official contract page lists V2/V3 factories, V2/V3 routers, UniversalRouter, Position Manager and Quot ers. Pair pool addresses are token-pair-specific.
- Ekubo on Starknet: official docs list Core, Positions, Positions NFT and Router V3.0.13. Pools are represented by pool keys/state inside Core.
- Raydium on Solana: official repository lists AMM v4, CPMM, CLMM and Stable AMM program IDs. Since the discovery row does not specify a pool family, program IDs are retained as alternate protocol identifiers and not assigned to a single exact pool path.
- Fluid on Arbitrum One: official DEX V2 contract directory consulted lists Ethereum and Polygon, not Arbitrum. No address from another chain was reused.

All unsupported contract/factory/router/pool values remain UNKNOWN. UI values are populated only when already backed by official project or repository evidence. Explorer links are chain-specific and joined from the canonical network records.

## Fee mechanics

Six distinct fee categories are recorded per deployment:
- `SWAP_TRADING_FEE`: 25
- `LIQUIDITY_PROVIDER_FEE`: 25
- `PROTOCOL_FEE`: 25
- `AGGREGATOR_FEE`: 25
- `NETWORK_GAS_FEE`: 25
- `BUILDER_SOLVER_FEE`: 25

Fee validation counts:
- `PROVISIONAL`: 45
- `UNKNOWN`: 96
- `VERIFIED`: 9

- Uniswap: version-specific V2/V3 fee tiers; current official protocol fee configuration distinguishes LP share and protocol share, with all V2 pools and selected V3 pools active in the current rollout, subject to config. Exact version/route/pool enablement in each provider-labelled deployment remains PROVISIONAL.
- PancakeSwap: official general docs list V2 0.25%, V3 tiers 0.01/0.05/0.25/1%, and pool-specific StableSwap rates. V2 split is 0.17% LP, 0.0225% treasury, 0.0575% CAKE buyback/burn; V3 split varies by tier. Arbitrum/Base pool-version applicability remains PROVISIONAL.
- Ekubo Starknet: pool fee set at pool creation; canonical Positions contract applies 20% of collected position fees as protocol fee on Starknet. Exact pool fee values were not collected; the fee mechanics themselves are VERIFIED.
- Raydium: fee tiers and LP/protocol/fund shares vary across AMM v4, CPMM and CLMM. The exact product family for the registry row is unresolved, so fees are PROVISIONAL.
- Kyo: V2/V3 factories and routers are documented; numerical per-pool fee rate/protocol share are not published in the source used.
- Fluid: DEX V2 docs describe static/dynamic fee logic and a protocol-fee ceiling, but that model was not mapped to the Agent 03 Arbitrum row.
- Aero (three chain-scoped IDs), Metric, WOOFi, Hanji Protocol, Nado, Honeypop DEX, Pump, Orca, Scorch, Nostra, Maverick Protocol and SyncSwap Protocol: no direct deployment-level rate schedule was established in this bounded evidence review; remain UNKNOWN.

Network gas rows are separate from DEX fee rows. ETH/SOL/STRK gas assets are never copied into DEX fee-payment-token fields. CAKE/RAY/EKUBO buyback targets are not assumed to be the token a trader directly pays.

## Issue Log and deferred work

The Agent 04 issue log has 54 rows. All remain `OPEN_DEFERRED_PHASE6`. Issues identify missing technical identifiers/UI, missing numeric schedules, pool version/route ambiguity, protocol-specific configuration gaps and source coverage limitations. These values do not block task closure because they are explicit and traceable.

No open-ended research is authorized. Phase 6 may independently verify only as needed for its own integration scope.
