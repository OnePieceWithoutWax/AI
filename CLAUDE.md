# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This is a documentation-only repository for storing markdown instruction files used to guide AI behavior across projects. There are no source files, build steps, or tests.

## Structure

- `Claude_markdowns/` — Markdown instruction files intended to be referenced or copied into other projects.

## Working in This Repo

All tasks here involve reading and editing markdown files. When adding or updating a file:

- Follow the existing format of the file being edited.
- Do not rename files unless explicitly instructed.
- Place new instruction files in `Claude_markdowns/`.

## Library Development

The ongoing work in this repo is expanding the instruction library. When adding or improving files:

- Every file targets a specific injection point (where Claude reads it), a specific tool, and a specific behavioral domain. Name accordingly: `[ai]_[tool]_[what].md`.
- Instructions should be opinionated and ready to use, not generic. Avoid obvious advice. If a rule could apply to any AI assistant in any context, it's too vague.
- Match the tone of existing files: concise, direct, actionable. No filler, no bullet-point padding.
- When a new injection point is identified (a new tool, a new settings location), create a new file for it rather than appending to an existing one.
- Bracketed placeholder sections `[like this]` are acceptable only where content is inherently application-specific and cannot be generalised.

## Respurces
table of contents for every Claude Code documentation page
read this to load the latest docs
https://code.claude.com/docs/en/claude_code_docs_map.md


## Project Summary

| File | Injection Point | What it covers |
|------|----------------|----------------|
| `claude_cowork_general_instructions.md` | Cowork global settings | Session behavior: scope management, file operation rules, logging format, and reporting standards for Cowork sessions. |
| `claude_code_global_instructions.md` | `~/.claude/CLAUDE.md` | Universal Claude Code behavior: response style, editing discipline, code standards, git safety, decision-making, and boundaries. |
| `claude_code_project_template.md` | `./CLAUDE.md` per project | Full project scaffold: stack, directories, commands, architecture, conventions, boundaries, and an optional Task Chunking section (PROGRESS.md workflow) — remove the chunking section for small projects. |
| `claude_web_custom_instructions.md` | claude.ai → Settings → Custom Instructions | Two-field content: who the user is (technical depth, preferences) and how Claude should respond (style, format, what to omit). |
| `claude_web_project_instructions.md` | claude.ai → Projects → Instructions | Per-project system prompt template: context, background knowledge, mode of assistance, constraints, and output preferences. |
| `claude_api_system_prompt.md` | Anthropic API `system` parameter | Base system prompt for any API-built application: role, behavior rules, output format, hard constraints, and application context. |