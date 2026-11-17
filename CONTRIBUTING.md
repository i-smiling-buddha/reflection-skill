# Contributing

Thanks for helping improve Reflection Skill.

## Before opening a pull request

1. Describe the recreation problem your change solves (a missing step, a target type, an unclear rule).
2. Keep the clean-room rules intact: changes must never tell an agent to copy code, assets, copy or branding, bypass logins or paywalls, scrape, or use private APIs.
3. Keep `skills/reflection/SKILL.md` as one self-contained file that works in any Agent Skills tool.
4. Label anything that is a heuristic or estimate as such, the same way the skill labels findings.
5. If you adapt text from another project, check its licence and add it to `THIRD_PARTY_NOTICES.md`.

## Bug reports

Please include:
- The AI agent and version you used (Claude Code, Codex, Copilot, Gemini CLI, Cursor…)
- The track and mode (Lite / Full / Product, Clean room / Deep)
- What you asked, what the agent did, and what you expected
- The relevant part of the `recreate/` folder, with anything private removed

Do not upload passwords, API keys, private screenshots, or another company's code. A short redacted description is preferred.

## Pull requests

Keep changes focused, update both `README.md` and `README.hi.md` when behaviour changes, and explain how you tested the change with a real agent.
