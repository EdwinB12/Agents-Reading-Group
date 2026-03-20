# CLAUDE.md — Agents-Reading-Group

## Repo purpose

This repo supports an RSE fortnightly reading group focused on AI agents. It holds session plans and topic ideas contributed by group members.

## Directory structure

```
sessions/   — one Markdown file per session
ideas/      — lightweight topic proposals
```

## sessions/ conventions

- File naming: `YYYY-MM-DD-short-slug.md` (use the session date)
- Required sections: Overview, Background reading, Timed agenda, Practical activity, Discussion prompts
- See `sessions/2026-03-31-nemoclaw-openshell.md` as the canonical example

## ideas/ conventions

- File naming: `YYYY-MM-DD-short-slug.md` (use today's date when creating)
- Template is defined in `ideas/README.md`
- Fields: title, proposed by, date added, suggested format, why interesting, links, notes

## README.md schedule table

Do NOT modify the Schedule table in `README.md` without explicit user confirmation. The table is maintained manually and changes affect the published group schedule.

## Commit message style

Follow the conventional-commits pattern seen in the repo history:

```
feat: <short description>
fix: <short description>
docs: <short description>
```

Examples from history: `feat: add session plan for NemoClaw & OpenShell (31/03/2026)`
