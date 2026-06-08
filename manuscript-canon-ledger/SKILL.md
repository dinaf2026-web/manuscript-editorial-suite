---
name: manuscript-canon-ledger
description: >
  Living, versioned canon ledger for any book or series — the persistent source of
  truth the continuity pass reads before it audits. Holds canon as STATE (per
  character/place/timeline fact, marked STABLE, DISPUTED, or EVOLVING) plus a DELTAS
  changelog of intentional changes tagged to book + chapter + reason, and OPEN
  QUESTIONS for unresolved canon disputes. Stored per project under
  .manuscript/canon-ledger.json. Use when the author says "canon ledger", "update
  the ledger", "record a canon change", "is this canon", "what's the canon for X",
  "add a delta", "resolve open question", or "seed the ledger from book N". It
  maintains the ledger and renders a human .xlsx view; it does NOT audit a
  manuscript (continuity-audit does that, consuming this ledger), rewrite prose, or
  judge mystery logic.
---

# Manuscript Canon Ledger — The Living Spine of a Series

A snapshot tells you what canon *is* in one book. This ledger tells you what canon
*is across the series* and **which changes were on purpose.** That distinction is
the whole point: it lets `manuscript-continuity-audit` flag only unintentional
drift instead of drowning the author in intentional evolution (a character aging, a
relationship deepening, a secret shifting).

## STEP 0 — Resolve the project

From the current working directory, walk **up** for `.manuscript/`. The ledger
lives at the path the profile's `ledger_path` names (default
`.manuscript/canon-ledger.json`), relative to that project root. If there is no
`.manuscript/` yet, invoke `manuscript-profile-setup` first (it creates the folder
and seeds an empty ledger).

The JSON is the source of truth. The xlsx is a one-way view — never edit the xlsx
as the authority; edit the JSON, then re-render. Keep both inside the project's
`.manuscript/` folder so they travel with the manuscript.

## Schema (three layers)

1. **`canon`** — current state. Each entity has attributes; each attribute has:
   - `value` — the current canonical fact
   - `status` — `STABLE` (safe), `DISPUTED` (sources disagree; see `governed_by` OQ),
     `EVOLVING` (changes on purpose; see `governed_by` delta)
   - `baseline` / `since` — where it was established
   - `conflict` / `note` — what diverges and where
   - `governed_by` — the OQ or delta id that rules this attribute

2. **`deltas`** — the changelog of **intentional** changes. Each has `from`, `to`,
   `book`, `chapter`, `reason`, `intentional: true`, and `status`. A difference
   matching a delta is NOT an error — it is recorded evolution.

3. **`open_questions`** — unresolved disputes (`OQ-n`) with `severity`, `baseline`,
   `conflict`, `options`, `recommended`, and `decision` (null until decided).

## Seed an empty ledger

When no ledger exists, write this skeleton to `ledger_path`:

```json
{
  "schema_version": 1,
  "ledger_version": "0.1.0",
  "title": "",
  "series": "",
  "author": "",
  "updated": "",
  "baseline_source": "",
  "books": [],
  "canon": [],
  "deltas": [],
  "open_questions": [],
  "legend": {
    "status": {
      "STABLE": "Safe, settled canon.",
      "DISPUTED": "Sources disagree; governed by an open question (OQ-n).",
      "EVOLVING": "Changes on purpose; governed by a delta (Dn)."
    }
  }
}
```

Fill `title`/`series`/`author` from the profile if available.

## Operations

### Look up canon ("what's the canon for X / is this canon?")
Read the JSON, find the entity/attribute. Report the `value`, its `status`, and the
governing OQ/delta. If `DISPUTED`, say so and cite the open question — never present
a disputed value as settled.

### Record a delta ("record a canon change / add a delta")
When the author makes an intentional change, append a delta with from→to, the book +
chapter where it happens, and the reason. Set the affected attribute's `status` to
`EVOLVING` and point `governed_by` at the new delta id. Bump `ledger_version` patch.
Re-render the xlsx.

### Open / resolve an open question
To raise: add an `OQ-n` with baseline, conflict, options, recommended. Set affected
attributes to `DISPUTED`, `governed_by` the OQ.
To resolve: set `decision`, apply the decided value to the attribute, flip its
`status` to `STABLE` (or `EVOLVING` if the resolution is a delta), and record a delta
if the decision changes established canon. Bump `ledger_version` minor.

### Seed from a book ("seed the ledger from book N")
Extract that book's canon (characters, places, timeline, threads, established facts,
each cited to chapter + short quote), then merge:
- New fact, no prior value → add as `STABLE` with `since`.
- Matches existing canon → leave; optionally add the citation.
- Differs from existing canon → do NOT overwrite. Open an `OQ-n` (or, if the author
  confirms it's intentional, record a delta). The ledger never silently overwrites
  established canon.

### Render the xlsx view
Run `scripts/render_ledger.py <ledger_path>` to regenerate the human view next to
the JSON (`canon-ledger.xlsx` in the same `.manuscript/` folder). Requires
`openpyxl` (`pip install openpyxl`).

## Versioning
`ledger_version` is semver: patch for a delta/citation, minor for an OQ resolution
or a book seed, major for a schema change. Always update `updated` (pass the date in;
do not rely on the system clock).

## How continuity-audit consumes this ledger
`manuscript-continuity-audit` loads this JSON FIRST, then, for every cross-book
difference it finds:
- Matches a `deltas` entry → "intentional evolution (delta Dn) — not a flag."
- Attribute is `DISPUTED` → "governed by OQ-n (undecided)" — not a fresh error.
- Otherwise → **unintentional drift**; flag it with severity, evidence, and a
  proposed fix, and offer to record it (as a delta if intentional, or a new OQ).

This is the difference between a snapshot and a graph that grows with the series.
