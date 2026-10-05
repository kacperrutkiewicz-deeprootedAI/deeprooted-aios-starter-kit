---
name: sync
description: Makes the two skills folders (.agents/skills and .claude/skills) match again. Use when the user says "sync", "sync my skills", "my skill is missing", "a skill doesn't show up in Claude", "the skills folders don't match", or after installing a new skill.
---

# Sync

Your skills live in two folders:

- `.agents/skills/` is the **home**. Most AI apps read skills from here.
- `.claude/skills/` is the **mirror**. Claude only reads skills from here.

Both must hold the same skills with the same words. This skill finds every difference and
fixes it, with the user's OK. It never deletes anything.

## Step 1: Compare

List every skill folder in both places. For each skill name, compare the two copies
word for word: the `SKILL.md` AND any other files inside the skill folder. Sort every skill into
one of four groups:

| Group             | What it means                               |
| ----------------- | ------------------------------------------- |
| Match             | In both folders, identical                  |
| Missing in mirror | In `.agents/skills/` only                   |
| Missing in home   | In `.claude/skills/` only                   |
| Different         | In both, but the words or files don't match |

Show the user a short report:

```
Skills checked: 12
Match: 10
Missing in mirror: weekly-update
Different: grill-me (SKILL.md, 3 lines differ)
```

If everything matches: "All [N] skills match. Nothing to fix." Stop there.

## Step 2: Fix, one skill at a time

**Missing in mirror** (the usual case: a new skill was dropped into `.agents/skills/`):
copy the whole folder from `.agents/skills/` to `.claude/skills/`.

**Missing in home** (usually a skill made or installed from inside Claude):
copy the whole folder from `.claude/skills/` to `.agents/skills/`.

**Different:** show the lines that differ, side by side, and ask which version to keep:

```
grill-me: the two copies differ
.agents/skills (home):   "Ask one question at a time."
.claude/skills (mirror): "Ask up to three questions at a time."
Keep which one? (home / mirror)
```

If they're not sure, recommend the home copy, since `.agents/skills/` is the home. Copy the
kept version over the other one.

Before each fix, say what you'll do in one line ("Copy weekly-update into `.claude/skills/`?").
The user can say "fix them all" to approve the rest at once.

**If they meant to remove a skill** ("I deleted that on purpose"), don't restore it. Don't
delete the other copy either. Offer to move it to `context/archive/skills/[skill-name]-YYYY-MM-DD/`,
and move it only after a yes.

## Step 3: Check your work

Compare both folders again, exactly like Step 1. Every skill should now be in the Match group.
If anything still differs, fix it before you finish.

## Close

```
Synced. [N] skills, both folders match.
Fixed: [list what you copied or replaced]
```

Then one line: "If a skill still doesn't show up, start a new chat. Some apps only load skills
when a chat starts."

## Rules

- Never delete a skill or a file. Archive only with a yes.
- Copy whole skill folders, not just `SKILL.md`, so any extra files inside come along.
- Don't edit what a skill says. This skill only copies. To change a skill, use `/update-aios`
  or edit it with the user.
