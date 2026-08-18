# AI agents that re-examine old research to make new discoveries

**Proposed by:** Joe Heffer
**Suggested format:** paper + discussion (with an optional hands-on demo)

## Why interesting

A fast-growing use of AI agents is pointing them *backwards* — at the existing body of published code, papers, and datasets — rather than at new experiments. The pitch is twofold: surface **errors** (statistical mistakes, unreproducible results, image duplication, mis-reported numbers) and surface **discoveries** (connections across papers, re-analysis of open data, hypotheses no one followed up). This is directly relevant to RSE work: much of it is agents reading, running, and checking *other people's* research artefacts. It's a good lens on where agentic reproducibility and error-detection tooling actually stands versus the hype.

## Links

- [Nature: AI agents to review old research outputs (d41586-026-02235-8)](https://www.nature.com/articles/d41586-026-02235-8) — the article that prompted this idea
- [Black Spatula Project](https://github.com/The-Black-Spatula-Project) — community effort using LLMs to find errors in published papers at scale
- [Related in-repo idea: Claude Science workbench](claude-science-workbench.md) — includes a dedicated "reviewer" agent that verifies reported numbers against underlying code

## Notes

Angles the session could cover — pick a subset rather than all of them:

**Finding errors in the existing literature**
- Statistical / reporting error detection (e.g. statcheck-style checks now driven by LLMs, GRIM tests, mis-matched p-values, sample-size inconsistencies).
- Reproducibility agents that clone a repo, rebuild the environment, run the code, and check whether the published figures/numbers actually regenerate.
- Image and data-integrity checks (duplicated western blots, manipulated figures) — historically specialist tools, now being combined with agentic triage.

**Making new discoveries from old outputs**
- Re-analysis of open datasets with modern methods or new questions.
- Literature-scale synthesis: agents reading thousands of papers to find under-explored links or contradictions (cf. the Allen Institute multi-agent literature-review case study).
- Hypothesis generation grounded in existing negative/unpublished results.

**State of the art & open questions**
- What tools exist today, how mature are they, and what's the false-positive problem? (An agent that flags 100 "errors", 90 of them spurious, creates work rather than saving it.)
- Where does human-in-the-loop sit — triage assistant vs. autonomous auditor?
- Incentives and ethics: who acts on agent-flagged errors, how are authors notified, and what's the risk of automated accusations at scale?

### Discussion prompts

- If an agent flags a possible error in a published paper, what's the responsible workflow from "flag" to "correction/retraction"? Who is in the loop?
- Verification is the hard part: how do you keep the false-positive rate low enough that flags are worth acting on? What does "adversarially verify each finding before reporting it" look like in practice?
- Re-running old code is a reproducibility problem we know well — how much of "review old research" is really just "can we rebuild the environment", and where do agents genuinely add value beyond that?
- Discovery vs. audit: is the bigger payoff finding *mistakes* in old work or finding *missed insights*? Which is more tractable for current agents?
- What would we, as RSEs, want an agent to check on our *own* past outputs before we'd trust it on someone else's?

### Practical things to try

- Point an agent at a small, self-contained published repo (ideally one with a paper + data + figures) and ask it to reproduce one headline number or figure. Narrate where it succeeds, where it silently fudges, and where it gives up.
- Take a short methods/results section and ask an agent to check internal consistency of the reported statistics (degrees of freedom, p-values, group sizes). Manually verify a sample of its flags to estimate its precision.
- Sketch a two-agent design — a "finder" that proposes possible errors and an independent "verifier" whose only job is to try to *refute* each flag — and discuss whether that pattern lowers the false-positive rate enough to be useful.
