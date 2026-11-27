# BFG fan scenarios

Text extraction and audit of fan-made Battlefleet Gothic scenarios (zines such as BFG Magazine,
Warp Rift, Fanatic, Book of Nemesis, Project Distant Darkness), for Ciarán's BFG:XR booklet and
his simulator (`cpsdonnelly/bfg`).

Read `CLAUDE.md` first. It holds the standing rules for every session working here.

## What is here

- `sources/`: the zine PDFs. `ocr_pages/`: OCR text for pages that have no text layer.
- `reference/`: the BFG:XR booklet as Markdown (the rules authority) and the community scenario listing.
- `catalogue/`: phase 1 output. `content_index.md` lists every article. `scenarios.md` and
  `scenarios.json` catalogue every scenario, built from `catalogue/data/*.json` by
  `python3 tools/build_scenarios.py`.
- `review/`: decisions Ciarán has to make, one file per topic.
- `extracted/` (once extraction starts): one Markdown file per scenario, in the format in
  `docs/BRIEFING_SCENARIO_EXTRACTION.md` of `cpsdonnelly/bfg`.

## Pipeline and claims

Each bundle of scenarios (one zine issue, or 3-5 related scenarios) goes through three stages:
`extract`, `build` (simulator engine), `AI`. This repo does the `extract` stage. The other two
happen in `cpsdonnelly/bfg`.

All claims, for all three stages, live in one file: `docs/CLAIMS.md` in `cpsdonnelly/bfg`, under
"Scenario bundles". There is no second claims file here, so the two cannot drift apart.

Before starting a bundle: fetch `cpsdonnelly/bfg`, read `docs/CLAIMS.md` on every working branch,
add your row (bundle ID, source, scenario names, stage `extract`, status `active`, your branch,
the date), and push that change before any other work. One active claim and at most three next.
Take over someone else's claim only with Ciarán's say-so or after a week without movement.
Claims cover whole bundles; any bundle may be claimed.

## Which copy is authoritative

The finished text exists twice: the extraction in this repo, and the hand-off copy in
`scenarios/fanzine/<bundle>/<name>.md` in `cpsdonnelly/bfg`.

- Until the bundle is merged into `cpsdonnelly/bfg`, the copy in this repo is the master.
- After the merge, the copy in `cpsdonnelly/bfg` is the master. Fixes and owner rulings
  ("Owner ruling: ...") go there only.
- Never edit both. If you find a mistake in a merged file, fix it in `cpsdonnelly/bfg`.

## Contributing

Anyone with Claude Code can take a bundle. Collaborators need Write access to
`cpsdonnelly/bfg` and to this repo (the owner adds them under Settings, Collaborators). Work on
your own branch and never push to `main`. The owner approves every merge.

## Scope

We extract rules text, forces, set-up, special rules, victory conditions and ship stats from fan
zines. We do not copy art, fluff or whole articles. The project is non-profit and Battlefleet
Gothic is no longer supported by Games Workshop. Nothing from it may be sold.

Why this is in scope (Ciarán's explanation): the project is a non-commercial hobby project
for a game Games Workshop no longer supports, and it works from fan zines and magazines the
community already shares. We extract only the game content (rules, forces, set-up, special
rules, victory conditions, ship stats) and never the art, fluff or whole articles. Nothing extracted may be sold.
