# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository purpose

This is a personal learning repository (notes/exercises, not a software product) where the user documents their
progress learning AI and software development. It also serves a public purpose: `01-Notes/` is the public, ongoing
core of the repository — a learning log on GitHub documenting what the user learns and builds around AI, Claude
Code, coding agents, APIs, MCP, and skills. Courses (`02-Anthropic/`, `03-Andrew-Ng-Agentic-AI/`) and
`04-Recursos-Creados/` are supporting categories around that core, not the main focus. Content is written in
**Spanish**. There is currently no build, lint, or test tooling — the repo holds course notes and will grow to
include exercises/small projects as courses progress.

## Structure

Two top-level organization patterns coexist, depending on whether the top-level folder is a single dedicated
course or a provider that hosts multiple courses:

- **Single-course folder** (e.g. `03-Andrew-Ng-Agentic-AI`): the course lives directly at the top level, modules
  go straight inside it:
  ```
  <course-name>/NN-Module/
  ```
  `Projects/` is a fixed, non-numbered exception inside a single-course folder — an open-ended container for
  hands-on projects built while taking the course, not a sequential module.
- **Provider folder with multiple courses** (e.g. `02-Anthropic`): each course gets its own subfolder under the
  provider, so new courses can be added as siblings without touching existing ones:
  ```
  <provider-name>/NN-Course-Name/
  ```
  Current example: `02-Anthropic/01-Claude-Code-101/`. Content lives directly inside the course folder — only add
  `NN-Module/` subfolders within it if that specific course is naturally split into numbered modules worth
  separating; don't add them by default.

Each course/module contains a `reflections.md` with three prompts to fill in after finishing it:
- ¿Qué aprendí? (What did I learn?)
- ¿Qué me costó entender? (What was hard to understand?)
- ¿Cómo podría usar esto en un proyecto mío? (How could I use this in my own project?)

When adding a new course: if it belongs to a provider that already hosts multiple courses (like Anthropic), add a
new `NN-Course-Name/` subfolder under that provider's folder. If it's a new provider/instructor with a single
course, follow the flat `<course-name>/NN-Module/` pattern like Andrew Ng. Either way, include a `reflections.md`
unless the user says otherwise.

### Naming conventions

- **Numbered folders** (top-level, courses, modules): `NN-Name-In-Kebab-Case` — two-digit prefix, hyphen
  separator (never a dot), title-cased words joined by hyphens. Applies at every level: `01-Notes`,
  `02-Anthropic/01-Claude-Code-101`, `03-Andrew-Ng-Agentic-AI/01-Module`.
- **Non-numbered, open-ended folders** (e.g. `Projects/`): keep as-is, no number — they aren't sequential.
- **Content files inside a course/module**: lowercase, kebab-case, no spaces. Fixed names by function:
  `reflections.md`, `resumen.md` (running notes/summary of the course or module), `key-concepts.md`,
  `cheatsheet.md`, `practical-cases.md`. Use these exact names — don't invent variants (`notes.md`,
  `Key Concepts.md`, etc.) for the same purpose.
- **Fixed exceptions** (never renamed, standard filenames): `README.md`, `CLAUDE.md`.
- **`01-Notes/` entries**: `YYYY-MM-DD-slug-en-kebab-case.md` (date-first, so chronological order matches
  alphabetical order).
- **`04-Recursos-Creados/` files**: `NN-slug-en-kebab-case`, no accents/spaces in the filename (the accented,
  human-readable title can live in the Markdown link text pointing to it).

## Notes / learning log (`01-Notes/`)

`01-Notes/` is the public, ongoing core of the repository — the learning log. Entries are dated files
named `YYYY-MM-DD-slug-descriptivo.md`.

Two indexes must be kept in sync by hand whenever a new entry is added (no scripts/automation):
`01-Notes/README.md` (the full chronological index) and the "Últimas notas" section of the root
`README.md` (trimmed to the 3-5 most recent entries).

For the full daily-note creation workflow (trigger, template, tone rules, exact index-update steps),
see the `nota-diaria` skill (`.claude/skills/nota-diaria/SKILL.md`).

## Working in this repo

- Keep new notes/exercises in Spanish, matching the existing content, unless the user asks for a specific piece in English.
- Since this is a learning log, prefer preserving the user's own words in reflections over rewriting them — only fix clarity/grammar if asked.
- If a module introduces runnable code (e.g. a Python/Jupyter exercise), add the actual build/lint/test commands for that subproject here once they exist — do not invent commands prematurely.
