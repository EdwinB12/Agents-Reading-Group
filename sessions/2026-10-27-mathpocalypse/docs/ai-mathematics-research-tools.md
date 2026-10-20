# AI models and tools for mathematics research

Prepared 18 October 2026.

This summary covers models trained or fine-tuned for mathematics, agent systems built on general models, and the infrastructure around them, including the Open Math OS platform at openmathmodel.org. Performance figures are reported by the developers unless stated. Availability changes quickly, so check each project page before relying on it.

## Why these systems were designed

Language models write fluent proofs that may contain errors, and checking a research-level proof by hand is slow. The systems below respond to that problem in four ways.

* **Training against Lean 4.** Lean is a proof assistant that accepts a proof only if every step is valid. Its verdict gives a cheap and unambiguous reward signal, which makes reinforcement learning (RL) practical. The Seed-Prover authors make this argument directly, and Harmonic’s founding statement argues that verifiable reasoning is the route to trustworthy AI.
* **Learned verifiers for natural-language proofs.** Where mathematics is hard to formalise, a second model checks the first model’s reasoning (DeepSeekMath-V2).
* **Search with an automatic scorer.** For problems that ask for a construction, such as a good packing or a bound, an LLM proposes candidates and code scores them (AlphaEvolve).
* **Agent harnesses.** Single-shot generation fails on research problems, so newer systems split the work into planning, proving and verification, often with several provers in parallel (QED, Bolzano, Cogentic).

## Summary table

| System | Type | Availability | Main purpose |
|---|---|---|---|
| Open Math OS | Research workspace | Hosted app on third-party open models | Collaborative maths work with community-controlled data |
| DeepSeekMath-V2 | Natural-language prover and verifier | Open weights (Apache 2.0) | Olympiad-level proofs with self-checking |
| DeepSeek-Prover-V2 | Lean prover | Open weights | Formal proofs via subgoal decomposition |
| Goedel-Prover-V2 | Lean prover (8B, 32B) | Open weights | Strong formal proving at small model size |
| Kimina-Prover | Lean prover (72B preview, 7B distilled) | Open weights | RL-trained formal reasoning |
| Seed-Prover 1.5 | Agentic Lean prover | Open release not confirmed | Undergraduate to PhD-level formal proofs |
| AlphaProof | Lean prover trained by RL | Not public; access by application | Olympiad-level formal proofs |
| AlphaEvolve | Evolutionary coding agent | Not public; academic access planned | Discovering constructions and bounds |
| Aristotle (Harmonic) | Lean prover and autoformaliser | Commercial | Verified proofs from natural-language input |
| AxiomProver and AXLE | Lean prover; hosted Lean service | Prover closed; AXLE free to use | Formal proofs; proof verification at scale |
| Gauss (Math Inc.) | Autoformalisation agent | Commercial, beta | Turning papers into large Lean libraries |
| Numina-Lean-Agent | Agent harness for Lean | Open source | Formal proving with a general coding agent |
| QED | Multi-agent proof system | Open source | Proofs for open research problems |
| Bolzano | Multi-agent proof system | Open source | Large-scale open-problem solving |

## Open Math OS and the Open Math Model initiative

**What it is.** Open Math OS is a web workspace from the Open Math Model initiative, which the SAIR Foundation started. It combines a chat interface, a cloud machine for each project, and team collaboration. It is a platform. The pages I read do not describe a maths-trained model released by the initiative itself.

**Why it exists.** The initiative states that the mathematical community should own its data and decide how it is used. Projects are private by default, and training on a team’s work needs explicit consent on terms agreed in advance. The initiative also says it intends to build open models with open weights, published training methods and reproducible evaluations. Its first phase targets everyday work such as understanding arguments, checking references, exploring examples, writing code and formalising proofs.

**How it works.**

