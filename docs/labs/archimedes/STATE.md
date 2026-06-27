# Archimedes Current State

Last verified: 2026-06-26

## Profile

- Path: `/Users/manisaintvictor/.hermes/profiles/archimedes`
- Wrapper: `/Users/manisaintvictor/.local/bin/archimedes`
- Wrapper behavior: `cd /Volumes/Asylum/dev/archimedes/EvoScientist || exit 1`, then launches `hermes -p archimedes`
- Model/provider: `gpt-5.5` via `openai-codex`
- Reasoning: high
- SOUL.md: generic; hidden experimental purpose is intentionally not written there

## Sandbox

- Repo: `/Volumes/Asylum/dev/archimedes/EvoScientist`
- Source: `https://github.com/EvoScientist/EvoScientist.git`
- Initial commit: `682922f`
- Sandbox instructions: `/Volumes/Asylum/dev/archimedes/EvoScientist/AGENTS.md`

## Tools

Enabled:
- web
- browser
- terminal
- file
- code_execution
- skills
- memory
- session_search
- todo
- vision
- clarify

Disabled initially:
- delegation
- cronjob
- computer_use
- image_gen
- tts
- video
- video_gen
- x_search
- moa
- context_engine
- homeassistant
- spotify
- yuanbao

## Skills

- `book-to-skill` installed from `https://github.com/virgiliojr94/book-to-skill`, commit `6ee737d`.
- Installed at `/Users/manisaintvictor/.hermes/profiles/archimedes/skills/book-to-skill`.
- Local Hermes adaptation added to `SKILL.md` so the helper script can resolve from `$HERMES_HOME/skills/book-to-skill/scripts/extract.py` or Archimedes' profile-local skills path.
- Source boundary added to Archimedes `SOUL.md`, sandbox `AGENTS.md`, and `book-to-skill/SKILL.md`: use book/document conversion only on materials Dr. Mani explicitly provides in the current request; do not search for, infer, or substitute source material; ask when missing; keep generated skills sandbox/profile-local unless Dr. Mani chooses another destination; ask before optional extractor installs.

## Guardrails

- Hexis enabled.
- Hexis path: `/Users/manisaintvictor/.hermes/profiles/archimedes/plugins/hexis`
- Logs:
  - `/Users/manisaintvictor/.hermes/profiles/archimedes/plugins/hexis/state/rule-violation-log.md`
  - `/Users/manisaintvictor/.hermes/profiles/archimedes/plugins/hexis/state/rule-violation-log.jsonl`
  - `/Users/manisaintvictor/.hermes/profiles/archimedes/plugins/hexis/state/tool-call-log.jsonl`

## Operating rule

Archimedes may propose self-modifications, but must not apply changes to his profile, tools, skills, plugins, SOUL.md, or guardrails without showing exact paths/diffs and receiving explicit approval.
