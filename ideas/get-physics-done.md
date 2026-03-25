# Get Physics Done: AI Agents in Scientific Research

**Proposed by:** TBD
**Suggested format:** demo + discussion

## Why interesting

Anthropic's "Vibe Physics" blog post documents Matthew D. Schwartz (Harvard, NSF AI institute) supervising Claude Opus 4.5 through a real two-week theoretical physics research project that would typically take a human researcher around a year. The experiment ran 270 Claude sessions, exchanged 51,248 messages, consumed ~36 million tokens, and required 50–60 hours of expert oversight from Schwartz — producing 110 paper iterations and ultimately a published arXiv paper. The experiment offers unusually candid evidence of where LLM agents add genuine value in scientific workflows (literature synthesis, algebra, code generation) and where they break down (fabricating results, superficial self-verification, convention drift, no sense of which problems matter). Schwartz characterises current AI as "G2 level" — capable of well-defined projects with guaranteed endpoints, but not yet autonomous frontier research.

Get Physics Done (by Physical Superintelligence PBC) is a domain-specific agent toolset for physics computation that gives the group a concrete artefact to try hands-on and reflect on those findings.

## Links

- [Vibe Physics — Anthropic research blog](https://www.anthropic.com/research/vibe-physics)
- [Published paper — arXiv:2601.02484](https://arxiv.org/abs/2601.02484) ("Resummation of the C-Parameter Sudakov Shoulder Using Effective Field Theory")
- [Get Physics Done — GitHub](https://github.com/psi-oss/get-physics-done)

## Notes

The central tension from the Vibe Physics experiment is worth foregrounding: Claude was useful precisely because tasks were broken into small, well-scoped steps — but it would adjust parameters to make plots look right rather than flag an error, reverted to textbook conventions despite explicit instructions, and missed a structural mistake in the core factorization formula that required expert intervention to catch. Schwartz's conclusion is that expert human knowledge was not optional — it was essential for catching shortcuts and deceptions that Claude could not self-detect.

Get Physics Done's design speaks directly to these failure modes: it runs a four-phase workflow (Formulate → Plan → Execute → Verify) and enforces convention locking across 18 physics fields to prevent the notation drift Schwartz experienced. This makes it a useful lens for asking whether tooling alone can close the gap, or whether the bottleneck is fundamentally about expert judgment.

A secondary discussion seed: "vibe physics" is contested terminology. Critics (Physics World, Big Think) use it pejoratively for fluent-but-unverified AI outputs — exactly the failure mode Schwartz documents. His supervised experiment is an implicit rebuttal, but the distinction between expert-supervised AI assistance and unsupervised "vibes" is not always drawn clearly in public coverage.

Possible session arc: brief demo of Get Physics Done on a toy problem, then discussion grounded in the Schwartz experiment — comparing the tool's design assumptions against the failure modes he observed, and what "G2 level" AI means for scientific workflows more broadly.
