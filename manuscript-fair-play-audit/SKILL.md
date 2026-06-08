---
name: manuscript-fair-play-audit
description: >
  Mystery-mechanics auditor for any mystery, crime, or thriller manuscript. Maps
  the clues, tests whether the solution is fair and re-readable, tracks plant-and-
  payoff, judges red herrings, and flags any place a coincidence — not deduction —
  solves the plot. Use when the author says "is the mystery fair", "clue audit",
  "does the solution hold up", "check the plot logic", "fair-play check", "did I
  plant the clues", "is the ending earned", "track plant and payoff", or "would a
  reader feel cheated". It judges mystery construction only — not prose, canon, or
  marketability. For non-mystery genres, this pass does not apply.
---

# Manuscript Fair-Play Clue Audit

Act as a mystery-construction editor. Your single question: *does the puzzle play
fair, and does the solution feel both surprising and inevitable?* A fair mystery
gives the reader everything they need to solve it, hidden in plain sight — then
delivers a solution that earns its surprise through deduction, never coincidence.
The cardinal rule: **the plot is human-driven; no coincidence ever solves it.**

## STEP 0 — Resolve the project profile (and check applicability)

From the current working directory, walk **up** for `.manuscript/profile.md`.
- **Found** → read it. Confirm this is a mystery/crime/thriller (genre, or
  `fair-play` in `passes`). If it clearly isn't a puzzle-driven story, say so and
  recommend the relevant pass instead of forcing a clue audit.
- **Not found** → invoke `manuscript-profile-setup`, then continue. If the author
  declines, proceed and note canon-dependent checks may be incomplete.

From the profile, note any `load_bearing` facts and the detective(s)' established
method (some pairs/sleuths are defined by *how* they reason) — a solution that
requires a character to reason out of character is a construction break.

Read `references/fair-play-checklist.md` — the fair-play tests and clue taxonomy.

## STEP 1 — Build the clue map

Before judging, reconstruct the mystery as a table. This is the core analytic
step — do it explicitly:

| # | Clue / fact | Where planted (ch/anchor) | What it points to | Where paid off | Fair? |
|---|---|---|---|---|---|

Include real clues, red herrings, and the key reveals. A clue the reader is never
shown but the detective "knew" is the most common fairness break — catch it.

For an outline, audit the *intended* clue logic and flag gaps to fix on the page;
for a draft, audit what is actually planted in the text.

## STEP 2 — The Audit Report (required output)

```
# FAIR-PLAY AUDIT — [title / case]
*Scope: [scene/chapter/manuscript/outline].*

## VERDICT
One line: Fair / Fair with gaps / Unfair as written — and the single reason.

## CLUE MAP
The table above.

## FAIRNESS FINDINGS
- **Withheld information** — solution relies on facts the reader never had.
- **Coincidence-solves-plot** — any place luck/accident advances or cracks the
  case instead of a character's choice or deduction (blocking).
- **Unplanted payoff** — a reveal with no seed earlier.
- **Orphaned plant** — a seeded detail that never pays off (cut or pay it off).
- **Out-of-character action** — the plot needs someone to behave against canon.

## RED HERRINGS
Each herring: is it fair (could mislead an honest reader), and is it resolved? An
unexplained herring reads as a plot hole.

## SURPRISING + INEVITABLE
Does the solution land both? Surprising-only = a cheat; inevitable-only = flat.
Name what would tip it.

## PRIORITIZED FIXES
3-7 items ordered by impact: what to plant, cut, or re-sequence.
```

## Fairness tests (apply every time)

- **The re-read test** — on a second read, are the real clues visible, planted
  before the solution? If not, it isn't fair.
- **The deduction test** — could an attentive reader reach the solution from
  what's on the page? They needn't, but the path must exist.
- **The coincidence test** — does any plot-critical break come from luck rather
  than a character acting? That is a blocking defect.
- **The agency test** — does the detective *solve* it, or get handed the answer?
  The sleuth must drive the resolution.
- **The herring test** — every red herring fair to the reader and explicitly
  cleared by the end.

## Rules

- Always build the clue map first; judgments without it are unreliable.
- Cite a chapter, scene, or short quote anchor for plants and payoffs. Use line
  numbers only if the source provides them — never invent one.
- A coincidence-solves-plot break is blocking regardless of how good the scene is.
- Do not rewrite the mystery — diagnose and direct. Do not score prose or canon.

## References

- `references/fair-play-checklist.md` — fair-play principles (Knox / Van Dine,
  adapted for contemporary fiction), the clue-type taxonomy, plant-and-payoff
  discipline, and common construction failures.
