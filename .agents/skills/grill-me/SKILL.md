---
name: grill-me
description: Pressure-tests a plan, idea, decision, or priority with hard questions, one at a time, until it's sharp. Use when the user says "grill me", "pressure-test this", "poke holes in my plan", "stress-test this idea", or wants to sharpen a priority before acting on it.
---

# Grill Me

Interview the user relentlessly about their plan until you both understand it the same way.
The goal isn't to kill the idea. It's to make it sharp: clear, specific, and honest about the risks.

## Before you start

1. Read `context/priorities.md`, `context/goals.md`, and `context/business.md` quietly.
   Use what's there. Never ask for something these files already answer.
2. If they didn't say what to grill, ask one question: "What should I grill you on? A plan,
   an idea, a decision, or your #1 priority?"
3. Restate the plan in one or two lines and ask: "Is that it?" Fix it until they say yes.

## Map it as a tree

Every plan is a tree of decisions. Some decisions depend on others. Example: you can't pick a
price until you know who the customer is. Work from the root down:

- **Root questions first:** who it's for, what "done" looks like, why now.
- **Then the branches:** how, when, with what money and time, what could go wrong.
- **Then the details:** the first step, the deadline, how they'll know it worked.

Don't ask a question whose answer depends on something not settled yet.

## How to ask

- **One question at a time.** Wait for the answer before the next one.
- **Give your recommended answer** under every question, so they can just say "yes" if you're right:

```
Q3: Who exactly is this for?
You mentioned "small businesses." Is it any small business, or one kind (bakeries,
contractors, salons)?

My take: start with one kind. "Bakeries in my town" is easier to reach than "small businesses."
```

- **Push on vague words.** "Soon", "more", "grow", "better", "some" all get a follow-up:
  "Soon meaning by when?" "More meaning what number?"
- **Find facts yourself.** If the answer is in their files, read it. Only ask for decisions
  and things only they know.
- **Name the risks out loud.** If something looks shaky (no time, no money, no customer
  asked for it), say it plainly and ask how they'll handle it.
- If they say "I don't know," note it as an open item and move on. Don't stall.
- If they say stop, stop. No extra question.

## When it's done

It's done when every branch has an answer or is marked open. Then show:

```
THE PLAN, SHARPENED

Before: [their original one-liner]
After:  [the sharp version: who, what, by when, how they'll know]

Decided:
- [each decision, one line]

Risks and how you'll handle them:
- [risk]: [plan]

Still open:
- [anything unanswered, and what would settle it]

First step: [one concrete action, with a day]
```

Ask: "Does this match what's in your head?" Fix anything they correct.

## Save it (only with a yes)

Offer, one at a time:

1. If they grilled their #1 priority or a goal: "Want me to update `context/priorities.md`
   (or `goals.md`) with the sharp version?" Show the before/after line, then write it after a
   yes, and set `Last updated:` to today. Keep the file's headings exactly as they are.
   Write only the one or two line "After" version there. The details go in step 3.
2. If they made a real decision: "Want me to log this in `context/decisions.md`?" Add it at the
   bottom as `YYYY-MM-DD: decision (why)`.
3. If it's a bigger project: "Want me to save the full plan to `projects/[project-name]/plan.md`?"

Never write a file without a yes. Offer these one at a time, even if they say "save it all".
Once the saves are done, the grill is over: close with the first step, and don't start new questions.

---

_Adapted from `/grill-me` in Matt Pocock's skills (MIT): https://github.com/mattpocock/skills_
