---
name: session-handoff
description: Saves where the user left off so the next chat picks up right there. Use when the user says "session handoff", "hand off", "wrap up", "save where we are", "I'm done for now", "pick this up later", or is about to close the chat or start a new one.
---

# Session Handoff

AI chats forget everything when you close them. This skill writes one short file,
`context/session-handoff.md`, that the next chat reads first. The next chat should be able to
pick up exactly where this one stopped, without the user re-explaining anything.

## Step 1: Look back over the whole chat

Review the entire conversation, not just the last few messages. Collect:

- What the user wanted from this session
- What got decided (and why)
- What got made or changed (files, drafts, plans), with their paths
- What's half-done
- Any question that never got a clear answer

Only include what happened in THIS chat. Don't go digging through other files.

## Step 2: Close the open questions (do not skip)

The user is here right now. A question carried into the next chat usually gets lost.

Ask every open question **one at a time**. Each one ends one of two ways:

- **Decided now:** they answer it. It goes under "Decided" with the reason.
- **Waiting on someone or something else** (a reply from a customer, a quote, a delivery):
  it goes under "Waiting on" with what unblocks it ("once Jen confirms the date, send the invoice").

"I need to think about it" counts as open. Push once, kindly: "What would help you decide right
now?" If they still can't, write it under "Waiting on: you" with what they need to decide.

## Step 3: Write the file

Write `context/session-handoff.md` with exactly this structure. Overwrite the old one: it only
ever holds the latest handoff. Use plain words. Write "none" for any empty section; never
drop a section.

```
# Session Handoff

Last updated: YYYY-MM-DD

## What this session was about
[1-2 sentences]

## Decided
- [decision] (why)

## Made or changed
- `path/to/file` : what it is

## Half-done
- [what's started but not finished, and where it is]

## Waiting on
- [item] : waiting on [who/what], unblocks when [condition]

## Pick up here
[The single next step for the next chat, in one or two sentences.]
```

## Step 4: Confirm

Show the "Pick up here" line in chat and say:

"Saved to `context/session-handoff.md`. Next time you open a chat here, I'll read it and pick
up from there. You can close this chat."

## Rules

- **One file only.** Don't change any other file in this skill. If a decision should go in
  `context/decisions.md` or a priority changed, offer that separately, after the handoff.
  Even if they say "save everything", each other file gets its own before/after and a yes.
- **Never invent anything.** If it didn't happen in this chat, it doesn't go in.
- **Short.** The whole file should fit on one screen.
- **No secrets.** Never write passwords, keys, or private account details into the handoff.
