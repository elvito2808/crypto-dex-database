# Agent 03 — DEX Discovery

**Task:** `AGENT-03-DEX-DISCOVERY`  
**Branch:** `main`  
**Status:** `COMPLETED` (evidence gaps documented; no unresolved issue blocks closure)  
**Checked at:** 2026-11-10T16:49:00Z  
**Qualification rule:** strictly greater than USD 50000 of provider-reported 24h volume on the specific deployment.

## Executive result

- Canonical chain scope: **18 / 18** networks from `data/01_chains.txt`; no other chain was added.
- DefiLlama chain pages attempted: **18**; successful retrievals: **17**; retrieval failures: **1** (Celestia; no retry).
- Qualified protocol registry: **20** distinct DEX protocol identities.
- Qualified deployment registry: **25** chain-specific deployment rows.
- Volume observations retained: **82** distinct snapshots.
- Non-qualified / unresolved candidate rows: **70**.
- Candidate statuses: BELOW_THRESHOLD **46**, UNVERIFIED_VOLUME **21**, UNKNOWN **1**, CONFLICT **2**, INACTIVE **0**.
- Retrieval / evidence issue rows: **118**.
- Qualified means the exact provider-displayed 24h USD amount is > USD 50,000. Values exactly USD 50,000 would fail. No protocol-wide volume is copied to another chain.

## Method and sources

1. Read `data/01_chains.txt` as the sole scope authority. The 18 entries were used verbatim.
2. Used the chain-filtered DefiLlama DEX volume page for each network to discover protocol labels and per-chain 24h volume rows. No global multi-chain protocol total was attributed to an individual deployment.
3. A provider row is qualified only when its own chain-specific USD amount is strictly greater than USD 50,000. The source currency was USD, so no conversion was necessary.
4. Kept each observed row as its own volume snapshot. The provider publishes a calendar as-of date and a 24h label, but the retrieved page does not expose exact UTC start/end instants. `observed_at_utc` is the agent retrieval timestamp; the provider measurement boundary remains explicitly undisclosed.
5. Kept provider display precision. Abbreviated values (for example `$108.11m`) are normalized to USD numbers at the displayed precision; they are not represented as unrounded raw API amounts.
6. Repeated provider display labels across different chains were not automatically merged into one DEX protocol. Shared protocol IDs are used only where official cross-chain documentation supports the identity (Uniswap and PancakeSwap); other repeated labels receive chain-scoped protocol IDs to avoid merging forks or same-name projects without evidence.
6. Consulted official sources for protocol identity / supported-chain context where returned (Uniswap, PancakeSwap, Ekubo, Kyo Finance, Curve, PumpSwap). Contract/factory/router values remain `UNKNOWN` where no authoritative chain-specific identifier was confirmed.

**Primary analytics provider:** DefiLlama chain-filtered DEX pages.  
**Official cross-check sources:** Uniswap deployment directory; PancakeSwap docs; Ekubo docs / interface; Kyo Finance; Curve interface; PumpSwap interface. All URLs are also listed in `sources/source_registry.csv`.

## Canonical chain coverage

| Chain | Discovery result |
|---|---|
| Abstract | Chain-filtered page retrieved; total $41,380; Aborean $30,749 and SakuraSwap $10,631; no qualified DEX. |
| Arbitrum Nova | Page snapshot as of Nov 4 reports $0 total and zero-volume Sushi / Archly; stale; current status unverified. |
| Arbitrum One | Current Nov 10 page: qualified rows Uniswap, Aero, Metric, Fluid, PancakeSwap, WOOFi. |
| Base | Current Nov 10 page: qualified rows Aero, Uniswap, PancakeSwap, Hanji Protocol. |
| Celestia | Provider page retrieval failed once; no retries; chain-wide DEX discovery UNKNOWN. |
| Fraxtal | Nov 5 snapshot: Frax Finance and Curve above threshold; stale, therefore not promoted. |
| Ink | Current Nov 10 page: Uniswap, Aero, Nado qualify; other exposed rows below threshold or missing. |
| Linea | Nov 9 aggregate total $374,380; no chain-specific per-DEX values exposed; candidates unverified. |
| Mode | Nov 9 table: all numeric rows below $50,000; missing rows remain unverified. |
| OP Mainnet | Nov 10 aggregate total $17.85m; protocol rows found only in Oct 17 archive/capture; not current qualification evidence. |
| Scroll | Nov 10 page: Honeypop DEX $396,706 qualifies; all other exposed rows <=$50,000. |
| Solana | Nov 10 page includes Pump, Orca, Raydium, Scorch >$50,000; BisonFi and Meteora show conflicting same-date captures and are withheld. |
| Soneium | Nov 9 page: Kyo Finance $118,839 and Uniswap $52,495 qualify. |
| Starknet | Nov 9 page: Ekubo Protocol $5.96m and Nostra $108,978 qualify; remaining rows below or without numeric volume. |
| Taiko | Nov 9 total $1,146; all numeric protocol rows below threshold; Uniswap row lacks numeric volume. |
| Unichain | Nov 9 page: Uniswap $18.44m qualifies; other numeric rows below threshold. |
| Zircuit | Nov 4 page: Ocelex $0 and total $0; stale; no current volume qualification. |
| ZKsync Era | Nov 9 page: Maverick $304,000 and SyncSwap $292,013 qualify; iZUMi $46,973 below threshold. |

