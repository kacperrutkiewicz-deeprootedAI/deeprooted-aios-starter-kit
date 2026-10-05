# DeepRooted AIOS Starter Kit

Your own AI operating system: one folder that holds who you are, how your business runs, and the skills you use every day. Open it in Claude or ChatGPT and your AI already knows you.

No coding needed. Works with any AI that reads an `AGENTS.md` file (a plain instructions file in this folder). Built for the free course on YouTube and the DeepRooted Skool community.

## Quick start

1. **Get the kit** (pick one):
   - `git clone https://github.com/kacperrutkiewicz-deeprootedAI/deeprooted-aios-starter-kit.git`
   - On GitHub, click **Code > Download ZIP**, then unzip it
   - Download the zip from the DeepRooted Skool community
2. **Open the folder** in your AI app:
   - **Claude Desktop:** the **Code** tab (plain Chat and Cowork don't read this folder's instructions)
   - **ChatGPT desktop app:** the **Codex** tab, then **New project**, and add this folder
3. **Type `/onboard`** and answer the questions. When it's done, your AI knows you.

Check it's working anytime: type `aios check`. You should see `AIOS online` plus your name and your #1 priority.

## What's inside

| Folder            | What it holds                                                                     |
| ----------------- | --------------------------------------------------------------------------------- |
| `AGENTS.md`       | The instructions every AI reads at the start of a session                         |
| `context/`        | Who you are, your business, customers, goals, priorities, voice, tools, decisions |
| `projects/`       | One folder per project                                                            |
| `references/`     | Docs you reuse, plus `voice-samples/` of your writing                             |
| `brand-assets/`   | Logo, colors, fonts, photos                                                       |
| `.agents/skills/` | Your skills (the home folder)                                                     |
| `.claude/skills/` | A mirror of your skills so Claude finds them too                                  |

## Skills

| Skill              | What it does                                                                    | Credit      |
| ------------------ | ------------------------------------------------------------------------------- | ----------- |
| `/onboard`         | Interviews you and fills in your context files                                  | Nate Herk   |
| `/plan-tomorrow`   | Builds tomorrow's plan from your priorities                                     |             |
| `/update-aios`     | Refreshes stale context and tunes up your setup                                 |             |
| `/grill-me`        | Pressure-tests a plan with hard questions                                       | Matt Pocock |
| `/session-handoff` | Saves where you left off so the next session picks it up                        |             |
| `/create-skill`    | Turns a task you repeat into a new skill                                        |             |
| `/sync`            | Keeps the two skills folders matching                                           |             |
| `/os-audit`        | Checks your AIOS for stale, broken, or bloated files                            |             |
| `/aios-audit`      | Scores your setup on the Four Cs™ (Context, Connections, Capabilities, Cadence) | Nate Herk   |
| `/level-up`        | Finds your next automation with the Three Ms™ (Mindset, Method, Machine)        | Nate Herk   |

## Troubleshooting

- **AI doesn't know your setup?** Type `aios check`. If it fails, look for a stray `CLAUDE.md` in this folder or any folder above it. A `CLAUDE.md` stops Claude from reading `AGENTS.md`.
- **Claude still not reading it?** In the Code tab, type `/config` and set **Project instructions** to `claude-md-or-agents-md`.
- **ChatGPT's Codex tab asks permission to edit `.agents`?** Approve it. That's your skills folder, and Codex protects it by default.
- **Stuck?** Post in the DeepRooted Skool community, or book a 1:1 setup session there.

## Credits

- **Nate Herk** and his AIS-OS: `/onboard`, `/aios-audit`, and `/level-up` started from his work. [AIS-OS on GitHub](https://github.com/nateherkai/AIS-OS). Join his community: [AI Automation Society (free)](https://www.skool.com/ai-automation-society/about?ref=6d792349a24746cba3127867f850d497) and [AI Automation Society Plus](https://www.skool.com/ai-automation-society-plus/about?ref=6d792349a24746cba3127867f850d497).
- **Matt Pocock:** `/grill-me` comes from his [skills repo](https://github.com/mattpocock/skills) (MIT).

## Learn more

- YouTube: [@kacperrutk](https://www.youtube.com/@kacperrutk)
- DeepRooted Skool community (free course, checklists, help): [join here](https://www.skool.com/ai-automation-network-2970/about)

## License

MIT. See `LICENSE`. Built by Kacper Rutkiewicz at DeepRooted AI.
