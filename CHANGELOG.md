# Changelog

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
