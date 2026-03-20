# Harmonic Aristotle — Automated Theorem Proving for Graduate and Research-Level Mathematics

**Session:** 14 April 2026 · 3:00–4:30 pm
**Lead:** TBD

---

## Overview

Formal verification has long been the domain of specialist logicians and proof engineers. **Harmonic Aristotle** changes that calculus: it is an automated theorem proving system by [Harmonic](https://harmonic.fun/) that proves and formally verifies graduate and research-level problems in mathematics, software, and beyond, producing machine-checked proofs in **Lean 4**. Rather than generating plausible-looking derivations that must be checked by a human expert, Aristotle outputs proofs that are verified by the Lean kernel — a small, auditable core whose acceptance is a correctness guarantee, not a heuristic.

This raises a sharp question for the agentic AI community: *what does it mean for an AI agent to not just solve problems, but to produce unforgeable certificates of correctness?* Aristotle is a concrete existence proof that agentic reasoning can be coupled to formal verification, with implications for mathematical research, software correctness, and the broader question of how we build trustworthy AI systems.

---

## Background reading

Work through these before the session — in order if time is short:

1. **Harmonic product page** — overview of Aristotle and the broader Harmonic vision
   <https://harmonic.fun/>

2. **Lean 4 documentation** — introduction to the Lean proof assistant and its type-theoretic foundations
   <https://leanprover.github.io/lean4/doc/>

3. **Lean 4 theorem proving tutorial** — hands-on introduction to writing proofs in Lean 4
   <https://leanprover.github.io/theorem_proving_in_lean4/>

4. **mathlib4** — the Lean 4 mathematics library that Aristotle builds on
   <https://github.com/leanprover-community/mathlib4>

---

## Timed agenda

| Time        | Activity                                                      | Who        |
|-------------|---------------------------------------------------------------|------------|
| 3:00–3:15   | Intro & framing — why formal verification matters for AI      | Lead       |
| 3:15–3:40   | Aristotle deep dive — architecture, capabilities, and limits  | Lead       |
| 3:40–3:55   | Lean 4 primer — reading and understanding machine-checked proofs | Lead    |
| 3:55–4:15   | Practical activity (see below)                                | All        |
| 4:15–4:30   | Discussion & evaluation (see prompts below)                   | All        |

Total: 90 minutes.

---

## Practical activity (~20 min)

**Goal:** develop intuition for what Aristotle produces and how formal proof certificates differ from informal mathematical argument.

### Setup (5 min)

Each person or pair picks one of the problem domains below:

| Domain | Problem |
|--------|---------|
| **A** | A basic number theory result (e.g. infinitely many primes, or the irrationality of √2) |
| **B** | A result from linear algebra (e.g. rank-nullity theorem) |
| **C** | A software correctness property (e.g. a sorting algorithm maintains sorted order) |

### Task (15 min)

For your chosen problem:

1. **Write an informal proof** — in plain English or pseudocode, give the argument you would present to a graduate student.

2. **Identify the proof steps** — break your informal proof into discrete logical steps. For each step, note:
   - What mathematical fact or lemma is being used?
   - Is this fact itself trivial, or does it require its own proof?
   - Could an automated system reliably verify this step?

3. **Consider the verification gap** — where does your informal argument rely on human intuition, implicit knowledge, or hand-waving that a formal system would need made explicit?

### Discussion (5 min)

Share your analysis with the group. Where did people find the biggest gaps between informal and formal argument?

---

## Discussion & evaluation prompts

Use these to structure the final 15 minutes. Aim to cover at least three.

1. **What counts as a proof?** — A Lean proof is machine-checked against a small trusted kernel. Does this give stronger guarantees than peer review? What are the limits of this kind of assurance?

2. **Research impact** — If Aristotle can prove graduate-level results, what does this mean for mathematical research as a discipline? Does it augment mathematicians or replace parts of their work?

3. **Failure modes** — Lean proofs can be correct but unreadable, or correct but rely on axioms beyond ZFC. How do you evaluate the *quality* of a formally verified proof, not just its correctness?

4. **Scope boundaries** — Aristotle targets maths and software. What problem domains are inherently resistant to formal verification, and why?

5. **Trust in AI reasoning** — Formal verification provides a certificate of correctness. How does this compare to other approaches to trustworthy AI (RLHF, constitutional AI, interpretability)? Is verifiability the right frame?

6. **Agentic integration** — How would you integrate a system like Aristotle into a broader AI agent pipeline? What would it mean for a research agent to be able to call out to a formal verifier mid-task?
