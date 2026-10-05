---
name: create-skill
description: Turns a task the user repeats into a new skill they can run with a slash command. Use when the user says "create a skill", "make a skill", "turn this into a skill", "I keep doing this", "automate this task", or has asked for the same kind of task 3 or more times.
---

# Create Skill

A skill is a saved set of step-by-step instructions. Once it exists, the user types
`/skill-name` and the AI does the task the same way every time. This skill interviews the
user, writes the new skill into BOTH skills folders, and tests it.

## Step 1: Pick the task

If they named a task, use it. If not, read `context/tools.md` ("Recurring weekly tasks") and
suggest the top 1-3: "These repeat every week. Want to turn one into a skill?"

Good skill = a task they do often, the same way, that ends in something concrete (an email,
a post, a plan, a summary). If the task is a one-off, say so and suggest just doing it instead.

## Step 2: Interview (one question at a time)

1. **What's the task, in one sentence?** ("Write the weekly update email to my team.")
2. **What would you type or say when you want it?** Collect 3-5 ways they'd ask. These become
   the trigger phrases.
3. **What do you give it to start?** (Notes, a link, a customer name, nothing.)
4. **Walk me through how you do it today, step by step.** Ask follow-ups until each step is clear.
   If they can't explain a step, say so: "If you can't explain it to a person, the AI can't do
   it either. Want to skip that step or figure it out together?"
5. **What does the finished result look like?** Ask for a real past example if they have one.
   Save it to `references/` (ask first) so the skill can point to it.
6. **What should it never do?** (Send without asking, use a certain word, guess numbers.)
7. **Which of your files should it read?** Suggest the obvious ones: `context/voice.md` for
   anything written, `context/customers.md` for anything customer-facing.

Facts that can change (phone number, address, prices, hours) don't go inside the skill. Save
them to the right `context/` file (ask first) and have the skill read that file, so a change
only happens in one place.

## Step 3: Name it

Suggest a short name: lowercase, words joined with dashes, verb first if it fits
(`weekly-update`, `write-quote`, `plan-posts`). Check `.agents/skills/` so it doesn't clash
with an existing skill. Confirm the name with them.

## Step 4: Show the draft

Draft the skill using this template. Plain words, numbered steps, under 150 lines.

```
---
name: [skill-name]
description: [What it does, in one sentence]. Use when the user says "[trigger 1]", "[trigger 2]", "[trigger 3]".
---

# [Skill Title]

[One or two lines: what this does and what the user gets at the end.]

## Before you start

- Read: [the files from question 7]
- If [a needed input] is missing, ask for it (one question).

## Steps

1. [step]
2. [step]
3. [step]

## The result

[What the finished output looks like. Point to the example in references/ if there is one.]

## Rules

- [each "never" from question 6]
- Ask before sending, publishing, or deleting anything.
```

The `name:` must match the folder name exactly. The `description:` must say both what it does
AND when to use it, with their real trigger phrases: that's how the AI knows to pick it.

Show the full draft and ask: "Anything to change before I save it?"

## Step 5: Save it to BOTH folders

After a yes, write the exact same file to both places:

- `.agents/skills/[skill-name]/SKILL.md` (the home)
- `.claude/skills/[skill-name]/SKILL.md` (the mirror, so Claude finds it too)

Then read both files back and confirm they match word for word. If they don't, fix the mirror
so it matches the home copy. Tell the user: "Saved in both skills folders."

Then add one row for it to the skills table in `AGENTS.md`: `/[skill-name]` and when to
suggest it (one short line). That's how a fresh chat knows it exists.

If the app blocks writing to `.agents/skills/` (Codex protects that folder), tell the user:
"Your app is asking permission to save into your skills folder. Please approve it." Then retry.
If it's still blocked, say plainly which copy saved and that `/sync` will finish the job.

## Step 6: Test it

Say: "Let's test it. Type `/[skill-name]`." (Some apps only see a new skill after you start a
new chat. If it doesn't show up, open a new chat in this folder and try again.)

Watch the result with them. If something is off, ask what to change, update BOTH copies the
same way, and test again. Stop when they say it works.

## Close

"Your skill `/[skill-name]` is ready. Use it a few times this week. When it gets something
wrong, tell me and we'll fix the instructions. That's how it gets better."

If they made this skill from a recurring task in `context/tools.md`, offer to note next to that
task "(skill: `/[skill-name]`)". Write it only after a yes, and set `Last updated:` to today.
