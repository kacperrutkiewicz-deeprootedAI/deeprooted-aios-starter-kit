---
name: update-aios
description: Refreshes stale context files and tunes up AGENTS.md and the skills. Use when the user says "update my AIOS", "my context is out of date", "things changed", "refresh my files", "tune up my AIOS", or when a context file is 30+ days old.
---

# Update AIOS

Two parts: a **context refresh** (are your files still true?) and a **self tune-up** (are your
instructions and skills still clean?). Every change is shown first and written only after a yes.

Open with one line: "Two parts: first we refresh what's changed in your life and business,
then I tune up your setup. Want both, or just one?" Run what they pick.

If `context/about-me.md` still says `[NOT FILLED YET]`, stop: "Let's run `/onboard` first.
There's nothing to update yet."

## Part 1: Context refresh

### Step 1: Find what's stale

Read every file in `context/` (skip `decisions.md` and `session-handoff.md`). For each one,
check its `Last updated:` date against today's real date. Show a short table:

```
File            Last updated   Age
goals.md        2026-08-01     65 days   <- stale
priorities.md   2026-09-28     7 days
...
```

Stale = more than 30 days old. Also flag any file with a `[GAP: ask later]` spot, a date
that's already passed ("by Friday" two months ago), or "this week" content older than 7 days.

### Step 2: Ask what changed, one area at a time

Walk the areas in this order, stale and flagged ones first: priorities, goals, business,
customers, about-me, tools, voice. For each area, ask ONE question:

> "Your goals say: [one-line summary]. Still true, or did something change?"

- **"Still true"** -> no rewrite. Don't ask anything extra: it goes on the "checked, date
  only" list in Step 3, and move straight to the next area.
- **Something changed** -> ask one follow-up if the answer is vague, then move on.
- **Gaps** -> ask the gap's question. "Skip" leaves it as `[GAP: ask later]`.
- Keep a quick "Got it" between questions. No walls of text.

Don't write anything during the questions. Hold the answers. If they ask to lock something
in right away, show that before/after, write it after a yes, then go straight back to the
next area. Only stop early if they say stop, and then tell them what's left.

### Step 3: Show the changes, then write

For each file that changed, show a before/after of only the lines that change:

```
priorities.md
- BEFORE: #1 priority: launch the fall menu
+ AFTER:  #1 priority: hire a weekend baker by Nov 15

Checked, date only: business.md, customers.md
```

Ask: "Good to write these?" Write only what they approve. For each file you write:

- Overwrite the old line. Current truth, not history (see the memory rules in `AGENTS.md`).
- Set `Last updated:` to today.
- If the file is now longer than about one page, offer to move the older detail to
  `context/archive/[file]-YYYY-MM-DD.md`. Move it only after a yes.

If a change was a real decision (dropped a goal, raised prices, changed focus), offer to log it
at the bottom of `context/decisions.md` as `YYYY-MM-DD: decision (why)`.

## Part 2: Self tune-up

Read `AGENTS.md` and every `SKILL.md` in `.agents/skills/`. Look for these problems:

1. **Too long:** `AGENTS.md` over 150 lines, or any `SKILL.md` over 150 lines.
2. **Dead routes:** a file or folder named in `AGENTS.md` or a skill that doesn't exist.
3. **Contradictions:** two rules that say opposite things (in `AGENTS.md`, in "Your rules",
   or between a rule and `context/voice.md`).
4. **Repeated asks:** something the user keeps telling you in this chat or past handoffs
   ("stop using bullet points", "always sign off with Cheers") that isn't a rule yet.
5. **Skill overlap:** two skills that do the same job, or a skill whose description is so vague
   it would never get picked.
6. **Mirror drift:** a skill in `.agents/skills/` that's missing or different in
   `.claude/skills/` (or the other way). Don't fix it here: point them to `/sync`.

If you find nothing, say so: "Your setup is clean." Don't invent problems.

For each problem, show it as a before/after, one at a time:

```
Fix 1 of 3: Contradiction
Where: AGENTS.md, "Your rules"
- BEFORE: Tone: short and direct
-         Tone: detailed, explain everything
+ AFTER:  Tone: short and direct, with detail only when I ask
Why: two tone rules fight each other, so the AI guesses.
```

Ask "Apply this one?" and wait. Apply only approved fixes. If a fix touches a skill, change the
copy in BOTH `.agents/skills/` and `.claude/skills/` so they still match.

Never delete a skill or a file. If a skill should go, offer to move both copies to
`context/archive/skills/[skill-name]-YYYY-MM-DD/`, and only after a yes.

## Close

Show a short wrap-up:

```
Updated: priorities.md, goals.md (dated today)
Checked, no change: business.md, customers.md
Tune-up: 2 fixes applied, 1 skipped
Logged: 1 decision
```

Then one line: "Run `/update-aios` whenever life changes, or when I tell you a file is 30 days old."
