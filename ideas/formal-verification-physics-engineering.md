# Lean for physics and engineering: formal verification as a "unit test" for agents

**Proposed by:** Joe Heffer
**Suggested format:** discussion (with a short demo / exercise)

## Why interesting

Lean is already used to formalise mathematics so that an agent's output can be machine-checked, which works like a unit test for a proof. Lanyon, a company that has just launched, says it is doing the same for physics and engineering: a neurosymbolic agent that generates formally verified scientific code and proofs. If that approach works, it changes what "trust the agent's output" means for research software. We need to discuss what it means for agents (verifiable tool use, a hard reward signal, a check that doesn't depend on the model's self-assessment) and for research (what counts as a verified result, and who checks that the specification matches the science).

## Links

- [Lanyon: Welcome (blog post)](https://lanyon.ai/blog/welcome/) — the post that prompted this idea
- [Lean 4 documentation](https://leanprover.github.io/lean4/doc/) — background on the proof assistant
- [Related in-repo idea: Harmonic Aristotle](mathematics-harmonic-aristotle.md) — the maths-side counterpart (Lean 4 proofs of research-level results)
- [Related in-repo idea: Get Physics Done](get-physics-done.md) — agents doing physics without a formal check
- [Related in-repo idea: Agent benchmarks and evals](agent-benchmarks-and-evals.md) — verification as an eval signal

## Notes

**What Lanyon claims** (from the announcement; not independently verified)

- A neurosymbolic agent with a proprietary domain-specific language for mathematics and physics. Symbolic algorithms expand a specification into code and proof together, rather than the LLM writing each separately.
- This is aimed at "misformalization", where the formal statement and the implementation drift apart. The post says the design makes this impossible by construction.
- Initial target domains are aerospace engineering, space and atmospheric propulsion, and nuclear energy.
- Lower compute cost than frontier models and very fast proof generation.
- It builds on proof assistant languages (Lean, Rocq, Agda).
- The authors state the main open problem themselves: syntactic correctness is guaranteed, but *semantic* correctness (does the specification capture what the user actually meant?) is still a research question.

**Questions to bring**

- A verified proof only certifies the specification. Where does the physics come from, and who validates the model (units, boundary conditions, modelling assumptions, discretisation)?
- Is this verification of code, of mathematics, or of the physical claim? How do those differ for a CFD solver or a reactor simulation?
- Does a proprietary DSL help or hurt reproducibility and auditability compared with open Lean/mathlib?
- What would we want from this as RSEs: verified numerical kernels, verified units and dimensional analysis, verified refactors of legacy scientific code?
- Are there other efforts in this space (e.g. Lean-based physics libraries, verified numerics, property-based testing)? The proposer only found this one, so please add others.
- What happens to the agent loop when a hard pass/fail verifier is available? Compare with test suites, linters and LLM-as-judge.

**Prerequisites:** none; skim the Lanyon post and the Harmonic Aristotle idea beforehand.
