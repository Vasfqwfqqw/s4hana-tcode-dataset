# Changelog

## 1.0.0 — 2026-07-10

- First public release.
- Parsed from the Simplification List for SAP S/4HANA 2025 (initial shipment / FPS01), 806 simplification items.
- 828 t-code records: 440 replaced, 371 deleted, 14 changed, 3 available.
- 212 records human-reviewed with end-user delta notes (FI/CO modules plus high-traffic codes such as FBL1N, FB60, F110, KE30, MIRO, ME21N).
- Known limitations: `pending` records are machine-parsed and may contain parse artefacts; descriptions largely unpopulated; review coverage expands module-by-module in minor releases.
