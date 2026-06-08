---
# Manuscript Editorial Suite — project profile
# Copy this file to:  <your book project root>/.manuscript/profile.md
# Every editorial pass reads it. Fill what you know; leave the rest blank and the
# passes will fall back to sensible, genre-general behavior (and tell you what
# they couldn't assess). Nothing here is required to start — but the more you
# give, the sharper every critique gets.

title: ""                 # the book / manuscript title
series: ""                # series name, or leave blank for a standalone
book_number:              # e.g. 1  (blank for standalone)
author: ""                # your name or pen name / byline

genre: ""                 # e.g. mystery | fantasy | romance | thriller | literary | sci-fi | memoir | nonfiction
subgenre: ""              # e.g. cozy mystery | epic fantasy | romantic suspense | coming-of-age
audience: ""              # e.g. adult | YA | middle-grade | new-adult
register: ""              # the tonal target, e.g. cozy-with-real-stakes | dark literary | breezy comedic | grounded

# 2–3 REAL, recent comparable titles this book would shelve beside.
comps:
  - ""
  - ""
  - ""

# The craft north star: an author/book whose TECHNIQUE (not words) you're aiming
# at. The prose pass and publisher read use this as the standard to measure against.
craft_standard: ""        # e.g. "Tana French's interiority" | "Fredrik Backman's warmth"

# Which greatness rubric the publisher critique scores you against. Pick the one
# closest to your book; "general" works for anything.
greatness_set: "general"  # mystery | fantasy | romance | thriller | literary | memoir-nonfiction | general

# Which passes apply to this book. Remove any that don't fit.
#   continuity        — canon / internal-consistency audit (all genres)
#   fair-play         — mystery clue-fairness audit (mystery/crime/thriller only)
#   prose-immersion   — line-level scene-immersion audit (all narrative prose)
#   publisher         — acquisitions + developmental read (all)
#   listing           — KDP blurb / categories / keywords (all)
# (A cinematic / blocking pass is available as a separate add-on skill,
#  manuscript-cinematic-scene-audit — add `cinematic` here once it's installed.)
passes:
  - continuity
  - prose-immersion
  - publisher
  - listing
  # - fair-play       # uncomment for mysteries/thrillers
  # - cinematic       # add-on: manuscript-cinematic-scene-audit (all narrative prose)

# WHERE your series bible / canon lives. Any one of these (or none):
#   doc:   a path to a bible document the continuity pass should read
#   skill: the name of a Claude skill that holds your canon
#   inline: list load-bearing facts right here (see below)
# With none set, continuity falls back to internal-consistency-only.
canon_source:
  doc: ""                 # e.g. "G:/.../My Series Bible.docx"  or a local path
  skill: ""               # e.g. "my-series-bible"
  inline: []              # e.g. ["Protagonist is left-handed", "Story spans one summer"]

# Load-bearing facts: the handful of things a contradiction of would BREAK the
# book or a character (a secret, a death, a timeline anchor). The continuity pass
# treats a break of these as blocking. List the ones that matter most.
load_bearing: []          # e.g. ["The narrator's brother is dead from page 1", "Magic costs memory"]

# Marketing / spoiler constraints for the listing pass — anything that must stay
# OUT of blurbs and back-cover copy.
marketing_constraints: []  # e.g. ["Do not reveal the twin reveal", "Keep the killer's identity hidden"]

# Canon ledger location (the living, versioned canon store). Default is fine.
ledger_path: ".manuscript/canon-ledger.json"
---

# Notes (free text — anything the passes should know)

Write anything here that doesn't fit a field above: the emotional spine of the
book in one sentence, recurring motifs, a character's voice quirks to protect,
known weak spots you want watched, the intended shelf if it's contested, etc.
The passes read this section too.
