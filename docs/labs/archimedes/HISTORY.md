# Archimedes History

Append one entry after every meaningful Archimedes move: tool change, prompt/rule change, profile change, skill/plugin change, observed failure, recovery, or milestone.

## 2026-06-26 21:25 — Initial sandbox baseline

Operator:
- engineering

Intent:
- Create a controlled Archimedes profile sandbox for EvoScientist-grounded metacognitive/self-programming experiments while keeping the hidden purpose out of Archimedes `SOUL.md`.

Changed:
- Created Hermes profile `archimedes` at `/Users/manisaintvictor/.hermes/profiles/archimedes`.
- Created wrapper `/Users/manisaintvictor/.local/bin/archimedes`.
- Patched wrapper to `cd /Volumes/Asylum/dev/archimedes/EvoScientist || exit 1` before launching Hermes.
- Cloned `https://github.com/EvoScientist/EvoScientist.git` to `/Volumes/Asylum/dev/archimedes/EvoScientist`.
- Wrote sandbox rules to `/Volumes/Asylum/dev/archimedes/EvoScientist/AGENTS.md`.
- Wrote Engineering handoff/project notes under `/Users/manisaintvictor/.hermes/profiles/engineering/`.
- Enabled Hexis in Archimedes.
- Set initial tool surface.

Observed behavior:
- `archimedes` launches from the EvoScientist sandbox even when invoked from `/tmp`.

Evidence:
- Live cwd test returned `/Volumes/Asylum/dev/archimedes/EvoScientist`.
- `hermes profile show archimedes` showed model `gpt-5.5` via `openai-codex`.
- `archimedes tools list` showed research/local engineering tools enabled and delegation/cron/computer_use/media tools disabled.
- EvoScientist repo was on `main`, commit `682922f`.

Rollback:
- Restore `/Users/manisaintvictor/.local/bin/archimedes` to a plain `exec /Users/manisaintvictor/.local/bin/hermes -p archimedes "$@"` wrapper if the fixed sandbox cwd becomes undesirable.
- Disable Hexis with `archimedes plugins disable hexis` if it blocks legitimate early experiments.
- Remove `/Volumes/Asylum/dev/archimedes/EvoScientist` only after confirming no local work needs preserving.

Next:
- Ask Archimedes to map EvoScientist memory, skills, context editing, and scheduled-task architecture before making any self-modification.

## 2026-06-26 21:40 — Installed book-to-skill

Operator:
- engineering

Intent:
- Give Archimedes the requested document/book-to-skill capability from `https://github.com/virgiliojr94/book-to-skill`.

Changed:
- Cloned `https://github.com/virgiliojr94/book-to-skill` to `/tmp/book-to-skill-inspect` for inspection.
- Copied the repo into `/Users/manisaintvictor/.hermes/profiles/archimedes/skills/book-to-skill`.
- Patched Archimedes' installed `book-to-skill/SKILL.md` to include Hermes profile-local helper script candidates:
  - `$HERMES_HOME/skills/book-to-skill/scripts/extract.py`
  - `$HOME/.hermes/profiles/archimedes/skills/book-to-skill/scripts/extract.py`

Observed behavior:
- `archimedes skills list` reports `book-to-skill` as a local enabled skill.
- The extractor preflight runs successfully.

Evidence:
- Source commit: `6ee737d`.
- `archimedes skills list` output included `book-to-skill │ local │ enabled`.
- `python3 /Users/manisaintvictor/.hermes/profiles/archimedes/skills/book-to-skill/scripts/extract.py --check` reported ready fallbacks for common formats; Calibre missing only affects MOBI/AZW/AZW3.

Rollback:
- Remove `/Users/manisaintvictor/.hermes/profiles/archimedes/skills/book-to-skill`.
- Run `archimedes skills list` to confirm the skill is gone.

Next:
- If Archimedes uses this on technical PDFs, consider installing optional `docling` only after approval because it may be heavyweight.
- Keep generated skills sandbox-local unless Dr. Mani chooses another destination.

## 2026-06-26 21:50 — Added book-to-skill source boundary to Archimedes system

Operator:
- engineering

Intent:
- Make Archimedes' book/document conversion capability explicit in his system-level instructions while constraining it to sources Dr. Mani actually provides.

Changed:
- Updated `/Users/manisaintvictor/.hermes/profiles/archimedes/SOUL.md` with the profile-level document/book-to-skill operating boundary.
- Updated `/Volumes/Asylum/dev/archimedes/EvoScientist/AGENTS.md` with the sandbox-level `book-to-skill` boundary.
- Updated `/Users/manisaintvictor/.hermes/profiles/archimedes/skills/book-to-skill/SKILL.md` with an Archimedes-specific source boundary.

Observed behavior:
- `book-to-skill` remains installed and enabled for Archimedes.

Evidence:
- Readback confirmed the boundary in `SOUL.md`, `AGENTS.md`, and `book-to-skill/SKILL.md`.
- `archimedes skills list` still showed `book-to-skill │ local │ enabled`.

Rollback:
- Remove the added source-boundary paragraphs from the three changed files.

Next:
- When Dr. Mani hands Archimedes a book/document/path/URL, generated skills should stay Archimedes-local unless Dr. Mani explicitly chooses another destination.

## 2026-06-27 10:26 EDT — Added neutral Anbeeld writing guardrails

Operator:
- engineering

Intent:
- Give Archimedes the same writing preamble used by other profiles while preserving his book/document conversion boundary and not exposing hidden experimental framing.

Changed:
- Updated `/Users/manisaintvictor/.hermes/profiles/archimedes/SOUL.md` with a neutral `## Writing` section.
- Added an explicit conflict boundary: writing rules govern reader-facing prose only and do not override `book-to-skill` source-boundary rules or any conversion workflow boundary.
- Updated `/Users/manisaintvictor/.hermes/profiles/engineering/projects/archimedes/PROJECT.md` so future Engineering sessions know Archimedes has `writing`, `book-to-skill`, and `codebase-orientation` enabled.

Observed behavior:
- Archimedes has `writing` enabled alongside `book-to-skill` and `codebase-orientation`.
- The `writing` package is byte-identical to the global canonical Anbeeld package.
- No conflict found: `book-to-skill` controls conversion/source intake; `writing` controls prose quality for reader-facing outputs.

Evidence:
- `archimedes skills list` showed `book-to-skill`, `writing`, and `codebase-orientation` enabled.
- `diff -qr /Users/manisaintvictor/.hermes/skills/writing /Users/manisaintvictor/.hermes/profiles/archimedes/skills/writing` returned no differences.
- Readback of Archimedes `SOUL.md` showed `## Writing` plus the sentence that writing rules do not override `book-to-skill` source boundaries.

Rollback:
- Remove the `## Writing` section from `/Users/manisaintvictor/.hermes/profiles/archimedes/SOUL.md`.
- Remove `/Users/manisaintvictor/.hermes/profiles/archimedes/skills/writing` only if Dr. Mani wants Archimedes without the Anbeeld writing skill.

Next:
- Restart or start a fresh Archimedes session to load the updated `SOUL.md` and skill inventory.
