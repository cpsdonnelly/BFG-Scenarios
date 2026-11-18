# Phase 1 progress

## Step 1: content index (`content_index.md`)

| Publication folder | Files | Indexed |
|---|---|---|
| Advanced_Tournament_Nemesis_Starblade | 4 | done |
| Annual_2002_Invasion | 3 | done |
| BFG_Magazine | 22 (19 issues, Old 12, Scenario Listing, xlsx index) | done |
| Fanatic_Magazine | 17 | done |
| Fanatic_Online | 34 | done |
| Project_Distant_Darkness | 3 | done |
| Warp_Rift | 50 | done |
| Warp_Storm_Planet_Killer | 3 (Warp Storm in two parts) | done |

## Step 2: scenario catalogue

Source of truth: `catalogue/data/*.json` (one file per publication) and `catalogue/shortlist.json`.
`python3 tools/build_scenarios.py` validates them and writes `scenarios.json` and `scenarios.md`.

| Publication | Entries | Done |
|---|---|---|
| BFG Advanced Scenarios | 6 | done |
| Tournament Mission Pack | 18 | done |
| Book of Nemesis | 13 | done |
| Starblade | 9 | done |
| 2002 Annual and Invasion | 11 | done |
| BFG Magazine 1-10 | 19 | done |
| BFG Magazine 11-19 | | next: Numitor, Cold Passage, They Come Only to Murder, Cerberus 1-4, Belis Corona 1-4, Hydrass, Sy'Lklell, Apotheosis etc. |
| Fanatic Magazine and Fanatic Online | | |
| Project Distant Darkness | | |
| Warp Storm and Planet Killer | | |
| Warp Rift | | |
| Review file, shortlist | | last |

## Notes for later sessions

- Pages with no text layer are not blank: OCR is in `ocr_pages/<publication>/<file>.pNNN.txt` (399 pages). Check it and the rendered page. Audited against the content index: only Tournament Pack A6/B1/B2 (pp.9-11) hold scenario rules among them; Warp Rift 18 p.38 is the Divine Intervention ship sheet; Warp Rift 46 pp.39-78 are Imperial Navy fleet rules and profiles; the rest are covers, art, poems, templates and showcase pages.
- Page text for the PDFs with a text layer was extracted with `pdftotext -layout` into the scratchpad (regenerate if lost).
- Project Distant Darkness opponents in the index were inferred from faction mentions on each mission page; confirm when cataloguing.
- Scenario entries were built from page images at 95-150 dpi where the source is OCR; the entry's `ocr_note` says so.
