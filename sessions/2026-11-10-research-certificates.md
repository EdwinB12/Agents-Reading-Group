# Research Certificates — Making Research Outputs Verifiable at Scale

- **Session:** 10th November 2026
- **Lead:** [Joe Heffer](https://github.com/Joe-Heffer-Shef)

---

## Overview

AI-assisted research is producing hypotheses, claims, and papers at a pace human peer review cannot match. If we can't scale trust alongside scale of output, the result is a flood of unverifiable — or quietly wrong — research. Formal methods communities have spent decades solving an analogous problem for software and mathematics: Lean 4 and similar proof assistants let a small, trusted kernel machine-check a claim, producing a "certificate" that can be verified independently of who (or what) produced it. This session asks whether a similar certificate model — something short of full formal proof, but stronger than "trust the author" — could apply to research outputs more broadly, and what would need to be true for that to work.

---

## Background reading

Work through these before the session — in order if time is short:

1. **Cryptographic certificates of validity for trustworthy AI** (Heriot-Watt) — compiles correctness predicates into succinct, independently checkable proofs
   <https://arxiv.org/html/2606.23768>

2. **Proof-Carrying Certificates for LLM Pipelines: A Trust-Boundary Architecture** — defines certificate validity via kernel type-checking plus auditing, and treats the prover itself as untrusted
   <https://arxiv.org/pdf/2605.16407>

3. **Lean4Agent: Formal Modeling and Verification for Agent Workflow and Trajectory** — applies Lean 4-style verification to agent behaviour, not just mathematical claims
   <https://arxiv.org/pdf/2606.06523>

4. **AI Research Claims: What Has Actually Been Verified?** — practical framing of what "verifiable" means for a research claim (retrievable sources, reproducible execution) when it *isn't* a theorem
   <https://www.digitalapplied.com/blog/ai-research-proof-types-reference>

5. **Why the open-source programming language is becoming a key tool to inject rigor and certainty into AI systems** (VentureBeat, on Lean 4) — accessible primer on how Lean 4's kernel/certificate model works and why it's gaining traction beyond pure mathematics
   <https://venturebeat.com/ai/lean4-how-the-theorem-prover-works-and-why-its-the-new-competitive-edge-in>

---

## Timed agenda

| Time        | Activity                                                  | Who        |
|-------------|------------------------------------------------------------|------------|
| 3:00–3:15   | Intro & framing — why verification needs to scale with output | Lead       |
| 3:15–3:35   | How Lean 4 certificates work — kernel, trust boundary, sorry-free proofs | Lead       |
| 3:35–3:50   | Beyond mathematics — certificate/proof-carrying approaches for code, agent trajectories, and claims | Lead       |
| 3:50–4:15   | Practical activity (see below)                            | All        |
| 4:15–4:30   | Discussion & evaluation (see prompts below)                | All        |

Total: 90 minutes.

---

## Practical activity (~25 min)

**Goal:** work out what a "certificate" could actually check for a research output that *isn't* a mathematical theorem — and where that breaks down.

### Setup (5 min)

Each person or pair picks one research output type:

| Type | Example claim |
|------|----------------|
| **A** | A statistical result ("this intervention improves outcome X, p < 0.05") |
| **B** | A piece of scientific software (`this function correctly implements algorithm Y`) |
| **C** | A literature synthesis ("no prior work has combined methods X and Y") |
| **D** | An empirical benchmark result ("model M scores N% on dataset D") |

### Task (15 min)

For your chosen claim type, sketch a "certificate" design:

- **What is the trusted kernel?** (What small, auditable thing does the checking, analogous to Lean's kernel?)
- **What is machine-checkable vs. what still needs a human?** Be honest about the gap — most of these claims are not reducible to a closed formal system the way a theorem is.
- **What would a forged or "gamed" certificate look like?** (e.g. p-hacking dressed up as a passing check, a benchmark run against a leaked test set)
- **What's the minimal artefact a reader/reviewer needs to independently re-check the certificate**, without re-running the whole study?

### Share & critique (5 min)

Swap with another person/pair. Push on: does this design actually reduce trust required in the *author*, or does it just relocate trust to whoever built the checker?

---

## Discussion & evaluation prompts

Use these to structure the final 15 minutes. Aim to cover at least four.

1. **Where does the Lean 4 analogy hold, and where does it break?** Lean's guarantee rests on a small trusted kernel and a closed formal language. Most research claims (empirical, statistical, qualitative) don't reduce to that. Is "certificate" the wrong word for anything short of a proof, or is a weaker, graded notion of certificate still useful?

2. **Trust relocation, not trust elimination** — a certificate is only as good as whoever wrote the checker and chose what it checks. Who audits the auditors? Does this just create a new gatekeeping layer with its own incentive problems?

3. **Scale vs. rigour trade-off** — the pitch here is coping with an explosion of AI-generated research output. Does a lightweight, partial certificate (e.g. "reproducibility passed," "no citation exists that was fabricated") do enough good to be worth building, even if it can't approach Lean-level guarantees?

4. **Incentives for adoption** — would researchers actually generate certificates for their own work, given the current incentive structure (publish fast, novelty over rigour)? What would have to change — journal requirements, funder mandates, tooling being free/invisible — to get adoption?

5. **Certifying agents vs. certifying outputs** — Lean4Agent-style work verifies agent *trajectories*, not just final claims. For an AI research assistant, is it more valuable to certify the process (how the claim was derived) or the product (whether the claim itself holds)?

6. **What would we actually build?** If this group prototyped something, what's the smallest useful version — a citation/claim checker, a reproducibility harness, a "sorry"-style flag for unverified steps in an AI-written paper? What's already out there we'd be duplicating?

---

# Links

Papers

- [Cryptographic certificates of validity for trustworthy AI](https://arxiv.org/html/2606.23768)
- [Proof-Carrying Certificates for LLM Pipelines: A Trust-Boundary Architecture](https://arxiv.org/pdf/2605.16407)
- [Lean4Agent: Formal Modeling and Verification for Agent Workflow and Trajectory](https://arxiv.org/pdf/2606.06523)
- [Formally Verified Patent Analysis via Dependent Type Theory: Machine-Checkable Certificates from a Hybrid AI + Lean 4 Pipeline](https://arxiv.org/pdf/2604.18882)
- [Automated Conjecture Resolution with Formal Verification](https://arxiv.org/pdf/2604.03789)
- [NeurIPS Should Require Reproducibility Standards for Frontier AI Safety Claims](https://arxiv.org/pdf/2605.08192)
- [Position: Behavioural Assurance Cannot Verify the Safety Claims Governance Now Demands](https://arxiv.org/pdf/2605.15164)

Commentary and background

- [Why the open-source programming language is becoming a key tool to inject rigor and certainty into AI systems (VentureBeat, on Lean 4)](https://venturebeat.com/ai/lean4-how-the-theorem-prover-works-and-why-its-the-new-competitive-edge-in)
- [AI Research Claims: What Has Actually Been Verified?](https://www.digitalapplied.com/blog/ai-research-proof-types-reference)
- [Verifiable AI Research (2026): What It Actually Means](https://www.atlasworkspace.ai/blog/verifiable-ai-research)
- [AI and the Evolving Role of the Scientific Paper (CACM)](https://cacm.acm.org/opinion/ai-and-the-evolving-role-of-the-scientific-paper/)

Tools

- [Leanstral: Mistral's open-source proof agent for Lean 4](https://webkul.com/blog/mistrals-leanstral/)
