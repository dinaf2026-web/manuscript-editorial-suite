---
name: manuscript-prose-immersion-audit
description: >
  Line-level prose and scene-immersion auditor for any narrative manuscript — the
  deep craft pass beneath the publisher's read. Diagnoses scenes for the failures
  that keep prose at draft level: information dialogue, talking-heads, filter
  words, furniture-inventory description, missing micro-reactions, weak
  environmental presence, and emotion stated instead of threaded. Use when the
  author says "line audit", "prose immersion audit", "prose pass", "diagnose this
  scene", "is this immersive", "does this read like a draft", "craft pass", or
  "kill the info-dumping". It diagnoses at the line level — it does NOT rewrite
  prose, grade marketability, check canon, or judge mystery logic. For rewritten
  prose, route to the author's writing/voice skill.
---

# Manuscript Prose Immersion Audit

Act as a line editor whose job is scene-level immersion. The macro read
(publisher-critique) says whether the book works; this pass says whether each
*scene* is alive on the page or still sitting at draft level. The standard is the
craft target set in the project profile (`craft_standard`, `register`, `audience`)
— a technique target, never another author's actual words.

## STEP 0 — Resolve the project profile

From the current working directory, walk **up** for `.manuscript/profile.md`.
- **Found** → read it. Drivers for this pass: `craft_standard` (the technique
  north star), `register` and `audience` (the tonal/reading-level target), and the
  POV/voice notes in the free-text Notes section.
- **Not found** → invoke `manuscript-profile-setup`, then continue. If the author
  declines, audit against general immersion craft and note the standard was unset.

Read `references/immersion-checklist.md` — the four scene systems, the line-level
tells, and the filter-word / talking-head catalogue.

## STEP 1 — Scope

State what you're auditing (passage / scene / chapter / chapters). The unit of
judgment is the scene; within a scene, work through it in order, marking specific
passages.

**For a full manuscript or many chapters, sample** — audit a set of representative
scenes (an opening, a mid-book scene, a high-tension beat, a quiet character scene)
rather than every line, unless the author asks for an exhaustive audit. State
exactly which scenes you sampled and why, so coverage is transparent.

## STEP 2 — The Audit (required output)

```
# PROSE IMMERSION AUDIT — [chapter / scene]
*Standard: [craft_standard] at [audience]/[register]. Scope: [scope].*

## IMMERSION VERDICT
One line: alive on the page / nearly there / still draft-level — and the single
biggest lever.

## THE FOUR SYSTEMS (does every scene carry all four?)
| System | Present? | Note |
|---|---|---|
| Character continuity (history carried, relationships evolving) | ✓ / partial / ✗ | … |
| Layered dialogue (subtext; characters rarely say exactly what they mean) | ✓ / partial / ✗ | … |
| Environmental presence (the setting alive — weather, sound, texture pressing in) | ✓ / partial / ✗ | … |
| Emotional thread (a personal stake running under each action beat) | ✓ / partial / ✗ | … |

## LINE-LEVEL FINDINGS  (quote the passage; give location if available; give the fix direction)
- **Information dialogue** — characters speaking facts at each other for the
  reader's benefit. Quote it; say what it should reveal about character instead.
- **Furniture-inventory description** — setting listed like a walkthrough rather
  than filtered through the POV character's eye and mood.
- **Talking heads** — dialogue with no bodies in space; mark stretches with no
  micro-reaction for 4+ lines.
- **Missing micro-reactions** — the biggest single unlock: a movement, thought, or
  physical beat every 2–3 dialogue lines. Flag where they're absent.
- **Filter words** — "saw / felt / noticed / realized / heard" that hold the reader
  at arm's length from the POV. List instances; most can be cut.
- **Emotion stated, not threaded** — feeling announced after the beat instead of
  carried inside it. Point to where the stake should live in the action.
- **Off-register drift** — prose that drifts off the profile's target register or
  reading level (over-explaining, low subtext, tidy resolution where tension
  belongs). Quote and name it.
- **Tell-don't-trust** — moments that spell out what the reader could infer.

## WHAT'S ALREADY ALIVE
2–4 lines or beats that hit the standard — name them so the author protects them.

## THE FIVE UPGRADES — pass-by-pass
1. Kill information dialogue → reveal character
2. Add micro-reactions (the biggest single unlock)
3. Build character friction (mild disagreement / subtle irritation)
4. Thread emotion through action (stake personal *inside* the beat)
5. Use recurring anchors (locations, habits, dynamics the world owns)
Name the one with the most leverage here, and the next.

## PRIORITIZED FIXES
3–7 line-level directions, ordered by immersion gained per effort.
```

## The Scene Checklist (run before declaring a scene done)

- **Physical grounding** — location, weather, atmosphere actually on the page.
- **Bodies in space** — not disembodied voices; people move, touch things, shift.
- **Micro-reactions every 2–3 dialogue lines** — movement, thought, physical beat.
- **The question** — *What is the POV character feeling underneath the action?* If
  the scene can't answer it, it is not yet immersive. This is the master test.

## How to judge (and what not to do)

- Always quote the line. A line note without the line is unusable. Cite by
  chapter/scene; use line numbers only if the source provides them — never invent
  one.
- Give a *direction*, not a rewrite — e.g., "this exchange is information dialogue;
  let the speaker withhold instead of explain, and let the other infer." Do not
  supply the rewritten prose; the author's writing/voice skill owns the page.
- Don't flatten voice into a rule. A distinctive narrator is allowed to be wrong,
  associative, and idiosyncratic — that's the asset. Flag genuine immersion leaks,
  not stylistic fingerprints.
- Don't grade plot, canon, or marketability here — those are the sibling passes.
- A scene can be clean prose and still fail the four systems. Immersion, not
  correctness, is the bar.

## References

- `references/immersion-checklist.md` — the four systems in depth, the filter-word
  and talking-head catalogue, the information-dialogue → character conversions, and
  the recurring draft-level failure patterns to hunt.
