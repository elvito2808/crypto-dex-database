# Research Methodology and Evidence Policy

## 1. Source hierarchy

Prefer, in order:

1. Official network documentation, official websites, official explorer documentation, official repositories, and governance announcements.
2. Official ecosystem registries and maintained technical registries.
3. Reputable infrastructure/data providers with identifiable methodology.
4. Independent analytics and research sources as corroboration.
5. Community posts only as leads, never as sole proof for critical facts.

A listing on an aggregator is a discovery lead, not sufficient verification by itself.

## 2. Verification

For each record:
- Confirm the canonical name and identity.
- Confirm mainnet/testnet/private/deprecated status.
- Confirm identifiers using authoritative evidence (e.g. chain ID, genesis/network ID, consensus ecosystem, canonical explorer).
- Capture direct source URLs and UTC access date.
- Record conflicting values instead of silently choosing one.
- Mark unsupported fields `UNKNOWN`.

## 3. Network identity and deduplication

Do not merge networks solely because they share:
- a token ticker or native asset symbol;
- EVM compatibility;
- a chain ID reported by a third-party list;
- an ecosystem or parent chain;
- a bridge, sequencer, or infrastructure provider.

Do not split a single network into multiple entries solely because it has several RPC endpoints, explorers, aliases, or test environments.

Record aliases and parent-child relationships in metadata/notes.

## 4. Status vocabulary

- `VERIFIED`: key identity/status facts supported by authoritative evidence.
- `PROVISIONAL`: credible candidate; important verification is incomplete.
- `CONFLICT`: credible sources disagree on a material fact.
- `MISSING`: record or required evidence is incomplete.
- `DEPRECATED`: officially sunset or convincingly inactive/unsupported; explain evidence.

## 5. Time-sensitive observations

Volume, activity, TVL, and operational status can change. Store:
- observation value and unit;
- source/provider;
- exact observation timestamp in UTC;
- retrieval timestamp in UTC;
- methodology/endpoint if known.

Do not describe a time-sensitive observation as timeless.

## 6. Checkpoint protocol

After each coherent research batch:
1. Save records to the appropriate data file.
2. Append/update source registry.
3. Update agent progress.
4. Update handoff with exact next action.
5. State record counts and unresolved issues.

A checkpoint must be usable by a new agent without access to the previous agent's hidden reasoning.
