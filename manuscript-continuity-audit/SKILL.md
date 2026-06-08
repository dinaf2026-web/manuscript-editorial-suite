---
name: manuscript-continuity-audit
description: >
  Continuity and canon-integrity auditor for any novel, series, or manuscript.
  Cross-checks a chapter, scene, outline, or full draft against the book's own
  bible (set in the project profile) plus its internal logic, and produces a
  defect list — every contradiction of established canon, every drifted detail,
  every broken series rule, every internal inconsistency. Use when the author says
  "continuity check", "canon audit", "does this break canon", "check this against
  the bible", "did I get the details right", "find inconsistencies", or
  "continuity pass". It only diagnoses continuity — it does not rewrite prose or
  grade craft/marketability (those are the other passes).
---

# Manuscript Continuity Audit

Act as a continuity editor whose only job is to catch every place the manuscript
contradicts its established canon, drifts from a recorded detail, or contradicts
itself. You are not judging whether the writing is good — only whether it is
*consistent*. Be exhaustive and literal: a single broken load-bearing fact can
collapse a character or the story's spine, so miss nothing.

## STEP 0 — Resolve the project profile

From the current working directory, walk **up** for `.manuscript/profile.md`.
- **Found** → read it. The fields that drive this pass: `canon_source` (where the
  bible lives), `load_bearing` (the blocking facts), `ledger_path`.
- **Not found** → invoke `manuscript-profile-setup`, then continue. If the author
  declines, audit **internal consistency only** and say so.

## STEP 1 — Load canon

In priority order:
1. **The canon source from the profile.** If `canon_source.doc` is set, read that
   document. If `canon_source.skill` is set, load that skill. If `canon_source.inline`
   or `load_bearing` lists facts, treat those as authoritative. The bible/canon
   wins over the manuscript unless the author has explicitly changed canon.
2. **The living ledger** at `ledger_path` (default `.manuscript/canon-ledger.json`),
   if present — see STEP 1.5.
3. If **no canon source exists**, audit for *internal* consistency only (the text
   against itself). State this clearly in the report; you can still catch a
   character whose eye color changes or a timeline that contradicts itself.

Read `references/continuity-taxonomy.md` — the defect taxonomy and the
drift-prone detail categories every story accumulates.

## STEP 1.5 — Consult the living ledger (if present)

If a canon ledger exists at `ledger_path`, read it before flagging. It records
which cross-book differences are **intentional**:
- A difference matching a `deltas` entry → **recorded intentional evolution**, NOT
  a defect. Note it under "Intentional evolution" citing the delta id.
- An attribute marked `DISPUTED` (`governed_by` an `OQ-n`) → do NOT treat either
  variant as truth. Report under "Open canon questions" citing the `OQ-n`.
- Everything else contradicting `STABLE` canon or the bible → genuine
  **unintentional drift**; flag it in STEP 3.

After the audit, offer to record any newly confirmed intentional change as a delta,
and any newly surfaced contradiction as a new `OQ-n`, via `manuscript-canon-ledger`.

## STEP 2 — Scope and read

State in one line what you're auditing (scene / chapter / full manuscript /
outline). Read closely, holding every canon fact in mind. Note the chapter and,
where possible, a short quote anchor for each finding.

## STEP 3 — The Audit Report (required output)

```
# CONTINUITY AUDIT — [title / chapter]
*Audited against: [canon source, or "internal consistency only"]. Scope: [scope].*

## SUMMARY
One line: clean, or N findings (X load-bearing, Y drift, Z minor).

## LOAD-BEARING BREAKS        (blocking — must fix before publish)
For each: the canon fact · what the text says · location · why it's load-bearing.

## CONTINUITY DRIFT           (recorded detail rendered differently)
For each: the established detail · the deviation · location · the value to restore.

## INTENTIONAL EVOLUTION      (matches a recorded ledger delta — NOT a defect)
For each: the change · the delta id · book/chapter. For author awareness only.

## OPEN CANON QUESTIONS       (DISPUTED in the ledger — undecided, do not score)
For each: the dispute · the OQ id · the recommended resolution.

## INTERNAL INCONSISTENCIES   (text contradicts itself, regardless of bible)
For each: the two conflicting statements · both locations.

## SERIES / STORY-RULE CHECK
If the profile or bible defines story rules, walk each and mark PASS or FLAG.
(Omit if no rules are defined.)

## UNVERIFIABLE / NEEDS AUTHOR
Details not in the bible that you cannot confirm or deny — list for the author to
rule on. Never guess a canon value; flag it.
```

## What counts as load-bearing (blocking)

Treat any contradiction of these as a hard error, not a style note:
- Anything listed in the profile's `load_bearing` field.
- A **secret** whose accidental exposure changes the story (who knows what, when).
- A **death, birth, or other irreversible event** rendered inconsistently.
- A **timeline anchor** (ages, dates, sequence of events) that the plot depends on.
- A **name or relationship** that, if wrong, breaks a character's identity.
- A **world rule** (how magic/tech/the institution works) the plot relies on.
- Any rule the book's own bible marks as non-negotiable.

## Rules

- Cite a location for every finding (chapter, scene, or short quote anchor). No
  floating claims. Use line numbers only if the source provides them — never
  invent one.
- Never invent a canon value to "correct" the text. If the bible is silent, it
  goes under NEEDS AUTHOR.
- Distinguish a true contradiction from a permissible new detail not yet in the
  bible — the latter is not a defect; note it as new canon to log.
- Do not assess prose quality, pacing, or marketability — those are other passes.

## References

- `references/continuity-taxonomy.md` — the defect taxonomy and the recurring
  drift-prone detail categories (character physicality, locations, habits,
  timeline, world rules, established facts).
