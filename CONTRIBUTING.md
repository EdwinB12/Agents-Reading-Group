# Contributing to Agents-Reading-Group

## Repo purpose and structure

This repo supports the RSE Agentic Reading Group — a fortnightly session where we read papers, demo tools, and run exercises related to AI agents. The repo has two main areas:

```
sessions/   — planned session content (agenda, background reading, activities)
ideas/      — lightweight proposals for future topics
```

## Adding a session plan

Session files live in `sessions/` and follow this naming convention:

```
sessions/YYYY-MM-DD-short-slug.md
```

Use the session date, not the date you created the file.

### Required sections

Every session file should include:

| Section | Content |
|---------|---------|
| **Overview** | 2–4 sentences on the topic and why it matters now |
| **Background reading** | Ordered list of links to read before the session |
| **Timed agenda** | Table with time blocks, activity, and who leads |
| **Practical activity** | Hands-on exercise for the group (≥15 min) |
| **Discussion prompts** | 4–6 questions to structure the final segment |

See [`sessions/2026-03-31-nemoclaw-openshell.md`](sessions/2026-03-31-nemoclaw-openshell.md) for a complete example.

Once your file is ready, update the Schedule table in `README.md` and open a PR.

## Submitting an idea

1. Copy the template from [`ideas/README.md`](ideas/README.md).
2. Create a new file: `ideas/YYYY-MM-DD-short-slug.md`.
3. Fill in the title, suggested format, why it's interesting, and any relevant links.
4. Open a PR — ideas don't need to be complete or even have a date in mind.

## Branch and PR conventions

- Branch names: `add-<slug>` for new sessions/ideas, `fix-<slug>` for corrections.
- Commit message style: `feat:`, `fix:`, `docs:` prefix (e.g. `feat: add session plan for tool-use evals`).
- PR description: briefly explain what the session/idea covers and why you think it would suit the group.
- One session or idea per PR keeps reviews focused.
