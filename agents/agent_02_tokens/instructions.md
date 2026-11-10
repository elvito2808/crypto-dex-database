# AGENT-02 — Native Tokens, Wrapped Tokens & Stablecoins

**Task ID:** `AGENT-02-TOKEN-DISCOVERY`  
**Priority:** High  
**Status:** `COMPLETED`

## Mission

Identify and document native assets, chain gas/fee assets, important wrapped/bridged tokens, and stablecoins deployed on exactly the 18 canonical public production Mainnets named in `data/01_chains.txt`.

## Mandatory distinctions

- A chain's actual native balance asset is not automatically the gas token or the protocol fee token. Record these as separate attributes.
- Native ETH on EVM chains is not an ERC-20. Use `NATIVE_NO_CONTRACT`; native SOL uses `NATIVE_NO_MINT`.
- A contract-backed token used for protocol fees (for example STRK on Starknet) is not a native coin.
- Every wrapped/bridged token must retain its own chain + address identity, origin chain/asset and bridge/issuer when established.
- Stablecoins with the same symbol may have different issuers, backing models, origins and contracts. Never merge by ticker.
- Native Circle USDC, bridged USDC.e, Tether USDT and USDT0 must remain distinct where their deployment contracts and bridge/issuer semantics differ.
- Yield-bearing stablecoin wrappers are labeled as wrappers, not counted as independent stablecoin issuers.

## Research and evidence policy

1. Use first-party network documentation, issuer documentation and official maintained token/bridge registries first.
2. Use explorers and independent references only to corroborate, not to infer issuer, reserves or native/bridged status.
3. For each record, retain direct source URLs and a UTC check timestamp.
4. Do not guess. Write `UNKNOWN` for unavailable fields and create an issue-register row for each material unknown/evidence gap.
5. Use only the project status vocabulary: `VERIFIED`, `PROVISIONAL`, `CONFLICT`, `MISSING`, `DEPRECATED`.
6. If a source retrieval fails, record the URL, technical error and log timestamp once. Never retry that same failed URL, change route to evade the error, or loop. Distinguish retrieval errors from conflicts and evidence gaps.
7. Do not research or retry Agent 01 unresolved cases. Blast and Mantle are out of this task. Do not modify Agent 01's retrieval issue file.
8. No testnet, devnet, private network or chain outside `data/01_chains.txt` may be added.

## Output schemas

- `data/02_chain_tokens.csv`: one row per native asset or chain-specific contract/mint representation; contains asset identity, role, native/bridged classification, fee role, origin, address, standard, decimals, issuer/bridge, activity, status, sources and UTC timestamp.
- `data/03_stablecoins.csv`: one row per stablecoin deployment/representation; contains peg/backing model, issuer, chain, native/bridged status, origin, address, standard, decimals, mechanism, activity, status, sources and UTC timestamp.
- `reports/research_reports/agent_02_retrieval_issues.csv`: retrieval errors, evidence gaps, field-level UNKNOWNs and incomplete inventory coverage.
- `reports/research_reports/agent_02_token_discovery.md`: method, chain coverage, counts, findings, limitations, sources and next step.
- `sources/source_registry.csv`: append unique, directly used sources as SRC-0000xx records.
- `docs/data_dictionary.md`: canonical schemas, identity rules, sentinels and status conventions.
- `agents/agent_02_tokens/{instructions,progress,handoff}.md`.
- `PROJECT_STATUS.md` and `MASTER_TASKS.md`.

## Quality gates

- All 18 chain names are in scope; no off-scope chain appears in data.
- Record IDs unique; duplicate chain/address pairs reviewed; symbol is not a deduplication key.
- Native, protocol fee, wrapped/bridged and stablecoin categories are separated.
- Every material UNKNOWN, conflict, missing field and inventory limitation is logged.
- CSV UTF-8, RFC-4180 compatible, stable headers and consistent column count.
- Counts and status totals match the CSVs and report.
- After writes, re-read GitHub files and confirm content persistence.
- Complete with documented UNKNOWN/PROVISIONAL entries; do not use uncertainty as a reason to halt or retry endlessly.

## Completion and handoff

Completion means all required artifacts exist, counts reconcile, unresolved items are documented and GitHub read-back is confirmed. The next phase is Agent 03 — DEX Discovery, restricted to the same 18 chains and the project's strict 24-hour volume threshold.
