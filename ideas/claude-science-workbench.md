# Claude Science: an AI workbench for scientists

**Proposed by:** Joe Heffer
**Suggested format:** demo + discussion

## Why interesting

Anthropic just launched Claude Science (beta, ~1 July 2026) — an AI workbench that wraps a coordinating agent, 60+ domain skills/connectors, and MCP extensibility around real research workflows (genomics, proteomics, structural biology, cheminformatics). It's a good case study for several things this group cares about: multi-agent coordination (a generalist agent that spins up specialists and a dedicated "reviewer" agent for QC), agentic compute orchestration with human-in-the-loop approval, and "skills" as reusable, persisted pipelines — all applied to a domain (reproducible science) where auditability really matters.

## Links

- [Claude Science: an AI workbench for scientists (Anthropic announcement)](https://www.anthropic.com/news/claude-science-ai-workbench)
- [Claude Science beta (product page)](https://claude.com/product/claude-science)
- [Anthropic launches Claude Science, an AI workbench for the lab (The Next Web)](https://thenextweb.com/news/anthropic-claude-science-ai-workbench-scientists)

## Notes

What's happening under the hood, briefly:

- A generalist coordinating agent delegates to specialist sub-agents and to 60+ curated skills/connectors covering genomics, single-cell, proteomics, structural biology, and cheminformatics, backed by 60+ scientific databases (UniProt, PDB, Ensembl, etc.) and NVIDIA BioNeMo models (Evo 2, Boltz-2, OpenFold3).
- A separate **reviewer agent** checks citations and verifies that reported numbers/figures actually match the underlying code — a critic role rather than just a generator.
- **Compute is agentic but gated**: the system drafts a plan, asks before provisioning new resources, and submits jobs to the lab's own HPC (via SSH) or on-demand compute (Modal), scaling from one GPU to hundreds — but nothing costly happens without explicit sign-off.
- Every output carries an **auditable history** — code, environment, and full conversation context — so results can be traced back to exactly how they were produced.
- Labs can extend it via **MCP connectors** for proprietary data/pipelines, and save their own workflows as skills that persist across sessions.
- Case studies cited: Manifold Bio (target nomination), Allen Institute (automated multi-agent literature review across thousands of papers), UCSF Brain Tumor Center (~10x faster molecular epidemiology analysis).

### Discussion prompts

- The reviewer/critic agent pattern: how far does "a second agent whose only job is to catch the first agent's mistakes" generalise beyond science, e.g. to code review or data analysis agents we already build?
- What would "auditable history" (code + environment + conversation trace attached to every output) look like as a general requirement for agent frameworks, not just scientific ones?
- The compute-approval loop (plan → ask before spending → submit job) is a concrete pattern for agents that can trigger real-world cost or side effects. Where else should we be borrowing this "ask before you commit resources" pattern?
- Skills-as-reusable-pipelines that persist across sessions — how does this compare with our own experience writing and reusing Claude Skills in this repo/organisation?
- Is domain-specific curation (60+ pre-built skills/connectors) a scalable strategy, or does it just move the maintenance burden from "write the analysis" to "maintain the connector"?

### Practical things to try

- No beta access needed: read through the MCP connector approach described in the announcement and compare it with the MCP servers already wired into our own environment (e.g. the ChEMBL, Clinical Trials, and bioRxiv MCP tools available here) — same protocol, different domain.
- If anyone in the group has beta access, do a live demo of a small workflow (e.g. a cheminformatics compound search or a structure viewer walkthrough) and narrate what the coordinating agent is delegating vs. doing itself.
- As a group exercise, sketch what a "reviewer agent" would look like bolted onto one of our own existing coding or writing workflows — what would it check, and how would it flag/correct errors without just re-doing the original work?