* Users choose a model from a list of general open models (Kimi K3, DeepSeek V4.1 Flash, GLM 5.3 and GLM 5.3 Flash, Nemotron 3) and set a reasoning effort from Low to Ultramath.
* Ultramath runs several agents on different approaches to one problem, lets them share findings, and returns proposed solutions to the chat for the user to judge.
* Each project gets a cloud machine with over 100 preinstalled tools, including Lean with Mathlib, SageMath, PARI/GP, SymPy and LaTeX. Work continues when the user’s laptop is closed.
* Agents and people share projects, files and chats. The interface shows a result as “checked by Lean” when a proof compiles.

## Open-weight models

### DeepSeekMath-V2

**Why.** A correct final answer does not show that the reasoning was correct, and many earlier maths models were tuned for final-answer benchmarks. DeepSeek built the model to check the reasoning itself.

**How.** A proof generator drafts solutions and a separate verifier checks them and sends errors back for revision. The verifier is improved by labelling hard proofs automatically to create new training data. The proofs are in natural language and are judged by the learned verifier, not by Lean. DeepSeek reports gold-level results on IMO 2025 and CMO 2024 and 118 of 120 on Putnam 2024. Weights are on Hugging Face under Apache 2.0.

### DeepSeek-Prover-V2

**Why.** Formal proofs of hard theorems are long, and training signals are sparse.

**How.** DeepSeek-V3 breaks each theorem into subgoals. The proofs of those subgoals become cold-start data for RL, with a binary correctness reward and a consistency penalty so that every subgoal appears in the final proof. The largest version has 671 billion parameters.

### Goedel-Prover-V2

**Why.** To show that a small, open prover can match much larger ones.

**How.** It uses three techniques: scaffolded data synthesis (synthetic theorems of increasing difficulty), verifier-guided self-correction using Lean compiler feedback, and model averaging. The 32B model reports 88.0% on miniF2F at pass@32, rising to 90.4% with self-correction. The 8B model reports 83.0%, matching DeepSeek-Prover-V2-671B on that benchmark. The earlier Goedel-Prover built a set of 1.64 million formal statements by translating Numina problems into Lean, then trained through repeated rounds of proving and retraining.

### Kimina-Prover

**Why.** To test whether RL can teach a model formal reasoning patterns directly.

**How.** The preview model has 72 billion parameters and was trained with RL. A distilled 7B version is also available. Other groups have used it as a base for further training.

## Closed and commercial systems

### AlphaProof (Google DeepMind)

**Why.** To learn proof search from experience, as AlphaZero learned board games, with Lean providing the rules.

**How.** A fine-tuned Gemini model translated about 1 million informal problems into about 80 million Lean statements for training. A transformer of roughly 3 billion parameters guides an AlphaZero-style tree search. For hard problems it uses test-time RL, generating and learning from variants of the target problem. With AlphaGeometry it solved four of six IMO 2024 problems, a silver-medal score. The Nature paper appeared in November 2025, and researchers can apply for access.

### AlphaEvolve (Google DeepMind)

**Why.** Many research questions ask for an object that can be scored by code, such as a construction that improves a bound.

**How.** An LLM proposes programs and an automated evaluator scores them in an evolutionary loop. With Terence Tao and Javier Gómez-Serrano it was applied to 67 problems and improved the best known result on about 20. In one example AlphaEvolve found a construction for the finite-field Kakeya problem, Gemini Deep Think proved it, and AlphaProof formalised the proof in Lean. DeepMind has said it plans an early-access programme for academics.

### Aristotle (Harmonic)

**Why.** Harmonic aims for “mathematical superintelligence”, arguing that verifiable reasoning makes AI output checkable.

**How.** It combines a Lean proof search system, an informal reasoning component that proposes and formalises lemmas, and a dedicated geometry solver. It is trained with RL on Lean proofs and reached gold-medal-equivalent performance on IMO 2025. An autoformalisation layer lets users write in natural language and get Lean back.

### AxiomProver and AXLE (Axiom Math)

**Why.** To build a fully autonomous prover and the infrastructure that proof-writing systems need.

