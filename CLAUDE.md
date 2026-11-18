# BFG fan scenarios project

## What this project is

Ciarán (the owner) keeps a companion booklet for **Battlefleet Gothic: Extended Rules (BFG:XR)**, a fan ruleset. The booklet already has the official and XR scenarios: the Armada set, the Blue Book set, three from BFG Magazine 14, and XR's own matched-play set.

He now has a collection of fan-made scenario PDFs:

- BFG Magazine
- Warp Rift
- Fanatic
- Book of Nemesis
- Project Distant Darkness
- Starblade
- the Tournament Mission Pack
- Warp Storm, Planet Killer, Invasion
- BFG Advanced Scenarios

This project has two phases:

1. **Catalogue** every scenario in those PDFs, so Ciarán can choose which ones he wants.
2. **Build** the chosen scenarios into a **separate fan-scenario supplement**, in the same format and style as the booklet's Scenarios section.

This repo is separate from Ciarán's BFG simulator project. Don't touch the simulator.

Do phase 1 completely before starting phase 2. Don't build any scenario until Ciarán has picked it.

## Folder layout

```
CLAUDE.md                     this file
sources/                      the scenario PDFs (Ciarán adds them; one subfolder per publication)
reference/
  scenario_checklist.md       which listed scenarios the booklet already has (ticked) and which it lacks
  BFG_Scenario_Listing.pdf    the community listing the checklist was made from (titles, authors, "generic" flags)
  booklet_rules/              the booklet as Markdown, one file per section; the rules authority
    00_core-rules.md          core rules, sections 1-41
    01_...13_*.md             factions
    14_scenarios.md           the booklet's scenarios: the format to copy
    15_campaigns.md
    16-22_appendix-*.md
    media/                    the booklet's deployment diagrams
  booklet_source/BFGXR_XR_Companion.docx   the booklet itself (styles and template for phase 2)
catalogue/                    phase 1 output
review/                       review files for Ciarán (see "Review files")
```

## Standing rules (from Ciarán; follow all of them)

- **Never invent rules.** Every rule in a scenario comes from its source. If something is missing or unclear, say so in the review file; don't fill the gap.
- **Use the source's wording.** Copy rules text verbatim. Allowed without asking:
  - cutting flavour text;
  - fixing obvious typos;
  - British spelling (armour, defence, manoeuvre, behaviour, colour, centre);
  - swapping a page pointer for a section or scenario name.
- **Anything you write yourself that a person will read needs Ciarán's approval before it goes in the supplement.** That covers bridging sentences, adaptations to XR and summaries. Put each one in a review file. Your own wording in notes meant only for Claude Code is fine.
- **XR is the rules authority.** It takes priority over Remastered (another fan ruleset); note differences, don't silently merge them.
- **For Eldar, the booklet uses the fan Eldar MMS v2.0 rules,** which take priority over XR's Eldar.
- **Terminology:**
  - lances use FP (firepower), like macrobatteries; only ordnance uses S (strength);
  - "weapons batteries" in older sources are "macrobatteries" in the booklet.
- **Writing style for anything Ciarán reads:**
  - British English;
  - plain, natural prose;
  - no em dashes;
  - no "not X but Y" constructions;
  - no filler or hedging;
  - no "Clarification:" style labels in rule text.
- **Tables:** a single word must never wrap across lines in a table cell. Widen the column instead; multi-word phrases may wrap. Check the rendered output by eye, not by counting rows.
- **Review files are Markdown files, never zips.** Zips are only for Claude Code handoffs.
- **Never claim something is fixed or correct without looking at the rendered result.** Ciarán checks visually, and past "fixed" claims made from counts were often wrong.

## Phase 1: the catalogue

### Step 1: inventory the PDFs

For each PDF in `sources/`, record:

- the file;
- whether it has a text layer;
- page count;
- which scenarios it contains.

Some older magazine PDFs are scans. Scans need OCR (e.g. `ocrmypdf` or `tesseract`). Check every number, range, table and diagram label in OCR'd text against the page image, because OCR errors there change rules. Mark OCR'd scenarios in the catalogue.

### Step 2: catalogue every scenario

Write one entry per scenario, including scenarios not on the community listing. Output both:

- `catalogue/scenarios.md`, for Ciarán to read: a table plus a short paragraph per scenario;
- `catalogue/scenarios.json`, for later use by the simulator.

Fields for each entry:

