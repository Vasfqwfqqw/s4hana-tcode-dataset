# Schema

One record per affected transaction code.

| Field | Type | Values / notes |
|-------|------|----------------|
| `tcode` | string | The ECC transaction code, e.g. `FBL1N` |
| `description` | string | Short description (may be empty in v1.0) |
| `module` | string | Module area code, e.g. `FI-AP`, `CO`, `MM-IM`, `IND-Retail` |
| `status` | enum | `deleted` — gone in S/4HANA · `replaced` — named successor exists · `changed` — still runs but behaves differently or SAP is steering you elsewhere · `available` — still works as before |
| `replacement` | string | Successor transaction or Fiori app, empty if none |
| `replacement_type` | enum | `tcode` · `fiori_app` · `none` |
| `fiori_app_id` | string | Fiori Apps Reference Library app ID for the successor app (e.g. `F0712`), verified against the Fiori Apps Library export; empty if none / not yet verified. Added in v1.1.0 |
| `sap_reference` | string | Source Simplification List item title, item number and SAP Note where captured |
| `delta_note` | string | Plain-English "what changes at your desk" note, end-user voice. Original writing — only populated on reviewed records |
| `review_status` | enum | `reviewed` — human-checked, delta note written · `pending` — machine-parsed only, treat status/replacement as provisional |
| `source_item` | string | Simplification List item number, e.g. `6.5.3` (null on manually added records) |
| `source_page` | int | Page in the source PDF (null on manually added records) |

## JSON top level

`dataset`, `source_edition`, `version`, `generated`, `copyright_note`, `record_count`, `records[]`.
