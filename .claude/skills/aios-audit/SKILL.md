---
name: aios-audit
description: Scores the AIOS on the Four Cs (Context, Connections, Capabilities, Cadence), 25 points each, with evidence, and names the top fixes. Use when the user says "aios audit", "score my AIOS", "four cs", "how strong is my setup", "grade my AIOS", or wants to know what to improve next.
---

# AIOS Audit: the Four Cs™

Scores how well this AIOS actually works, out of 100: **Context, Connections, Capabilities, and
Cadence**, 25 points each. Score with the full rubric in [rubric.md](rubric.md) (in this skill's
folder). Read it before scoring.

The number means **verified reliability**: what you could prove works. It is not a grade on the
person. A folder, a skill, or a confident claim is not proof. Proof is a filled-in file, a real
output, a run that happened.

**Read-only.** Don't fix, move, or install anything. The only file you write is the report.

## Set expectations first (one short message)

"I'll score your AIOS on the Four Cs: Context (does it know you?), Connections (can it reach
your apps and data?), Capabilities (do your skills produce real results?), and Cadence (does
useful work happen on a schedule?). A brand-new kit scores low on Connections and Cadence.
That's normal: those are what you build next."

## Step 1: Gather evidence

1. Get today's real date. Read `AGENTS.md`, every file in `context/`, and the newest earlier
   report in `references/audits/` (`aios-audit-*.md`), if any.
2. Find the user's role, #1 priority, and up to three workflows that matter most (from
   `context/priorities.md` and `context/tools.md`). Template text like `[NOT FILLED YET]` counts
   as nothing.
3. List the skills in `.agents/skills/` and `.claude/skills/`. Look for evidence they've been
   used: outputs in `projects/`, `context/session-handoff.md`, entries in `context/decisions.md`,
   earlier reports.
4. Connections: which of the user's apps and data can this AI actually read? (Email, calendar,
   files, customer list, money, tasks.) A note that a tool exists is not a connection. If you
   can't check, mark it **unverified**.
5. Cadence: is anything scheduled to run on its own? A habit the user does by hand (like
   `/plan-tomorrow` each night) counts as a manual ritual, not automation.

Mark each finding as **verified**, **unverified**, **missing**, **stale**, or **conflicting**, and
name the file it came from. If you didn't check something, say so. Never give points for
something you didn't check.

## Step 2: Five routing probes

Test whether a fresh chat could find the answers, following only `AGENTS.md`'s routing table:

1. What does this person do, for whom, and what matters now?
2. What is the current #1 priority, and where is it written?
3. What's the latest state and next step on an important project?
4. Where is a past decision and the reason for it?
5. Where is a commonly needed doc, sample, or asset (a price sheet, a voice sample, the logo)?

For each, note: route followed, file found, and whether it was **found directly**, **found only
by searching**, or **not found**.

## Step 3: Score

Score every one of the 20 criteria in `rubric.md` using **0, 1, 3, or 5 only**. Then apply the
caps in its "Gates and stages" section. Show the math so anyone can check it. Name the stage
(Unproven, Foundation, Working with gaps, Dependable, Maintained).

## Step 4: The report

Show it in chat and save it to `references/audits/aios-audit-YYYY-MM-DD.md` (create the folder
if needed). Keep the chat version short; the saved file holds the full breakdown.

```
# AIOS Audit: YYYY-MM-DD (Four Cs, rubric v2)

## Bottom line
[2-3 sentences: what works, the biggest gap, the stage]

## Score
| C            | Score | Why (criterion points) |
| ------------ | ----- | ---------------------- |
| Context      | /25   | C1 _ C2 _ C3 _ C4 _ C5 _ |
| Connections  | /25   | N1 _ N2 _ N3 _ N4 _ N5 _ |
| Capabilities | /25   | P1 _ P2 _ P3 _ P4 _ P5 _ |
| Cadence      | /25   | D1 _ D2 _ D3 _ D4 _ D5 _ |
Raw total: __ | Caps applied: [which, why] | Final: __/100 | Stage: ____

## AGENTS.md findings
[What it does well, and anything missing, stale, or broken in it. If nothing: "No issues found."]

## Routing probes
[The 5 probes: question, file, found directly / by search / not found]

## What works
[Up to 3 strengths, with the file that proves each]

## Top fixes
1. [fix] : why it matters, the exact next step, and how you'll know it's done
2. ...
3. ...

## Since last audit
[Changes since the previous report, or "First audit: this is your baseline."]
```

Rules for the fixes: up to three, ranked by how much they'd help the user's real work. Wrong or
stale answers come before tidiness. Don't invent problems in a healthy setup.

## Close

Point to the next step in one or two lines:

- Biggest gap is stale or missing context: "Run `/update-aios`."
- Biggest gap is a missing workflow, connection, or schedule: "Run `/level-up` and we'll build
  the fix for: [the top gap]."

Suggest re-running `/aios-audit` after a fix, and monthly after that. A higher score has to come
from real use and real results, not from running the audit again.

---

_Adapted from `/audit` in Nate Herk's AIS-OS (MIT): https://github.com/nateherkai/AIS-OS.
The Four Cs™ framework is Nate Herk's._
