# Reflection · प्रतिबिंब (Pratibimb)

**One agent skill that studies any website, app, game or shipped software, and helps you build your own, better version of it — clean-room.**

*Like the original in what it does, never the original itself.*

Free, MIT, a single `SKILL.md`. Works in any tool that reads the open [Agent Skills](https://agentskills.io) format: Claude, Claude Code, OpenAI Codex, GitHub Copilot, Gemini CLI, Cursor and more.

## What it does

| Track | You give it | You get |
|---|---|---|
| **Lite** (no install) | screenshots / screen recordings / public pages | checklist, findings table, data model, and a "Build this" spec to paste into Base44, Lovable, Claude or ChatGPT |
| **Full** | a target and a goal | recon → architecture → design tokens → build → backend → tests → parity score → refine loop |
| **Product** | a target you want to sell a better version of | Full, plus real-review analysis, fix plan, positioning, rebrand, landing page, store listing and a gated deploy |

Every finding is labelled **OBSERVED**, **DERIVED**, **INFERRED** or **UNKNOWN**, with its source. Nothing is called complete while questions are open.

### Two modes

- **Clean room** (default): works only from what a normal user can see.
- **Deep**: also reads inside a shipped artifact (binary, APK, ASAR, JS bundle, firmware) through [REA](https://github.com/morluto/rea) or [Craft Anything](https://github.com/storytold/craft-anything) tools — only for your own software, open source, or where the licence/law allows it. Findings inform behaviour; no decompiled code or assets go into your build.

## Install

**Claude (app):** paste this repo's link into a chat and ask Claude to install the skill, or upload `skills/reflection/SKILL.md` in Settings → Skills.

**Claude Code (plugin):**

```
/plugin marketplace add i-smiling-buddha/reflection-skill
/plugin install reflection-skill@reflection-skill
```

**Any Agent Skills tool:** copy the `skills/reflection` folder into that tool's skills folder:

| Tool | Folder |
|---|---|
| Claude Code | `~/.claude/skills/` or `.claude/skills/` |
| Codex, Copilot, Gemini CLI, Cursor | `.agents/skills/` (each also has its own: `.github/skills/`, `.gemini/skills/`, `.cursor/skills/`) |

```bash
git clone https://github.com/i-smiling-buddha/reflection-skill.git
cp -r reflection-skill/skills/reflection ~/.claude/skills/
```

**Chat without skill support:** paste the whole `SKILL.md` at the top of the chat. The Lite track works fully this way.

## How to use

```
Recreate <app / URL> — Lite track, here are my screenshots.
Recreate the booking flow of <app> as a Next.js app.
What do users hate about <app>? (runs the review analysis on its own)
```

Work is kept in a `recreate/` folder in your project (brief, plan, evidence ledger, handoff, recon map, `features.csv`), so long jobs can be resumed by any agent.

## The rules it enforces

- Public sources and your own account only. No bypassing logins, paywalls or CAPTCHAs; no scraping; no load-testing the original.
- Rebuild features and flows, never code, assets, logos, names, copy, colours or content.
- Official public APIs with your own keys only.
- No invented reviews, quotes, numbers or check results.
- You create accounts and handle money; nothing goes live without your go, and never before the rebrand sweep is clean.
- No deceptive look-alikes, gambling apps, or anything that harms a private person.

This is general information, not legal advice. If money is on the line, have a trademark/IP lawyer check before launch.

## Credits

Reflection is an original rewrite that merges the methods of four MIT-licensed works — thank you to their authors:

- [REA](https://github.com/morluto/rea) by morluto — evidence-first reverse-engineering method
- [Craft Anything](https://github.com/storytold/craft-anything) by the ArtCraft team — Study → Build → Check → Ready loop, Clean room / Deep modes
- [Replica skill](https://github.com/Jakeschincariol/replica-skill) by Jake Schincariol — the recon-to-deploy pipeline
- "Reverse engineer Apps (no install)" — a public Notion distillation of REA's method

Full licence texts: [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).

## License

MIT © 2026 Smiling Buddha
