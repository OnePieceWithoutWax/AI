# Claude Code — Global Instructions

These instructions apply to every project opened in Claude Code.

---

## Response Style

- Lead with the answer or action. Skip preamble, filler words, and trailing summaries.
- Do not restate the user's request before responding.
- No emoji unless explicitly asked.
- Use markdown only when it will render. Prefer plain text in raw terminal contexts.

---

## Editing Code

- Read every file before editing it. Never propose changes to code you haven't seen.
- Do not add features, refactors, comments, or docstrings beyond what was explicitly asked.
- Do not add error handling for scenarios that cannot occur. Trust internal code and framework guarantees.
- Prefer editing existing files over creating new ones.
- Three similar lines of code is better than a premature abstraction.
- Do not add backwards-compatibility shims, re-exports, or `_unused` variables for removed code — just delete it.

---

## Code Standards

- Type hints required on all functions.
- Docstrings required on all public functions and classes.
- No debug code or print statements in committed files.
- No TODOs left in edited files without a corresponding backlog entry.

---

## Git

- Create new commits rather than amending, unless explicitly told to amend.
- Never skip hooks (`--no-verify`) or bypass signing unless explicitly instructed.
- Stage files by name — avoid `git add -A` without reviewing what would be included.
- Confirm before any destructive operation: `reset --hard`, `branch -D`, `push --force`, `checkout .`.
- Never force-push to `main` or `master`.

---

## Decision-Making

- When scope is ambiguous, do less and confirm rather than interpret broadly.
- For irreversible actions, state what you are about to do and wait for confirmation.
- On failure: read the error and diagnose before changing approach. Do not retry the identical action blindly.
- Do not ask clarifying questions for straightforward tasks — just execute.
- Do not propose follow-up improvements or refactors after completing what was asked.
- For tasks spanning more than one file: check for a `PROGRESS.md` first and resume from it if it exists. Write the plan before touching files.
- When a decision has significant architectural impact or requirements are ambiguous, surface it as a blocker rather than silently assuming. Do not make choices that affect files outside the current scope without confirmation.

---

## Boundaries

- Do not add new dependencies without confirmation.
- Do not delete files — mark as deprecated and ask.
- Do not modify shared interfaces without confirming downstream impact.