## Registry and deployment interpretation

- `data/04_dex_registry.csv` is intentionally limited to protocols with at least one non-conflicted current chain-specific qualifying observation.
- `data/05_dex_deployments.csv` contains only the qualified deployment rows (25). Every row has a chain-specific deployment ID; no protocol volume was copied across chains.
- Non-qualified, stale, unknown and conflicting deployment candidates are preserved in `agent_03_dex_candidates.csv` and their related evidence / unknowns are in the retrieval issue log.
- Address fields are not guessed. The 25 qualified deployments have `UNKNOWN` contract, factory and router fields until a chain-specific official deployment identifier is obtained. UI URLs are populated only when an official interface was confirmed; otherwise they remain `UNKNOWN`.
- The word `QUALIFIED` in a historical volume snapshot is the arithmetic comparison of that snapshot to USD 50,000. It does **not** mean a stale observation qualified the deployment for the current registry.

## Chain-volume summary (not allocated to protocols)

| Chain | Provider chain aggregate | As-of date | Use |
|---|---:|---|---|
| Abstract | $41,380 | 2026-11-10 | Context only; below threshold at chain aggregate. |
| Arbitrum Nova | $0 | 2026-11-04 | Stale context only. |
| Arbitrum One | $160.8m | 2026-11-10 | Context only; per-DEX rows separately qualified. |
| Base | $1.192b | 2026-11-10 | Context only; per-DEX rows separately qualified. |
| Celestia | UNKNOWN | UNKNOWN | Page retrieval failure. |
| Fraxtal | $314,302 | 2026-11-05 | Stale context only. |
| Ink | $3.56m | 2026-11-10 | Context only; per-DEX rows separately qualified. |
| Linea | $374,380 | 2026-11-09 | Aggregate only; no allocation. |
| Mode | $858.58 | 2026-11-09 | Context only; exposed rows below cutoff. |
| OP Mainnet | $17.85m | 2026-11-10 | Aggregate only; historical per-DEX rows not current evidence. |
| Scroll | $499,452 | 2026-11-10 | Context only; per-DEX rows separately qualified. |
| Solana | $1.105b / $1.259b | 2026-11-10 | Two same-date provider captures disagree at aggregate level; kept separate in issue log. |
| Soneium | $193,770 | 2026-11-09 | Context only; per-DEX rows separately qualified. |
| Starknet | $6.07m | 2026-11-09 | Context only; per-DEX rows separately qualified. |
| Taiko | $1,146 | 2026-11-09 | Context only; exposed rows below cutoff. |
| Unichain | $18.45m | 2026-11-09 | Context only; per-DEX rows separately qualified. |
| Zircuit | $0 | 2026-11-04 | Stale context only. |
| ZKsync Era | $735,223 | 2026-11-09 | Context only; per-DEX rows separately qualified. |

Chain aggregates above are reported as context only. They do not replace chain-specific DEX deployment evidence.

## Important limitations and issues

- **Celestia:** one failed retrieval (Internal Error); no retries were made.
- **Arbitrum Nova, Fraxtal, Zircuit:** only Nov 4 / Nov 5 source snapshots were exposed. Historical amounts are preserved, but do not establish current eligibility.
- **Linea and OP Mainnet:** aggregate volume is visible, but per-protocol chain-level values could not be verified from current accessible page data. OP Mainnet protocol rows are dated Oct 17 and retained as historical/unverified.
- **Solana:** two same-date DefiLlama captures differ for BisonFi ($157.07m vs $103.44m) and Meteora ($130.37m vs $105.31m). All four observations are kept as separate snapshots, each marked `CONFLICT`; both candidates are excluded from the main registry pending precise source-cutoff reconciliation. The chain aggregate also differed between page captures.
- **Provider measurement boundary:** exact UTC window start/end are not visible. The recorded UTC timestamp is the agent's retrieval time, not a claim about the provider's data cutoff.
- **Display precision:** several provider values are abbreviated; their normalized numbers preserve the shown precision.
- **Deployment identity:** contract, factory and router addresses were not guessed. UI URLs are `UNKNOWN` unless confirmed in an official source. These are recorded as explicit issues.
- **Coverage:** aggregator coverage is not an exhaustive chain census. Missing provider rows are not proof that no DEX exists.
- **Activity:** no deployment was labelled `INACTIVE` without direct evidence of shutdown or inactivity; lack of a row is treated as UNKNOWN / UNVERIFIED.

## Counts and final state

| Metric | Count |
|---|---:|
| Canonical chains checked | 18 |
| Qualified DEX protocol identities | 20 |
| Qualified chain deployments | 25 |
| Volume snapshots | 82 |
| Candidate rows | 70 |
| Below threshold candidates | 46 |
| Unverified volume candidates | 21 |
| Unknown candidate / chain-gap rows | 1 |
| Conflict candidates | 2 |
| Inactive candidates | 0 |
| Retrieval failures | 1 |
| Issue log rows | 118 |

Agent 03 is `COMPLETED`. The unresolved details are captured for later verification and do not hold this task open.

## Next phase

**Next Task:** `AGENT-04-DEX-TECHNICAL-DETAILS`

Agent 04 should start from the qualified protocol and deployment registries, verify exact contract/router/factory identifiers and official UIs, and then perform the technical fee/gas-token analysis within its own scope. Do not reopen Agent 01 or Agent 02 work.