| Field | Content |
|---|---|
| `id` | short slug |
| `title`, `source`, `pages`, `author` | as printed |
| `in_booklet` | yes/no, from `reference/scenario_checklist.md`. Also flag near-duplicates, e.g. Warp Rift 32's "Fleet Engagement Variant", Warp Rift 23's "Surprise attack scenario" |
| `type` | battle, raid, narrative, campaign-linked, tournament/matched, small-game |
| `generic` | playable by most factions? The listing's flag is a hint only; check the text |
| `factions_required` | e.g. "Imperial vs Chaos", "any vs Eldar", "any" |
| `forces` | points or ship limits, attacker and defender |
| `special_rules` | short list of every special rule |
| `xr_dependencies` | XR or booklet rules it relies on (sections from `booklet_rules/`) |
| `xr_conflicts` | rules that contradict XR or the booklet's rulings, or that were written for older rules (original BFG 1.0/1.5, the Armada era), with what changes under XR |
| `missing_or_unclear` | anything the source doesn't settle |
| `diagram` | none / simple / complex; is a deployment map printed? |
| `ocr` | yes/no |
| `length` | rough page count of rules text |
| `notes` | anything else Ciarán should know to decide |

The `xr_conflicts` field matters most. Many magazine scenarios predate XR. Check each one against `booklet_rules/00_core-rules.md`, the faction files and `14_scenarios.md`, and quote the conflicting rule texts with section numbers.

### Step 3: hand the catalogue to Ciarán

Send the catalogue as a Markdown file. At the top, give a short ranked shortlist with a one-line reason for each. Ciarán picks. Stop and wait for his choice.

## Phase 2: the supplement (only for scenarios Ciarán picks)

Copy the booklet's scenario format exactly. See `reference/booklet_rules/14_scenarios.md`. For example, Cruiser Clash:

1. `## Title`
2. `*Source: <publication>, <page>.*`, with the author where known
3. one or two short intro paragraphs, only if they hold rules or set-up context; cut pure flavour
4. **Forces.**
5. **Battlezone.**
6. **Set-up.**
7. the deployment diagram (a picture of the map), then the caption *Deployment diagram*
8. **First Turn.**
9. **Special Rules.** (when it has any; run-in bold labels like **Name:** for individual rules)
10. **Game Length.**
11. **Victory Conditions.**

Variant scenarios go under `### <Title> (Variant Scenario)` after their parent.

**Deployment diagrams:** redraw them cleanly in the style of `booklet_rules/media/scenarios_*.png`, which are black and white. Draw only the dimension callouts the source prints, and keep the source's orientation. Mirroring errors were a recurring problem before, so check each one against the source page by eye.

**Output format:** build the supplement as a .docx using the booklet's styles, so it can sit alongside the booklet. Use `reference/booklet_source/BFGXR_XR_Companion.docx` as the style and template source. Render to PDF to check it:

```
soffice --headless --convert-to pdf
```

Then view the pages. Before building, ask Ciarán whether he wants landscape two-column like the booklet, or something else.

**Adapting to XR:** where a scenario's rule conflicts with XR, don't rewrite it silently. Either:

- keep the source rule and add a note after it ("XR differs: …", short, grey italic, as the booklet does), or
- propose an adaptation.

Each one is a review item.

## Review files

Every decision Ciarán needs to make goes in `review/<topic>_review.md`. Each item has this form:

```
**S1. <Scenario>: <short title>.** What: <exactly what you did or found, quoting the text>.
Why: <why it needs his decision: source contradicts itself / source silent and you filled
a gap / your own wording / conflicts with XR (quote both)>. Proposed: <your recommendation>.
Decision:
```

Ciarán always wants to know **what** he is reviewing and **why**. Group items by reason:

- source contradicts itself or looks like a typo;
- source is silent;
- your own wording;
- conflicts with XR.

Changes made under the standing rules (spelling, flavour cuts, pointer swaps) go in one closing list, not as separate items.

## Booklet rulings that affect scenarios

The rulings in `reference/booklet_rules/` stand. A few relevant ones (Ciarán has ruled on these):

- **Fleet commander re-rolls** are lost if the commander's ship suffers Bridge Smashed or is destroyed. The opponent then scores the commander's VPs.
- **Fleet-builder limits:** "(or portion thereof)" rounds up, and "for every full" rounds down.
- **Light cruisers** listed in a fleet list's Cruisers category count as cruisers for "per N cruisers" limits.
- **Ordnance moving through gas or dust clouds** tests as if moving through a blast marker.
- **A single escort may be taken** if the fleet has no other escorts; otherwise escorts form squadrons per the fleet list.
- **Fleet lists don't include defences;** defences are scenario dependent.
- **Sourcebook change logs** describe changes; they are not rules text.
