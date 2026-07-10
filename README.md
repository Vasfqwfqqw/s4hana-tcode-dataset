# SAP S/4HANA T-Code Fate Dataset

**What happens to your ECC transaction codes in SAP S/4HANA — as structured, open data.**

This is (to our knowledge) the first open, parsed dataset of the SAP Simplification List: one record per affected transaction code, with its fate (`deleted` / `replaced` / `changed` / `available`), the named successor where one exists, and — the part you won't find anywhere else — plain-English **delta notes** written for the people who actually use these codes every day: FICO analysts, AP clerks, supply chain and HR staff. Not consultants. Not architects.

**Look up any t-code in your browser:** [tavrensolutions.com/tcodes](https://tavrensolutions.com/tcodes/)

## Contents

| File | Description |
|------|-------------|
| `data/s4hana-tcode-dataset.json` | Full dataset with metadata header |
| `data/s4hana-tcode-dataset.csv` | Same records, flat CSV |
| `SCHEMA.md` | Field-by-field schema |
| `CHANGELOG.md` | Version history |

## Dataset stats (v1.0.0)

- **828 transaction codes** across 29 module areas
- Statuses: 440 replaced · 371 deleted · 14 changed · 3 available
- **212 records human-reviewed** with end-user delta notes (FI/CO first — more modules each release; `review_status` field tells you which)
- Source edition: SAP Simplification List for SAP S/4HANA 2025 (initial shipment / FPS01)

## What a delta note looks like

> **F110** — *Your payment run is safe. F110 keeps the same engine in S/4HANA, and the Manage Automatic Payments app simply gives you a guided run monitor and easier exception handling on top of it.*

## Source, attribution and copyright

This dataset is **derived structured data plus original commentary**. It contains no verbatim text from SAP documentation.

- Source document: *Simplification List for SAP S/4HANA 2025* (White Paper), published by SAP SE on the [SAP Help Portal](https://help.sap.com/doc/0df2ffddebab40cf9338488b2f18dc41/2025.latest/en-US/SIMPL_OP2025.pdf). Each record cites its source item and, where available, the relevant SAP Note number — consult those for SAP's authoritative text.
- SAP, S/4HANA, SAP Fiori and related marks are trademarks of SAP SE. This project is **not affiliated with, endorsed by, or sponsored by SAP SE**.
- Transaction codes, statuses and successor names are facts; the delta notes are original writing by Tavren Solutions.

Always verify against SAP's official documentation before making migration decisions — this dataset is a navigation aid, not a system of record.

## Licence

[CC BY 4.0](LICENSE). Use it, build on it, redistribute it — commercial use included — with attribution to **[Tavren Solutions](https://tavrensolutions.com)** and a link back to this repository.

## Contributing

Spotted an error, or want to add a delta note for a code you know well? Open an issue or PR. Corrections with an SAP Note reference get merged fastest.

## Versioning

Semantic versioning. Major version bumps on re-parse against a new Simplification List edition; minor bumps as review coverage grows.

---

Maintained by [Tavren Solutions](https://tavrensolutions.com) — AI prompt toolkits for SAP business end users preparing for the ECC-to-S/4HANA transition.