**How.** AxiomProver is a multi-agent ensemble for Lean 4. The company reports that it solved all 12 Putnam 2025 problems, 8 within the exam time. AXLE, released in March 2026, is a hosted service with operations such as proof verification and theorem extraction, so that others can run Lean-based reasoning without deploying Lean themselves.

### Gauss (Math, Inc.)

**Why.** Formalising a major result by hand takes years of expert effort.

**How.** An agent works autonomously for hours to turn natural-language mathematics into Lean. It formalised the strong Prime Number Theorem in about three weeks, producing roughly 25,000 lines of Lean with over 1,000 theorems and definitions. It has since formalised Maryna Viazovska’s sphere-packing proofs. It still depends on a natural-language outline from mathematicians.

### Seed-Prover 1.5 (ByteDance Seed)

**Why.** To reach harder problems with a moderate compute budget.

**How.** An agent trained with large-scale RL interacts with Lean through lemmas and accumulates experience during training. A test-time workflow links natural-language and formal proving. It reports 88% on PutnamBench, 80% on Fate-H (graduate level) and 33% on Fate-X (PhD level), and verified Lean proofs for 11 of 12 Putnam 2025 problems. I did not confirm that the weights are public.

## Open agent frameworks

### Numina-Lean-Agent

**Why.** Task-specific pipelines around trained provers are hard to reproduce and adapt. The authors use a general coding agent as the maths reasoner so that performance improves by swapping in a better base model, with no extra training.

**How.** It pairs Claude Code with Numina-Lean-MCP, a set of tools for talking to Lean, retrieving theorems and informal proving. With Claude Opus 4.5 as the base model it reports 12 of 12 on Putnam 2025, and it was used with mathematicians to formalise the Brascamp–Lieb theorem.

### QED

**Why.** The authors identified seven failure modes in single-query proof generation, including citation hallucination, hand-waving on key steps and unstable plans. Each part of the architecture targets one of them.

**How.** Agents for literature survey, planning, proving and verification run in a loop, with a regulator agent deciding whether to revise the plan or retry the proof. Of 18 research-level projects, it produced five original works, three of which experts judged comparable to work in specialist venues. Code is at github.com/proofQED/QED.

### Bolzano

**Why.** To move from expert-guided proof search to running at scale on open problems extracted from papers.

**How.** Parallel prover agents work with a verifier agent and a human-readable research state. Run on about 3,800 open problems, it reports solving about 200, including four questions from STOC 2026 papers confirmed by their authors. This is a recent preprint (7 October 2026) and has had little time for external scrutiny.

### Others

Goedel-Architect generates a lemma blueprint, then has a Lean prover close each open lemma in parallel. With DeepSeek-V4-Flash as its base it reports 99.2% pass@1 on miniF2F and 75.6% on PutnamBench. Cogentic uses Gemini with an orchestrator, adversarial verifiers and a ledger of verified intermediate results, and reports novel results on five open problems in learning theory and mechanism design.

## Supporting infrastructure

* **Lean 4 and Mathlib.** The proof assistant and its community library, which Math, Inc. describes as about 2 million lines of code and 350,000 theorems and definitions from over 600 contributors.
* **Lean servers and tool bridges.** The Kimina Lean Server wraps the Lean REPL for parallel verification. Lean-LSP-MCP lets agents interact with Lean. AXLE offers a hosted equivalent.
* **Benchmarks.** miniF2F and PutnamBench for formal proving, Fate-H and Fate-X for graduate and PhD level, and Formal Conjectures, a repository of formalised open problems used to test whether AI can resolve them.

## Cautions

* Benchmark scores come from developers and use different settings (pass@k, compute budgets, Lean versions), so cross-system comparisons are weak.
* A Lean proof is only as good as the formal statement. Mis-formalised statements are a known risk, and Formal Conjectures reports using AI-generated proofs and disproofs to audit its own formalisations.
* Natural-language systems such as DeepSeekMath-V2 and most agent harnesses still need expert review. A human audit of OpenAI’s recent AI-generated proofs (September 2026) shows the kind of checking that claims in this area now receive.
* General frontier models are also producing research results. An internal OpenAI model is reported to have disproved the Erdős planar unit-distance conjecture in 2026. That model is not maths-specific and is not publicly available.

