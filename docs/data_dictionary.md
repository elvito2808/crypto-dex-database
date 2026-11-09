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
