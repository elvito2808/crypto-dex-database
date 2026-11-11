# Post-closeout QA amendment — Celestia canonical scope policy conflict

**Amendment status:** COMPLETED  
**Issue disposition:** `OPEN_DEFERRED_FINAL`  
**Baseline HEAD:** `f8edf3e5c3d7b7fee4ace55d4dc25db617aa85b7`  
**Branch:** `qa/celestia-canonical-scope-amendment`  
**New issue ID:** `POSTCLOSEOUT-CELESTIA-001`

## Scope and finding

This amendment was limited to the seven repository records enumerated in the task. No external research, source retrieval, URL retries, network refresh, or additional chain discovery was performed.

Celestia remains in the canonical 18-network list and its integrated `CHAIN:Celestia` record remains `VERIFIED`. The metadata row explicitly says `Active — Mainnet Beta; explicitly experimental` and retains the experimental caveat in `notes`. Agent01 instructions require only VERIFIED public production Mainnets and explicitly exclude experimental environments (instructions lines 65–66 and 135); the Agent01 handoff says experimental candidates do not belong in the canonical list (line 34). Existing `ISS-000010` concerns UNKNOWN `parent_chain` and numeric `chain_id` fields and does not independently register this canonical-membership/policy contradiction.

The new issue records exact affected files and fields, evidence locations, the contradiction, and why it remains unresolved. No decision was made to remove Celestia or to change its status. The canonical list, metadata and all downstream data were preserved.

## Changed files

| File | Change |
|---|---|
| `reports/research_reports/agent_05_consolidated_issues.csv` | Appended one new `PostCloseout` issue row using the existing 19-column schema |
| `data/final_crypto_dex_database.csv` | Appended one `AGENT_ISSUE` row using the existing 25-column schema |
| `reports/research_reports/post_closeout_qa_amendment_celestia.md` | Added this post-closeout status and validation record |

## Counts

| Measure | Baseline | After amendment |
|---|---:|---:|
| Consolidated issue records | 232 | 233 |
| Integrated database records | 807 | 808 |
| Integrated `AGENT_ISSUE` records | 232 | 233 |
| Canonical networks | 18 | 18 |

Issue origins: Agent01 14; Agent02 32; Agent03 118; Agent04 54; Agent05 14; PostCloseout 1. All 232 pre-existing issues and IDs remain; the amendment adds only `POSTCLOSEOUT-CELESTIA-001`. All 233 consolidated issues and integrated issue records remain `OPEN_DEFERRED_FINAL`.

## Validation results

- PASS — consolidated issue register has 233 data rows and 19 columns.
- PASS — composite `origin_agent + source_issue_id` identities are unique (233/233); the new issue ID occurs exactly once.
- PASS — integrated database has 808 data rows and 25 columns; `record_id` values are unique (808/808).
- PASS — integrated database contains 233 `AGENT_ISSUE` rows; the new issue occurs exactly once with `OPEN_DEFERRED_FINAL`.
- PASS — all 232 pre-existing consolidated issue CSV records and all 807 pre-existing integrated database records are byte-identical at the raw record-line level to the baseline snapshot.
- PASS — all five untouched source/evidence files retained their baseline blob SHAs: `data/01_chains.txt`, `data/01_chains_metadata.csv`, `agents/agent_01_chains/instructions.md`, `agents/agent_01_chains/handoff.md`, and `reports/research_reports/agent_01_retrieval_issues.csv`. The two other reviewed CSVs received only the single appended issue row each; all pre-existing records in them were preserved byte-for-byte.
- PASS — Celestia remains present in the unchanged 18-entry canonical list; metadata retains its experimental wording and VERIFIED metadata status; the integrated Celestia chain record is unchanged.
- PASS — existing `ISS-000010` remains unchanged and is not repurposed.
- PASS — no original Agent01–Agent05 research source files or original issue records were modified.

## Read-back blob SHAs

| File | Read-back blob SHA |
|---|---|
| `reports/research_reports/agent_05_consolidated_issues.csv` | `874142bc695f96addb34a9e5faa9f12f5f715fe9` |
| `data/final_crypto_dex_database.csv` | `a9ff48abafb8892b51aca5a438f6fbb8753c9728` |

The issue register and integrated database were read back from the amendment branch after writing. This report is the status synchronization artifact; the amendment is complete, while the underlying Celestia policy conflict intentionally remains open and deferred.
