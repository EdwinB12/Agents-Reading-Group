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

## Candidate toy problems

Problems are ranked by suitability for a live demo: well-scoped, visually rewarding, and exercise GPD's derivation + verification loop.

### Tier 1 — recommended (fits in 1–2 h, strong connection to session themes)

| Problem | Domain | Why it fits |
|---------|--------|-------------|
| **Damped harmonic oscillator with forcing** | Classical mechanics | Analytical + numerical solutions to compare; resonance plot is intuitive for a mixed audience; easy to introduce a deliberate sign error and test whether GPD catches it — directly probes the self-verification failure mode |
| **Two-body orbital mechanics (Kepler problem)** | Celestial mechanics | Classic RK4 integration; generates visually compelling orbital plots; conservation of energy and angular momentum provide natural verification checkpoints |
| **Ballistic pendulum** | Collision physics | Two-phase problem (momentum conservation → energy conservation); clean symbolic chain that illustrates how GPD links derivation steps |

### Tier 2 — good alternatives (require more setup or 1.5–2 h)

| Problem | Domain | Notes |
|---------|--------|-------|
| Double pendulum chaos | Nonlinear dynamics | Demonstrates Lyapunov exponents and sensitive dependence; richer but may be ambitious for one hour |
| 1D wave equation (finite difference) | PDEs / wave physics | Good for CFL stability analysis; needs 1.5–2 h |
| 1D heat diffusion | PDEs / heat transfer | Simpler PDE; useful contrast to wave equation (parabolic vs. hyperbolic) |
| Electrostatics: point charge field lines | Electromagnetism | Contour and vector field visualisation; purely superposition so symbolic path is clean |
| Ideal gas statistical mechanics | Thermodynamics | Partition function derivation; less immediately visual but rich verification story |

**Suggested primary demo:** damped harmonic oscillator — fits in ~30 min, clear verification moments, and the resonance plot lands well with non-specialists. Two-body orbital mechanics works well as an extended group exercise if time allows.
