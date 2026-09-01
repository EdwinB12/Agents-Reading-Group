# Agents Reviewing Old Research Outputs

**Date:** 1 September 2026 · **Lead:** Joe Heffer

Session materials for the RSE agents reading group on pointing AI agents *backwards* at
the existing body of research outputs — published papers, code, and datasets — rather
than at new experiments.

## Overview

Two modes frame the session:

- **🔍 Audit** — finding errors, unreproducible results, inconsistencies, and mis-reported
  numbers in the published record.
- **💡 Discovery** — connections across papers, re-analysis of open data, and hypotheses
  nobody followed up.

The prompt was the *Nature* news piece
["AI agents are spotting decades-old errors in scientific papers"](https://doi.org/10.1038/d41586-026-02235-8)
(Stokel-Walker, 2026). Recurring theme throughout: finding candidate errors is cheap,
adjudicating them is not — the binding constraint is human triage capacity, plus the cost
of a false accusation.

## Contents

| Path | What it is |
| --- | --- |
| `slides.md` | The session deck — Marp Markdown |
| `slides.css` | `uos` Marp theme (University of Sheffield branding) |
| `references.bib` | BibTeX for everything cited in the deck |
| `images/` | Logo and slide assets |
| `docs/` | Background source material (see below) |

### `docs/`

- `agents-old-research-session-pack.md` — facilitator pack: 30-minute landscape tour, then
  a ~85-minute hands-on lab with report-back
- `ai-agents-reexamining-research-timeline.md` — historical timeline, DENDRAL (1965) through
  to 2026
- `ai-agents-error-detection-primer.md` — primer on statistical and scientific error detection
- `literature-based-discovery-primer.md` — primer on Swanson's ABC model and LBD
- `re-reading-the-record.html`, `machines-re-reading-the-record.html` — rendered
  standalone versions of the above narrative material

## Building the slides

Slides are [Marp](https://marp.app/) Markdown. Preview with the VS Code Marp extension, or
export with the Marp CLI:

```bash
marp slides.md --theme slides.css -o slides.html   # HTML
marp slides.md --theme slides.css --pdf            # PDF
```

## Practical activity

Pick one:

1. Point an agent at a small self-contained published repo (paper + data + figures) and ask
   it to reproduce one headline number or figure. Narrate where it succeeds, where it
   silently fudges, and where it gives up.
2. Ask an agent to check the internal consistency of the reported statistics in a short
   methods/results section, then manually verify a sample of its flags to estimate precision.
3. Sketch a two-agent design — a "finder" proposing possible errors and an independent
   "verifier" whose only job is to refute each flag — and discuss whether that lowers the
   false-positive rate enough to be useful.

## Discussion prompts

- What's the responsible workflow from "agent flags an error" to "correction/retraction",
  and who is in the loop?
- How do you keep the false-positive rate low enough that flags are worth acting on?
- How much of "review old research" is really just "can we rebuild the environment" — a
  problem RSEs have owned for a decade?
- Bigger payoff: finding *mistakes* in old work, or finding *missed insights*?
- What would we want an agent to check on our *own* past outputs before trusting it on
  someone else's?
- How far can agents genuinely extrapolate, rather than interpolate between existing results?
- Is fully autonomous agentic error-finding wanted, or wise?

## Related

- [Claude Science workbench](../../ideas/claude-science-workbench.md) — idea in this repo for
  a dedicated reviewer agent that verifies reported numbers against underlying code
- [Black Spatula Project](https://github.com/The-Black-Spatula-Project) — community effort
  using LLMs to find errors in published papers at scale
