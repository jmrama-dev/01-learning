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
  <course-name>/Module-XX/
  ```
- **Provider folder with multiple courses** (e.g. `02-Anthropic`): each course gets its own subfolder under the
  provider, so new courses can be added as siblings without touching existing ones:
  ```
  <provider-name>/<Course-Name>/
  ```
  Current example: `02-Anthropic/Claude-Code-101/`. Content lives directly inside the course folder — only add
  `Module-XX/` subfolders within it if that specific course is naturally split into numbered modules worth
  separating; don't add them by default.

Each course/module contains a `reflections.md` with three prompts to fill in after finishing it:
- ¿Qué aprendí? (What did I learn?)
- ¿Qué me costó entender? (What was hard to understand?)
- ¿Cómo podría usar esto en un proyecto mío? (How could I use this in my own project?)

When adding a new course: if it belongs to a provider that already hosts multiple courses (like Anthropic), add a
new `<Course-Name>/` subfolder under that provider's folder. If it's a new provider/instructor with a single
course, follow the flat `<course-name>/Module-XX/` pattern like Andrew Ng. Either way, include a `reflections.md`
unless the user says otherwise.

## Notes / learning log (`01-Notes/`)

`01-Notes/` is the public, ongoing core of the repository — the learning log. Entries are dated files
named `YYYY-MM-DD-slug-descriptivo.md`.

- Recommended template (not mandatory — omit any section without real content, never fill one in
  just to keep the shape): `Qué hice hoy` / `Qué aprendí` / `Ideas clave` / `Qué me costó entender`
  (only if there's real evidence of a difficulty) / `Próximos pasos` (only if reasonably inferable). Not
  every entry is a daily recap — conceptual explanations, reflections, or problem analyses should use
  whatever structure fits the content instead.
- Preserve the user's own voice and words when they already exist (e.g. from `reflections.md`,
  `resumen.md`). Never invent reflections, difficulties, or learnings that aren't backed by real content.
- When creating a new public learning-log entry, update two places manually (no scripts/automation):
  - `01-Notes/README.md` — the full chronological index (add date, title, link; reverse-chronological
    order, most recent first).
  - The "Últimas notas" section in the root `README.md` — trim to the 3-5 most recent entries.

## Working in this repo

- Keep new notes/exercises in Spanish, matching the existing content, unless the user asks for a specific piece in English.
- Since this is a learning log, prefer preserving the user's own words in reflections over rewriting them — only fix clarity/grammar if asked.
- If a module introduces runnable code (e.g. a Python/Jupyter exercise), add the actual build/lint/test commands for that subproject here once they exist — do not invent commands prematurely.
