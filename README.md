# Manuscript Editorial Suite — Claude Code Skill Suite

A genre-agnostic editorial team for novelists, in eight Claude Code skills. Run a
publisher-grade read, a continuity audit, a fair-play mystery check, a line-level
prose pass, and a KDP listing critique on **any** book — mystery, fantasy, romance,
thriller, literary, memoir, or anything else. It learns your book from a small
**profile** it auto-detects in your project folder. Install one or all.

## How it works — the profile

Each book project carries a tiny profile that makes every pass genre-aware instead
of guessing:

```
<your book folder>/
  .manuscript/
    profile.md          ← genre, audience, register, comps, craft standard,
                          where your series bible lives, which passes apply
    canon-ledger.json   ← optional living canon store (auto-created)
```

Every skill **walks up from your working folder** to find `.manuscript/profile.md`.
If there isn't one yet, it runs the setup skill and interviews you to build it. No
profile content ships in this repo — it's all yours, and it stays in your project
folder. Copy [`profile.template.md`](profile.template.md) to get started, or just
ask any skill to "set up my book."

## Skills Included

### Start here
- `/manuscript-profile-setup` — Creates or edits your book's profile; seeds the canon ledger
- `/manuscript-editorial-router` — Broad ask? This routes "review my book" to the right pass(es) in the right order

### The five critique passes
- `/manuscript-publisher-critique` — Acquisitions verdict + scored developmental report card, graded against your genre's markers
- `/manuscript-continuity-audit` — Catches every contradiction of your canon and every internal inconsistency
- `/manuscript-fair-play-audit` — Mystery/thriller clue-fairness: clue map, plant→payoff, "would a reader feel cheated"
- `/manuscript-prose-immersion-audit` — Line-level scene immersion: info-dumping, talking heads, filter words, micro-reactions
- `/manuscript-listing-critique` — KDP blurb, description, categories, and keywords — does the listing earn the click?

### Supporting
- `/manuscript-canon-ledger` — A living, versioned canon store (STABLE / DISPUTED / EVOLVING + an intentional-change log) that the continuity pass reads so it flags real drift, not deliberate evolution

## Install

```powershell
# Windows (PowerShell)
$dest = "$env:USERPROFILE\.claude\skills"
Get-ChildItem -Directory -Filter "manuscript-*" | ForEach-Object { Copy-Item $_.FullName $dest -Recurse -Force }
```

```bash
# macOS / Linux
cp -r manuscript-* ~/.claude/skills/
```

The canon-ledger xlsx renderer needs Python + `openpyxl` (`pip install openpyxl`).
Everything else is prompt-only.

## Quickstart

1. Install the skills (above).
2. In your manuscript folder, ask Claude: **"set up my book"** (runs
   `manuscript-profile-setup`) — or copy `profile.template.md` to
   `.manuscript/profile.md` and fill it in.
3. Ask for a read: **"review chapter 3"**, **"is the mystery fair?"**, **"critique
   my blurb"**, or **"full editorial pass"**. The router picks the right passes for
   your genre.

## Works for any genre

The publisher critique grades against per-genre marker overlays (mystery, fantasy,
romance, thriller, literary, memoir/nonfiction, or a general default). The
fair-play pass only runs for mysteries and thrillers. The prose and continuity
passes are genre-neutral. Set your genre once in the profile and the suite adapts.

## Author
[@dinaf2026-web](https://github.com/dinaf2026-web)

## License
MIT
