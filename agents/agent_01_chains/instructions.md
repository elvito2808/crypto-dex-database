# AGENT-01 — CHAIN DISCOVERY

Task ID: `AGENT-01-CHAIN-DISCOVERY`
Repository: `elvito2808/crypto-dex-database`
Priority: Critical — this is the first research phase.

## Mission

Build a broad, evidence-backed inventory of blockchain networks that may host tokens and decentralized exchanges. Aim for comprehensive coverage, but never claim a mathematically complete list of every network in existence. Document scope and limitations.

## Scope

Research public production networks across:
- Layer 1 networks.
- Layer 2 networks and rollups (optimistic, ZK, validium and other designs).
- Sidechains.
- Appchains and application-specific networks.
- Subnets and independently operated ecosystem networks.
- Cosmos SDK / IBC networks.
- Substrate-based networks.
- EVM-compatible networks.
- Non-EVM networks and other independent architectures.

Also identify and classify separately:
- Testnets and devnets.
- Private or permissioned networks.
- Forks and renamed/derived networks.
- Deprecated, sunset, paused, or apparently inactive networks.

Do not mix these categories into the primary mainnet list.

## Main-list inclusion rule

A record may enter `data/01_chains.txt` only if:
1. It is a distinct public production network (not merely a token, app, RPC endpoint, explorer, or testnet).
2. Its canonical identity can be distinguished from similarly named networks.
3. Its mainnet existence and status have credible evidence.
4. The record status is `VERIFIED`.

Put uncertain candidates in metadata with `PROVISIONAL`, `CONFLICT`, or `MISSING`; do not promote them to the TXT file until resolved.

## Required fields

For every candidate, research:
- canonical name and common symbol (if any);
- network type;
- architecture and VM/runtime;
- ecosystem and parent/settlement/security chain, if applicable;
- mainnet status;
- chain ID where applicable;
- another canonical network identifier where available;
- official website;
- official documentation;
- official explorer;
- verification status;
- last checked UTC timestamp;
- direct evidence URLs;
- notes, aliases, caveats, and conflicts.

Do not invent identifiers or fill gaps from assumptions. Use `UNKNOWN`.

## Required outputs

1. `data/01_chains.txt`
   - One canonical name per line.
   - Only VERIFIED public production networks.
   - No duplicates; sort alphabetically (English).
2. `data/01_chains_metadata.csv`
   - Header:
`chain_name,chain_symbol,chain_type,architecture,vm,ecosystem,parent_chain,mainnet_status,chain_id,network_identifier,official_website,official_docs,official_explorer,status,last_checked_utc,source_urls,notes`
3. `reports/research_reports/agent_01_chain_discovery.md`
   - Methodology, categories covered, sources, counts by status, unresolved issues, exclusions, limitations, and coverage assessment.
4. `agents/agent_01_chains/progress.md`
   - Completed categories, remaining categories, record counts, saved files, blockers, and checkpoint timestamp.
5. `agents/agent_01_chains/handoff.md`
   - Exact resume point, unfinished work, unresolved conflicts, files, and next steps for the next agent.
6. `sources/source_registry.csv`
   - Header:
`source_id,source_name,source_url,source_type,related_chain,access_date_utc,reliability,notes`

## Source rules

Prefer official network sites, docs, repositories, explorers, governance announcements, and maintained technical registries. Aggregators may help discover candidates but are not sufficient as the only evidence for VERIFIED status.

For each important claim, record the direct source URL. Cross-check ambiguous identity/status claims. Preserve conflicting evidence and explain it.

## Status values

Use exactly one:
- `VERIFIED`
- `PROVISIONAL`
- `CONFLICT`
- `MISSING`
- `DEPRECATED`

## Research workflow

1. Read `README.md`, `PROJECT_STATUS.md`, `MASTER_TASKS.md`, `docs/research_methodology.md`, and `docs/data_dictionary.md`.
2. Build candidate lists by ecosystem and network architecture, not by one aggregator alone.
3. Verify each candidate and deduplicate using canonical identifiers and official evidence.
4. Save a checkpoint after each coherent batch; do not wait until the whole research task is complete.
5. Update the TXT, CSV, source registry, report, progress, and handoff consistently.
6. Before handoff, reconcile counts across all outputs.

## Checkpoint and time-limit protocol

At every checkpoint:
- commit/save the batch of data;
- update `progress.md` and `handoff.md`;
- record the exact last completed category and next candidate/category;
- list sources already reviewed and sources still to inspect;
- state any partial or unverified data explicitly.

If time, token, or execution limits are approaching, STOP new research and save the current state first. Never report unsaved work as complete.

## Completion criteria

The task is ready for manager review only when all six outputs exist, source URLs are traceable, primary TXT contains only VERIFIED mainnets, duplicates have been reviewed, and unresolved issues are explicitly listed.

Final response must include:
- total candidates;
- counts by status;
- number of VERIFIED mainnets in TXT;
- files created/updated;
- remaining issues;
- latest checkpoint and exact resume point.

Quality over raw record count. Do not fabricate completeness.


## Permanent amendment — public Mainnet scope and retrieval-error protocol

Effective immediately for every subsequent batch:

1. The primary `data/01_chains.txt` is exclusively a list of distinct, public, operational Mainnet networks with `VERIFIED` status. Never include testnets, devnets, private/permissioned networks, experimental environments, deprecated/sunset networks, or candidates whose Mainnet existence/current operation is not sufficiently evidenced. Do not create unnecessary side lists for test/private environments.
2. On any retrieval failure (HTTP error of any status, timeout, DNS/SSL, inaccessible docs/API/site/repository, or file read/load failure), do not retry that same source. Record one row per independent failure in `reports/research_reports/agent_01_retrieval_issues.csv` with the exact URL/location, UTC detection time, error, affected fields, verification impact and action. Never guess URLs, status codes or error details.
3. Retrieval failures are not evidence conflicts. Log failures only in the retrieval-issues file. For unresolved contradictions between credible sources, preserve both claims and use `CONFLICT`. Where a failed retrieval leaves a field unverified, set the field to `UNKNOWN`; do not infer it from third-party corroboration. Use `PROVISIONAL` or `MISSING` where evidence is insufficient, and `VERIFIED` only where all required claims are supported.
4. Do not repeat an external retrieval to validate storage. After committing, re-read changed repository files from GitHub only; this is a storage-integrity check, not permission to retry failed external sources.
5. Synchronize TXT, metadata, source registry, candidate matrix, retrieval issue log, report, progress, handoff and project status. Once finalization is authorized and counts reconcile, mark the Agent 01 task `COMPLETED`; the overall project may remain `IN_PROGRESS` while later phases are pending.


## Finalization amendment — AGENT-01 closed

The AGENT-01 chain-discovery task is finalized and its task status is `COMPLETED`. Do not conduct further discovery, source retries, evidence closure or repeated checks for unresolved AGENT-01 candidates. Preserve every unresolved retrieval failure, evidence gap, UNKNOWN field, PROVISIONAL record, CONFLICT and deprecated-record caveat in `reports/research_reports/agent_01_retrieval_issues.csv` for final project review. Retrieval failures and evidence conflicts remain distinct classifications. Only VERIFIED public operational Mainnets may appear in `data/01_chains.txt`; retain the current 18 entries and the existing network statuses. The next project phase is native-token, wrapped-token and stablecoin discovery for the 18 verified networks. Unresolved AGENT-01 items are archived for final project review and are not immediate tasks for the next agent.
