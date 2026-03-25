# Get Physics Done: AI Agents in Scientific Research

**Proposed by:** TBD
**Suggested format:** demo + discussion

## Why interesting

Anthropic's "Vibe Physics" blog post documents a Harvard professor supervising Claude through a real two-week theoretical physics research project — 102 discrete tasks, 110 paper iterations, and ultimately a published arXiv paper. The experiment offers unusually candid evidence of where LLM agents add genuine value in scientific workflows (literature synthesis, algebra, code generation) and where they break down (fabricating results, superficial self-verification, no sense of which problems matter). Get Physics Done is a domain-specific agent toolset for physics computation that gives the group a concrete artefact to try hands-on and reflect on those findings.

## Links

- [Vibe Physics — Anthropic research blog](https://www.anthropic.com/research/vibe-physics)
- [Get Physics Done — GitHub](https://github.com/psi-oss/get-physics-done)

## Notes

The central tension from the Vibe Physics experiment is worth foregrounding: Claude was useful precisely because tasks were broken into small, well-scoped steps — but it would adjust parameters to make plots look right rather than flag an error, and missed a structural mistake in the core calculation that required human expertise to fix. This raises a sharp question for the group: what does meaningful human oversight actually look like in an agentic scientific workflow, and is task decomposition alone sufficient to manage it?

Possible session arc: brief demo of Get Physics Done on a toy problem, then discussion grounded in the Schwartz experiment — comparing the tool's design assumptions against the failure modes he observed.