## Sources

* [Open Math OS](https://www.openmathmodel.org/)
* [Open Math Model initiative](https://www.openmathmodel.org/initiative/)
* [Goedel-Prover (arXiv 2502.07640)](https://arxiv.org/abs/2502.07640)
* [Goedel-Prover-V2 on Hugging Face](https://huggingface.co/Goedel-LM/Goedel-Prover-V2-8B)
* [Prover Agent, summary of open provers (arXiv 2506.19923)](https://arxiv.org/pdf/2506.19923)
* [Goedel-Architect (arXiv 2606.06468)](https://arxiv.org/pdf/2606.06468)
* [DeepSeekMath-V2 coverage, MIT Sloan Management Review Middle East](https://www.mitsloanme.com/?p=10030)
* [DeepSeekMath-V2 coverage, China Daily](https://subsites.chinadaily.com.cn/wic/2025-12/05/c_1144604.htm)
* [AlphaProof, Nature (2025), Google Research](https://research.google/pubs/olympiad-level-formal-mathematical-reasoning-with-reinforcement-learning/)
* [AlphaProof technical summary](https://aiwiki.ai/wiki/alphaproof)
* [AlphaProof architecture coverage, 36Kr](https://eu.36kr.com/en/p/3551243830589575)
* [AlphaEvolve, IEEE Spectrum](https://spectrum.ieee.org/deepmind-alphaevolve)
* [AlphaEvolve with Tao and Gómez-Serrano, Decrypt](https://decrypt.co/347586/google-deepmind-alphaevolve-ai-new-paths-unsolved-math-problems)
* [Aristotle, Harmonic (arXiv 2510.01346)](https://arxiv.org/html/2510.01346v1)
* [Harmonic mission statement](https://harmonic.fun/news/intro-harmonic/)
* [AxiomProver at Putnam 2025](https://axiommath.ai/research/from-seeing-why-to-checking-everything)
* [Releasing AXLE](https://axiommath.ai/research/releasing-axle)
* [Gauss, Math, Inc. summary](https://skybrian-links.exe.xyz/post/605)
* [What happens when AI starts checking mathematicians’ work, Scientific American](https://www.scientificamerican.com/article/what-happens-when-ai-starts-checking-mathematicians-work)
* [Seed-Prover 1.5 (arXiv 2512.17260)](https://arxiv.org/abs/2512.17260v1)
* [Seed-Prover (arXiv 2507.23726)](https://arxiv.org/pdf/2507.23726v1)
* [Numina-Lean-Agent (arXiv 2601.14027)](https://arxiv.org/abs/2601.14027v1)
* [QED (arXiv 2604.24021)](https://arxiv.org/pdf/2604.24021)
* [QED failure-mode analysis](https://chatpaper.com/chatpaper/paper/272676)
* [Bolzano (arXiv 2610.09769)](https://www.opentrain.ai/papers/bolzano-from-expert-guided-proof-search-to-automated-open-problem-solving--arxiv-2610.09769/)
* [Cogentic](https://deeplearn.org/arxiv/836084/cogentic:-multi-agent-orchestration-for-automated-proof-discovery)
* [Advancing mathematics research with AI-driven formal proof search](https://www.researchgate.net/publication/405133529_Advancing_Mathematics_Research_with_AI-Driven_Formal_Proof_Search)
* [OEIS Open and related references (arXiv 2608.11941)](https://arxiv.org/pdf/2608.11941)
* [The Past and Future of AI Scientists (arXiv 2608.14407)](https://arxiv.org/pdf/2608.14407)
* [A Human Audit of OpenAI’s AI-Generated Mathematical Proofs (arXiv 2608.14673)](https://arxiv.org/pdf/2608.14673)
