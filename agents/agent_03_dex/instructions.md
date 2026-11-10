# Agent 03 — DEX Discovery Instructions

**Task ID:** `AGENT-03-DEX-DISCOVERY`  
**Branch:** `main`  
**Status:** `COMPLETED`  
**Canonical scope:** read only `data/01_chains.txt` (18 entries). Never add a chain outside that file.

## Goal

Discover DEX protocols and chain-specific deployments. A deployment qualifies only when a directly attributable provider-reported 24h volume is **strictly greater than USD 50,000**. USD 50,000 exactly does not qualify.

## Evidence rules

- Keep protocol identity separate from each chain deployment.
- Do not attribute multichain/global protocol volume to a chain.
- Every volume observation is a separate snapshot with its provider-reported amount, USD equivalent, source URL, provider as-of label, and agent retrieval timestamp in UTC.
- Record provider window limitations explicitly. An agent retrieval time is not the provider's undisclosed volume cutoff.
- Do not fabricate conversion rates, contracts, routers, factories, UI URLs or explorer URLs.
- Use `UNKNOWN` for unknown identifiers and add the corresponding issue.
- Preserve below-threshold, stale, missing, conflicting and unknown cases outside the qualified protocol registry.
- Do not treat a provider row with no numeric amount as zero.
- No retries to any failed URL or API. Log the first failure and continue.

## Deliverables

- `data/04_dex_registry.csv`: qualified protocols only, one row per protocol identity.
- `data/05_dex_deployments.csv`: one row per qualified chain deployment.
- `data/06_dex_volume_snapshots.csv`: one row per independent volume observation, including below-threshold and historical observations.
- `reports/research_reports/agent_03_dex_candidates.csv`: non-qualified / unresolved candidates.
- `reports/research_reports/agent_03_retrieval_issues.csv`: technical failures, coverage gaps, unknowns, conflicts, missing deployment identifiers and threshold exclusions.
- `reports/research_reports/agent_03_dex_discovery.md`: methods, 18-chain coverage, counts, source limitations and next task.
- `progress.md` and `handoff.md`: completion state and next agent information.

## Controlled discovery statuses

`QUALIFIED`, `BELOW_THRESHOLD`, `UNVERIFIED_VOLUME`, `UNKNOWN`, `INACTIVE`, `CONFLICT`.

Only `QUALIFIED` protocols enter `data/04_dex_registry.csv`. Historical observations may pass the numerical comparison but do not prove current eligibility. Candidate issues never block completion once documented.

## Scope boundary

This agent performs discovery and volume qualification only. Detailed fee tiers, fee recipients, gas assets, protocol fees, LP fees, aggregator fees and exhaustive contract research belong to Agent 04.

## Closure rule

Close as `COMPLETED` when the 18 canonical networks have been checked and all missing/unknown/conflicting evidence is logged. Then hand off to `AGENT-04-DEX-TECHNICAL-DETAILS`.
