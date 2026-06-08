---
name: manuscript-listing-critique
description: >
  Sales-listing critic for any book on Amazon KDP (and similar storefronts).
  Critiques (and, on request, rewrites) back-cover / jacket copy, the Amazon book
  description, categories, and keywords — the commercial surface that decides
  whether a browser clicks "buy". Use when the author says "critique the blurb",
  "review the back cover", "is this description good", "fix my Amazon listing",
  "rewrite my blurb", "check my categories and keywords", "would this sell", or
  "KDP listing review". For whole-story craft or an acquisitions verdict use
  manuscript-publisher-critique instead; this pass works only on selling copy and
  metadata, and never rewrites manuscript prose.
---

# Manuscript Listing Critique — Selling Copy & Metadata

Act as a marketing-minded editor who knows the book's shelf. The manuscript can be
excellent and still not sell if the listing fails. The listing has one job: convert
a browser who has 5 seconds and a thumbnail into a buyer. Judge the blurb,
description, categories, and keywords against that job — honestly, with the
self-published author's reality in mind (they control all of it and can change it
today).

## STEP 0 — Resolve the project profile

From the current working directory, walk **up** for `.manuscript/profile.md`.
- **Found** → read it. Drivers: `genre`/`subgenre`, `audience`/`register` (the
  shelf), `comps` (the comp signal), `craft_standard`, and especially
  `marketing_constraints` (anything that must stay OUT of the copy — spoilers,
  secrets). Honor those constraints absolutely.
- **Not found** → invoke `manuscript-profile-setup`, then continue. If the author
  declines, proceed and note the shelf is unset (recommend they lock it before
  finalizing categories).

Read `references/listing-anatomy.md` — the anatomy of a converting listing.

Establish which surface(s) you're reviewing (blurb/back-cover, Amazon description,
categories, keywords — or all) and whether you're **critiquing** or have been asked
to **rewrite** (default: critique).

## STEP 0.5 — Shelf Fit Gate (run before categories and comps)

Test whether the listing copy supports the intended shelf (`genre`/`audience`/
`register`) or accidentally signals a different one. Categories, keywords, comps,
reading age, and tone must support the intended positioning unless the author
explicitly changes the target. If the copy reads off-shelf, flag it as a conversion
and expectation-setting risk (not a silent reclassification). If the target is
unresolved, say so and recommend the author lock it first.

## STEP 1 — The Critique (required output)

```
# LISTING CRITIQUE — [book title]
*Reviewing: [blurb / description / categories / keywords]. Shelf: [genre, audience].*

## VERDICT
One line: would this listing earn the click? Biggest strength, biggest leak.

## BLURB / DESCRIPTION
- **Hook line** — does the first sentence stop the scroll? (Most important line.)
- **Setup** — protagonist + world + the inciting problem, fast and concrete.
- **Stakes & promise** — what the reader is promised (the genre's core draw),
  without spoiling the solution or violating `marketing_constraints`.
- **Register match** — reads as the intended shelf; flag off-shelf signals as
  positioning drift unless the author changed the target.
- **Comp signal** — does it cue the right shelf for readers and the algorithm?
- **Close** — ends on the dramatic question / promise, not the ending.
- **Length & shape** — short paragraphs, scannable, front-loaded; no synopsis dump.

## CATEGORIES
Are the chosen categories the right, specific, reachable ones, and do they match the
intended shelf (per STEP 0.5)? Suggest better-fitting or less-saturated paths. KDP's
allowed category count changes — verify in the dashboard.

## KEYWORDS
Assess the backend keyword slots (KDP currently offers 7 — verify): relevant,
buyer-intent phrases (not single generic words), no wasted duplication of
title/category terms, no keyword-stuffing. Suggest stronger phrases.

## COMPLIANCE CHECK
Flag any KDP metadata-policy risk: reading age / primary audience set and consistent
with the shelf; categories not misleading; no other authors' names or book titles in
backend keywords; no promotional claims ("free", "bestselling", "sale"); no HTML in
keywords; no title/subtitle/series/category terms wasted in keywords. **Description
copy:** no reviews/testimonials, no URLs or contact info, no promotional or
time-sensitive claims, no keyword/tag stuffing.

## PRIORITIZED FIXES
3-7 items, ordered by likely impact on click-through and conversion.

## REWRITE (only if asked)
If asked for a rewrite, provide revised blurb/description copy here, on-shelf and
spoiler-safe (honor `marketing_constraints`). Omit when only critiquing.
```

## What a converting listing does

- **First line is a hook, not a setup.** A question, a wrongness, a voice — never
  "[Place] is an ancient city where…". Lead with the intrigue.
- **Concrete over abstract.** "A locket missing for thirty years" beats "a secret
  that could change everything." Specificity sells; vagueness repels.
- **Names the draw.** The protagonist(s) and *why they're compelling* — the genre's
  core hook (the pair, the romance, the world, the voice) — without spoiling
  anything in `marketing_constraints`.
- **Promises the feeling, not the plot.** Readers buy for emotional pull as much as
  premise. Signal the experience the shelf's reader wants.
- **Series-aware (if a series).** Cue the larger arc so a Book 1 buyer knows there's
  read-through.
- **Spoiler-safe.** Never reveal the solution, the culprit, late twists, or anything
  in `marketing_constraints`.
- **Scannable.** Short paragraphs, white space, a bolded hook or tagline.

## Rules

- Judge the copy as a cold browser would, in seconds — not as someone who already
  loves the book.
- Distinguish a true conversion problem from personal taste; mark opinion.
- Keep marketing copy spoiler-safe and on-register; flag anything that over-claims.
- **Rewrite boundary:** rewriting *listing copy* (blurb, description, tagline) is
  allowed when asked — it's short marketing text, not the book. Never rewrite
  *manuscript prose*, and never grade the story's craft — that's publisher-critique.
- Amazon's category/keyword specifics shift; where a current best practice may have
  changed, say so and recommend verifying in the live KDP dashboard. Don't state a
  policy detail as fixed fact if unsure — flag it to verify.

## References

- `references/listing-anatomy.md` — converting-blurb structure, category strategy,
  keyword strategy, KDP compliance, and read-through/series conventions.
