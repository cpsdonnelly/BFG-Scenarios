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
| Book of Nemesis | | |
| Starblade | | |
| 2002 Annual and Invasion | | |
| BFG Magazine | | |
| Fanatic Magazine and Fanatic Online | | |
| Project Distant Darkness | | |
| Warp Storm and Planet Killer | | |
| Warp Rift | | |
| Shortlist | | |


## Notes for later sessions

- Page text extracted with `pdftotext -layout` into the scratchpad (regenerate if lost).
- Tournament Mission Pack PDF pages 9-11 have no text layer: read from images.
- Project Distant Darkness opponents in the index were inferred from faction mentions on each mission page; confirm when cataloguing.
