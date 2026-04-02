# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

---

## Project Overview

[One sentence describing what this project does.]

---

## Stack

- Language: [e.g. Python 3.12, TypeScript 5]
- Framework: [e.g. FastAPI, Next.js, none]
- Database: [e.g. PostgreSQL, SQLite, none]
- Key dependencies: [e.g. pydantic, sqlalchemy, react-query]

---

## Key Directories

- `src/` — [description]
- `tests/` — [description]
- `[other]/` — [description]

---

## Commands

| Task | Command |
|------|---------|
| Install | |
| Build | |
| Test — all | |
| Test — single file | |
| Lint | |
| Format | |

---

## Architecture

[One paragraph: what this system does and how the major components fit together.]

[Key data flows or request paths worth knowing — the kind of thing that takes a day to figure out from reading the code alone.]

---

## Conventions

[Non-obvious conventions not derivable from reading the code — naming patterns, state management approach, API contract rules, folder ownership, etc.]

---

## Gotchas

[Environment setup quirks, known footguns, or things that have caused confusion in the past.]

---

## Boundaries

Do not modify the following without explicit confirmation:
- `[e.g. src/core/config.py]`
- `[e.g. migrations/]`

Do not:
- Add new dependencies without confirmation.
- Delete files — mark as deprecated and ask.
- Modify shared interfaces without confirming downstream impact.

---

<!--
  ============================================================
  TASK CHUNKING
  Remove this entire section for small or single-file projects.
  Keep it for tasks that will span multiple files or sessions.
  ============================================================
-->

## Task Decomposition

For any task spanning >1 file or requiring >50 LOC:

1. Check for `PROGRESS.md` — if it exists, resume from the **Active** section.
2. Write or update the plan in `PROGRESS.md` before editing any files.
3. Implement one module at a time.
4. After each module: run tests, run linter, commit with a descriptive message, update `PROGRESS.md`.

### Definition of Done (per chunk)

Before marking a chunk complete and committing:
- All tests pass: `[insert test command]`
- Linter passes: `[insert lint command]`
- All new functions have type hints and docstrings.
- No debug code or uncommitted TODOs in edited files.
- Changes committed with a descriptive message.

### PROGRESS.md format

```markdown
# PROGRESS.md

## Active
<!-- Current chunk being worked on -->

## Completed
<!-- Finished chunks with dates, e.g. "- [x] DataLoader — 2026-03-24" -->

## Backlog
<!-- Remaining chunks in priority order -->

## Blockers
<!-- Ambiguities requiring human input — stop and surface these rather than assuming -->
```

## When Uncertain

If requirements are ambiguous or a decision has significant architectural impact:
- Write the question under **Blockers** in `PROGRESS.md`.
- Stop and surface it rather than assuming.
- Do not silently make a choice that affects files outside the current chunk.

<!--
  ============================================================
  END TASK CHUNKING
  ============================================================
-->
