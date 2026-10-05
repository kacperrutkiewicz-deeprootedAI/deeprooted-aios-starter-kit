---
name: plan-tomorrow
description: Builds tomorrow's hour-by-hour plan from the user's priorities, energy, and commitments. Use when the user says "plan tomorrow", "plan my day", "what should tomorrow look like", or wants to map out the next day.
---

# Plan Tomorrow

A short end-of-day interview that turns tomorrow into a clear plan, so the user wakes up
knowing exactly what to do. Covers work and personal life: it's their whole operating system.

## Before you start

1. Work out tomorrow's date and weekday. Never guess: check today's date first.
2. Read quietly (don't dump these in chat):
   - `context/priorities.md` (the #1 priority and this week)
   - `context/about-me.md` (work hours, energy peaks, biggest time sink)
   - `context/goals.md` (the 90-day goal)
   - `context/tools.md` (recurring weekly tasks: is one due tomorrow?)
3. If `context/` is still `[NOT FILLED YET]`, say: "Let's run `/onboard` first so I can plan
   around your real priorities." Stop there.

## The interview

Ask **one question at a time**. Keep it to these five, in this order. Skip any the files
already answer clearly, but confirm what you assumed ("You usually start at 8, right?").

1. **Start and end.** "What time do you want to start tomorrow, and when do you want to be done?"
2. **Fixed stuff.** "Anything already locked in? Meetings, calls, appointments, pickups?"
3. **Personal stuff.** "Anything personal I should block in? Family, workout, errands, faith,
   time with someone, things around the house?" Always ask this one. People forget their own life
   when they plan work. Treat what they say with the same care as work.
4. **The big three.** "What are the three things that would make tomorrow a win?" If one of them
   doesn't connect to the #1 priority in `context/priorities.md`, point it out kindly and ask if
   the priority should be on the list.
5. **Anything else on your mind?** Loose ends, small tasks, things they're worried about forgetting.

## Build the plan

Draft the day hour by hour. Rules:

- **Fixed stuff first.** Place locked appointments and personal commitments, then fill around them.
- **Hardest work at peak energy.** Put the #1 priority work in their best energy window
  (from `about-me.md`). Small tasks and admin go in low-energy slots.
- **Breaks are real blocks.** Add meals and short breaks between long work blocks.
- **Respect the end time.** No work blocks after the time they want to be done. Personal
  blocks can go after.
- **Weekly tasks keep their day.** If an item belongs to a weekly task on another day (from
  `tools.md`), point it out and ask before moving it to tomorrow.
- **Be honest about the size.** If the day holds more than fits, say so and suggest what to cut
  or move. If it runs past 10 hours of work, flag it and offer a lighter version.
- **Name the cut line.** Mark which block gets dropped first if the day runs long.

Show it like this:

```
TOMORROW: [Weekday, Month Day]

8:00 - 10:00   Deep work: [the #1 priority task]
10:00 - 10:15  Break
10:15 - 11:00  [Fixed meeting]
...

Win condition: [the big three, one line each]
Cut line: [the block that goes first]
Totals: about [X] hours of focused work, [N] breaks
```

Then ask: "Want to change anything?" Adjust and show the updated plan until they say it looks
good. One quick check at the end: did every personal commitment from question 3 make it in?

## After they approve

- Tell them to copy it into their calendar, or keep this chat open in the morning.
- If tomorrow's plan shows the priorities have changed (a new #1, a finished item), offer to
  update `context/priorities.md`. Show the change and wait for a yes before writing it. Set
  `Last updated:` to today.
- If they made a real decision while planning (dropped a project, changed a goal), offer to log
  it in `context/decisions.md` as `YYYY-MM-DD: decision (why)`.

Close with one line: "You're set for tomorrow. Get some rest."
