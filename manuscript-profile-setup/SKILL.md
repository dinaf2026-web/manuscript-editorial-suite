---
name: manuscript-profile-setup
description: >
  Sets up (or edits) a book project's editorial profile for the Manuscript
  Editorial Suite. Every other pass auto-detects this profile from the working
  folder; this skill is what creates it. Use when there is no profile yet, when a
  pass reports "no profile found", or when the author says "set up my book",
  "create a profile", "edit my profile", "change my genre/shelf/comps", "onboard
  this manuscript", or "configure the editorial suite". It writes
  `<project>/.manuscript/profile.md` and seeds an empty canon ledger. It does not
  critique, score, or audit — it only configures.
---

# Manuscript Profile Setup

A manuscript's *profile* is what makes the rest of the suite genre-aware instead
of guessing. It records the book's genre, audience, register, comps, craft
standard, where the canon/series bible lives, which passes apply, and any
marketing constraints. The passes read it automatically — you set it once.

## STEP 0 — Locate the project root

Determine where `.manuscript/` should live. From the current working directory,
walk **up** the parent folders looking for an existing `.manuscript/profile.md`.

- **Found** → this is an *edit*, not a fresh setup. Load it, show the current
  values, and ask what to change. Skip to STEP 3.
- **Not found** → this is a *new* setup. The project root is normally the folder
  the author is working in (where the manuscript files are). Confirm the root in
  one line ("I'll set up the profile at `<path>/.manuscript/` — is that the right
  project folder?") before writing, unless the author already named the folder.

## STEP 1 — Interview (only ask what you can't infer)

First, *try to infer* from anything already available — the manuscript text, a
bible document in the folder, the author's message. Then ask only the gaps. Keep
it to a short, friendly back-and-forth, not a form dump. The fields:

1. **Title / series / book number / author byline.**
2. **Genre + subgenre** (mystery, fantasy, romance, thriller, literary, sci-fi,
   memoir, nonfiction…).
3. **Audience + register** (adult / YA / middle-grade; and the tonal target — cozy,
   dark, comedic, grounded…).
4. **2–3 real, recent comps** the book would shelve beside.
5. **Craft standard** — an author/book whose *technique* they're aiming at.
6. **Canon source** — do they have a series bible? A doc path, a skill name, or a
   few load-bearing facts stated inline? (Fine to have none — say so.)
7. **Load-bearing facts** — the handful of things a contradiction of would break
   the book (a secret, a death, a timeline anchor).
8. **Which passes apply** — default to continuity + prose-immersion + publisher +
   listing; add **fair-play** only if it's a mystery/crime/thriller. (If the
   add-on `manuscript-cinematic-scene-audit` is installed, also add `cinematic`.)
9. **Marketing constraints** — anything that must stay out of blurbs.

Don't stall on blanks. Any field can be empty; the passes degrade gracefully and
say what they couldn't judge. Capturing genre, audience, and the load-bearing
facts gives 80% of the value.

## STEP 2 — Derive sensible defaults

- `greatness_set` ← map from genre (mystery→mystery, fantasy→fantasy, romance→
  romance, thriller→thriller, literary→literary, memoir/nonfiction→memoir-nonfiction,
  anything else→general).
- `passes` ← continuity + prose-immersion + publisher + listing by default; add
  `fair-play` iff genre ∈ {mystery, crime, thriller, suspense}; add `cinematic` iff
  the `manuscript-cinematic-scene-audit` add-on is installed.
- `ledger_path` ← `.manuscript/canon-ledger.json`.

State the derived defaults so the author can override them.

## STEP 3 — Write the profile

Write `<project root>/.manuscript/profile.md` using the schema in
`profile.template.md` (the suite ships it at the repo root; mirror its YAML keys
exactly so the passes can parse it). Preserve the author's free-text **Notes**
section. For an *edit*, change only the requested fields and keep the rest.

Then **seed an empty canon ledger** if none exists: write
`<project root>/.manuscript/canon-ledger.json` with the empty skeleton the
`manuscript-canon-ledger` skill defines (its STEP "seed an empty ledger"). Do not
populate canon here — that's the ledger skill's job.

## STEP 4 — Confirm and hand off

Report, in a few lines: where the profile was written, the key choices (genre,
audience, passes enabled, canon source), and what to do next — e.g. "Run
`manuscript-editorial-router` on a chapter, or call any single pass directly." If
the author originally asked for a critique and only needed setup to proceed,
continue straight into that pass now.

## Rules

- **Never invent canon.** If you don't know a fact, leave it blank or ask — do not
  fill load-bearing facts with guesses.
- **One profile per project root.** If you find a profile up the tree, edit it;
  don't create a second one in a subfolder.
- Keep the profile human-readable: real YAML in the frontmatter, plain prose in
  Notes. The author will open and hand-edit this file.
- This skill writes only `.manuscript/profile.md` and an empty ledger. It does not
  read, grade, or rewrite the manuscript.
