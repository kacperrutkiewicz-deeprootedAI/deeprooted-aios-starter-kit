---
name: onboard
description: Sets up the AIOS by interviewing the user and filling in their context files. Use when the kit is fresh, or the user says "onboard me", "set me up", "let's get started", "fill in my AIOS", or wants to start over.
---

# Onboard

A friendly interview that teaches the AIOS who the user is. About 30 minutes, 16 questions
in 5 rounds. When it's done, every context file is filled in and their AI knows them.

## Before you start

1. Read `AGENTS.md` and every file in `context/`.
2. **Fresh kit** (files say `[NOT FILLED YET]`): start the interview.
3. **Already filled in:** ask one question: "You're already set up. Want to start over, or
   just redo one part (You, Business, Goals, How you work, Voice)?" Run only the rounds they pick.
   Before overwriting a filled file, confirm with the user, then copy the old version to
   `context/archive/[file]-YYYY-MM-DD.md`.

Open with one short line: "I'm going to ask you 16 questions in 5 rounds. Answer in your own
words. Say 'skip' or 'I don't know' anytime and we'll fill it in later."

## Interview rules

- **One question at a time.** Wait for the answer before asking the next one.
- Start each round with a marker: `Round 2 of 5: Your business`.
- Keep your replies short. A quick "Got it" is enough between questions.
- If an answer is vague, ask one follow-up to sharpen it (for example, "grow the business"
  becomes "to what number, by when?"). One follow-up max, then move on.
- "Skip" or "I don't know" is fine. Mark that spot `[GAP: ask later]` and keep going.
- Don't write any files during the interview. Hold the answers until the read-back.

## The questions

**Round 1 of 5: You**

1. What's your name, and what do you do?
2. What does a great week look like for you?
3. How do you want me to talk to you? (Casual, direct, detailed, funny, short...)
4. What's one thing I should never do? (A word, a habit, a tone.)

**Round 2 of 5: Your business**

5. What do you sell, and roughly what does it cost?
6. Who's your best customer? And who's a bad fit you should say no to?
7. How do customers find you?
8. Where's the business at right now? (Rough monthly revenue, team size.)

**Round 3 of 5: Your goals**

9. What's your big goal for this year?
10. What has to happen in the next 90 days?
11. What's your #1 priority this month?

**Round 4 of 5: How you work**

12. What eats up the most of your time each week?
13. What apps and tools do you use every day?
14. What tasks do you repeat every week, the same way each time?
15. What hours do you work, and when is your energy best?

**Round 5 of 5: Your voice**

16. Paste 2-3 things you've written: emails, posts, texts. More is better.

**The paste rule (the one rule you don't bend):** samples must be pasted from real writing,
not typed fresh in this chat. If they start writing something new, stop them kindly:
"Paste it raw from something you already sent. If you write it here, it's shaped by our
conversation and won't sound like the real you." Accept as many samples as they give.

## Read-back

When all 16 are answered, show a short summary grouped by round (one or two lines per
answer, gaps clearly marked). Then ask: "Did I get this right? Tell me anything to fix."
Make their fixes and show the changed lines. Write files only after they say yes.

## Write the files

Write each file in plain words, about one page max. Set `Last updated:` to today's date.
Keep the existing headings in each template and replace every `[NOT FILLED YET]` you have
an answer for. Unanswered spots get `[GAP: ask later]`. Delete each template's
"Run `/onboard` to fill this in." line. Write in first person ("I", "my"), in their words.

| File                    | Filled from                                                         |
| ----------------------- | ------------------------------------------------------------------- |
| `context/about-me.md`   | Q1 (name and role), Q2 (great week), Q12 + Q15 (how I work)         |
| `context/business.md`   | Q5 (what I sell), Q7 (how customers find me), Q8 (stage)            |
| `context/customers.md`  | Q6 (best customer, bad fit)                                         |
| `context/goals.md`      | Q9 (this year), Q10 (this quarter)                                  |
| `context/priorities.md` | Q11 (#1 this month). "This week": write the first step toward Q11   |
| `context/voice.md`      | Q3 (tone), Q4 (never), plus a 3-5 line style summary of the samples |
| `context/tools.md`      | Q13 (daily tools), Q14 (recurring weekly tasks)                     |

Also:

- **Voice samples:** save each one, word for word, as its own file in
  `references/voice-samples/` named `sample-01.md`, `sample-02.md`, and so on. Never edit them.
- **AGENTS.md:** under `## Your rules`, replace the two placeholder lines with their tone
  (Q3) and their "never" (Q4), one line each. Don't touch anything else in AGENTS.md.
- **`context/decisions.md`:** set `Last updated:` to today. Leave it empty otherwise.

Then check your work: every file above has today's date, no `[NOT FILLED YET]`, and no "Run `/onboard`" line left.

## The first win

Right after the files are written, show this (keep it this short):

```
Your AIOS is set up. It knows who you are, what you sell, where you're headed, and how you sound.

Want to see it work? I can write your next customer email in your voice right now.
```

If they say yes, ask who it's for and what it's about (one question), then write it using
`context/voice.md` and the samples. Ask: "Does this sound like you? What would you change?"
If they suggest a change to how they sound, offer to add it to `context/voice.md`.

Then close with one line: "Tonight, try `/plan-tomorrow` and I'll plan your day around your
priorities. Type `aios check` anytime to make sure I'm reading your setup."

---

_Adapted from `/onboard` in Nate Herk's AIS-OS (MIT): https://github.com/nateherkai/AIS-OS_
