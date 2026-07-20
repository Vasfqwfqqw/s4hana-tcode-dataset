# Changelog

## 1.2.2 — 2026-07-20

- Follow-up to 1.2.1: 3 more records carrying the same successor-mislabelled-as-deleted bug, missed by the original 35-code Fiori Apps Library cross-reference because they have no Fiori Apps Library entry at all. `status` `replaced` → `available`: KB21N, KB23N, KB24N. Delta notes were already correct and human-reviewed (`review_status=reviewed` unchanged) — status-field-only fix, same pattern as 1.2.1's KB11N/KB13N/KB14N group.
- Record count unchanged (838). No new records added or removed.
- See `dataset/launchpad-review-worklist-v1.1-RESOLVED.md` §D for the citation (S4TWL - ACTIVITY-BASED COSTING, item 6.5.2, SAP Note 2270408).

## 1.2.1 — 2026-07-20

- Data-quality patch: 30 records were misclassified `deleted`/`replaced` when SAP's Simplification List names them as the *successor* transaction, not the one being withdrawn — a parser bug (free-text extraction couldn't tell which column of the obsolete/successor table a code came from). All 30 corrected to `status=available` (or `changed` for KE27), `review_status=reviewed`, `replacement` cleared: CC04, CL20N, CL22N, CL24N, CT04, CT12, CU51, PMEVC, IQS8, IQS9, QA32, QE09, QM10, QM13, DIS01N, PEG01N, WLI2, KB11N, KB13N, KB14N, KSC5, KSII, KSU5, KSV5, WB24N, WBRR, POFO31, POFO32, POFO33, KE27.
- KE27 is a distinct bug class (header/value mismatch, not a column mix-up): the Simplification List text says the transaction remains available but is scoped to costing-based CO-PA; the previous delta note incorrectly treated it as withdrawn. Delta note rewritten, status `deleted` → `changed`.
- For 12 of the 30 (KB11N, KB13N, KB14N, KSC5, KSII, KSU5, KSV5, WB24N, WBRR, POFO31, POFO32, POFO33), the delta note was already correct and human-reviewed; only the `status` field was wrong, meaning this bug had already shipped in `reviewed` records.
- `WB25` is intentionally **not** included in this patch. The Simplification List's obsolete/successor table names `WB25_COMPAS`, not plain `WB25`, as the withdrawn code — but WB25 is independently confirmed as a real, distinct SAP transaction, and the live delta note asserts it's a genuine standalone withdrawal. Open question, unresolved; kept at its current (`pending`) state pending a human/practitioner call.
- Record count unchanged (838). No new records added or removed.
- See `dataset/launchpad-review-worklist-v1.1-RESOLVED.md` (source project) for the full per-code SL citations and resolution method.

## 1.2.0 — 2026-07-16

- 10 new manual records for changed-but-available FI/CO codes (status `changed`, human-reviewed with end-user delta notes): FAGLL03, FAGLB03, FS00, FB50, FB03, F-53, F-28, F-03, KSB1, KOB1. These codes are not in the Simplification List (they survive conversion) but are high-traffic end-user lookups.
- All 10 successor Fiori app IDs verified against the SAP Fiori Apps Reference Library export (2026-07-13): F2217, F0707A, F0731A, F0718, F0717, F1612, F1345, F1579, F4023 (×2).
- Record count 828 → 838 (24 changed, 3 available). Human-reviewed count 197 → 207.

## 1.1.1 — 2026-07-14

- Copyright hygiene pass: ~30 delta notes reworded to remove short phrase overlaps with SAP Simplification List instructional text (verified programmatically — remaining shared strings are official SAP product/feature/app names only, retained as factual identifiers). No status, replacement, or fiori_app_id changes.

## 1.1.0 — 2026-07-14

- New field `fiori_app_id`: successor Fiori app IDs verified against the SAP Fiori Apps Reference Library export (2026-07-13). Populated on FBL1N (F0712), FBL3N (F2217), FBL5N (F0711), F110 (F0770), MB51 (F1077), ME21N (F0842A); coverage grows each release.
- Successor app naming corrected to SAP's current catalogue: FBL1N successor is **Manage Supplier Line Items** (SAP renamed Vendor to Supplier); FBL3N successor is **Display Line Items in General Ledger** ("Manage G/L Account Line Items" no longer exists in the Fiori Apps Library).
- Delta notes added for the 3 `available` records (KKR0, KKBC_HOE_H, OKB9 — codes the Simplification List names as successors).
- 35 records with status `deleted`/`replaced` whose t-code still appears as a SAP GUI launchpad app in the Fiori Apps Library set back to `review_status=pending` while we verify their real fate (several are marked "(Deprecated)" by SAP). Human-reviewed count is 197 accordingly.
- `SCHEMA.md`: `replacement_type` enum corrected to match the data (`fiori_app`, not `fiori`).

## 1.0.0 — 2026-07-10

- First public release.
- Parsed from the Simplification List for SAP S/4HANA 2025 (initial shipment / FPS01), 806 simplification items.
- 828 t-code records: 440 replaced, 371 deleted, 14 changed, 3 available.
- 212 records human-reviewed with end-user delta notes (FI/CO modules plus high-traffic codes such as FBL1N, FB60, F110, KE30, MIRO, ME21N).
- Known limitations: `pending` records are machine-parsed and may contain parse artefacts; descriptions largely unpopulated; review coverage expands module-by-module in minor releases.
