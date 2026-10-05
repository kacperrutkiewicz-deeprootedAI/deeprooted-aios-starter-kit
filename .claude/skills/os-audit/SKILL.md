---
name: os-audit
description: Checks the AIOS for stale, broken, missing, duplicated, or bloated files, and reports what would make the AI give wrong answers. Read-only. Use when the user says "os audit", "check my AIOS", "is my setup stale", "is anything broken", "clean up my AIOS", or "my AI keeps missing things that are there".
---

# OS Audit: is your AIOS still true?

`AGENTS.md`, your context files, and your skills are all claims: "this file exists",
"this is my #1 priority", "this skill does X". This audit checks every claim against what's
actually in the folder. Broken structure is loud. Stale facts are silent, and they're the
reason an AI "keeps forgetting things": it's faithfully reading a file that stopped being true.

**Read-only.** Never fix, move, rename, or delete anything during the audit. The only thing you
write is the report at the end. Fixes happen after, one batch at a time, with the user's OK.

Get today's real date first. All the freshness math depends on it.

## The lens: four ways context breaks

Tag every finding with the one it feeds:

- **Poisoning** (false): something untrue sits where the AI reads it. A goal with a passed
  deadline, a "this week" from last month, a price that changed.
- **Bloat** (too much): files so long the AI loses the thread. `AGENTS.md` over 150 lines,
  context files over a page, junk files mixed in with real ones.
- **Confusion** (missing or wrong place): something the AI needs isn't where the routing table
  says, or a folder exists that nothing points to.
- **Clash** (contradiction): two files say different things about the same fact.

A finding that feeds none of the four is cosmetic. Say so and rank it last.

## Step 0: Last report

Look in `references/audits/` for earlier `os-audit-*.md` reports. If one exists, read the
newest. Your report must include "Since last audit": what got fixed, what got worse, what's new.

## The checks (run them in order)

### Check 1: Routing ("does everything it points to exist?")

1. Read `AGENTS.md`. List every file and folder it names (routing table, session start, skills
   table). Check each one exists. A rule pointing at a missing path = the AI walks into a wall.
2. Reverse: list the top-level folders and the files in `context/`. Flag any the routing table
   doesn't mention. Unmapped = invisible to a fresh chat.
3. Every skill in the `AGENTS.md` skills table should exist in `.agents/skills/`, and every
   skill folder should be findable (it has a `SKILL.md` with a `name:` and a `description:`).
4. Spot-check paths named inside each `SKILL.md`. Skills fail silently on dead paths.

### Check 2: Freshness ("is it still true?")

1. For every file in `context/` (skip `decisions.md`), read its `Last updated:` date:
   - **FRESH:** under 30 days
   - **DRIFTING:** 30-60 days
   - **STALE:** over 60 days, or a date that's in the future or missing
2. Read the content too, not just the date. Flag time-bound facts that have expired:
   deadlines already passed, "this week" items older than a week, "this month" from a past month.
3. Any `[NOT FILLED YET]` or `[GAP: ask later]` left? List each one.
4. Report the one date that matters most: "Your AIOS is effectively current through YYYY-MM-DD"
   (the oldest important file: priorities, goals, or business).

### Check 3: Bloat and tidiness ("is anything too big, doubled, or in the wrong place?")

1. Count lines in `AGENTS.md` (over 150 = bloat; it loads every single session).
2. Flag context files longer than about one page. History belongs in `context/archive/`.
3. Duplicates: the same content in two places, or two files that do the same job
   (`goals.md` and `goals-new.md`).
4. Loose files at the top level. The top should hold only the folders, `AGENTS.md`,
   `README.md`, and `LICENSE`. For each loose file, suggest an existing folder it belongs in.
5. Junk: empty files, empty folders (other than ones with a README), temp files, copies
   named "final-final".

### Check 4: Skills ("do they all load?")

1. Compare `.agents/skills/` and `.claude/skills/` folder by folder. Any skill missing from one,
   or different between the two = mirror drift. The fix is `/sync`.
2. Every skill folder needs a file named exactly `SKILL.md`, with `name:` matching the folder
   name and a `description:` that says when to use it. Anything else never loads, and never errors.
3. Flag any `SKILL.md` over 150 lines.

### Check 5: Clashes and safety ("does anything fight, or leak?")

1. Spot-check 3-5 key facts (the #1 priority, prices, the main goal, tone). Does each live in
   exactly one place? If two files disagree, that's a clash: name both and which looks older.
2. Do "Your rules" in `AGENTS.md` contradict each other or `context/voice.md`?
3. Secrets: look for files that look like passwords or API keys (`.env`, `*.key`, "password"
   in a filename). Don't open them or print their contents. If the folder uses git, check that
   `.gitignore` covers `.env`.

## The report

Show it in chat, then save it to `references/audits/os-audit-YYYY-MM-DD.md` (create the
folder if needed). That's the only file you write.

```
# OS Audit: YYYY-MM-DD

Your AIOS is current through: YYYY-MM-DD

| Check       | Verdict          | Worst finding |
| ----------- | ---------------- | ------------- |
| Routing     | 🟢 GREEN / 🟡 YELLOW / 🔴 RED | ...           |
| Freshness   | 🟢 GREEN / 🟡 YELLOW / 🔴 RED | ...           |
| Bloat       | 🟢 GREEN / 🟡 YELLOW / 🔴 RED | ...           |
| Skills      | 🟢 GREEN / 🟡 YELLOW / 🔴 RED | ...           |
| Clashes     | 🟢 GREEN / 🟡 YELLOW / 🔴 RED | ...           |

## What would make your AI give you a wrong answer today
- [2-4 bullets, the findings that matter most]

## Findings
- [one bullet per finding: the exact path, what's wrong, and its tag: [poisoning] [bloat] [confusion] [clash]]

## Since last audit
[fixed / worse / new. Leave this section out on the first run.]

## Fix list (nothing changed yet)
- Batch A: safety and broken skills
- Batch B: routing and tidiness (dead paths, loose files, duplicates)
- Batch C: freshness (run /update-aios on the stale files)
- Batch D: mirror drift (run /sync)
```

**Verdicts** (always with the colored circle): 🔴 RED = something that would cause a wrong answer today (dead route, expired fact in
priorities or goals, a clash on a key fact, a skill that can't load, a secret not covered by
`.gitignore`). 🟡 YELLOW = drift that will get there (a file 30-60 days old, an unmapped folder,
bloat, a gap). 🟢 GREEN = checked and clean. Be honest. Don't invent problems in a clean setup.

## After the report

Ask: "Want me to fix Batch A?" Fix one batch at a time, showing each change before you make
it. Never delete: move old material to `context/archive/` with a yes. Suggest running
`/os-audit` once a month, or after any big change.

---

_DeepRooted AI original. Companion to `/aios-audit`: this checks whether your AIOS is still true,
`/aios-audit` scores how strong it is._
