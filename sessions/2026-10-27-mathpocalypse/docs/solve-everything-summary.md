# Summary: "Solve Everything: Achieving Abundance by 2035"

- **Source:** <https://solveeverything.org/> (authors' companion post:
  [The Innermost Loop](https://theinnermostloop.substack.com/p/solve-everything))
- **Authors:** Alexander D. Wissner-Gross (founder of Physical Superintelligence) and Peter H. Diamandis
  (founder of XPRIZE). The site says AI was used as a co-writer.
- **Published:** the site gives no date. Secondary coverage puts it at around February–April 2026,
  so **before** OpenAI's Navier–Stokes announcement (8 Sep) and the 722-manuscript release (6 Oct).
- **Added:** 18 October 2026

> A book-length techno-optimist / accelerationist blueprint, written to persuade. It is useful here
> as the **utopian counterpoint** to the Fields Medallists'
> [misalignment statement](mathandai-statement-summary.md). Its figures are the authors' own and have
> not been checked against primary sources. See [Caveats](#caveats-for-the-session).
>
> For the wider accelerationist / techno-optimist context (Hassabis, Amodei, Altman, Andreessen,
> e/acc, Szegedy, Harmonic, Zeilberger and critics within the camp), see
> [accelerationist-viewpoints.md](accelerationist-viewpoints.md).

## Core claim

Advanced AI turns "cognition" into "a commodity". If that cheap intelligence is aimed at clearly
defined "Moonshots" and judged against rigorous, blinded targets, whole fields can be "solved" in bulk
by 2035. A field counts as **solved** once progress depends on compute rather than on rare human
genius.

## Key points

1. **Each revolution removes one scarcity.** The scientific, industrial and digital revolutions removed
   ignorance, the limits of muscle power, and distance. This one removes scarce expert attention. Each
   revolution goes through four stages: Legibility, Harnessing, Institutionalisation and Abundance.
2. **The new bottleneck is "routing".** Models are getting better, cognition is getting cheaper, and
   AI is getting easier to plug in. The scarce resource becomes the decision about *where to point*
   the intelligence.
3. **Fields industrialise only once success is measured precisely.** Their template is AlphaFold.
   Protein folding went from a PhD-level craft to a cheap query because the field had a clear purpose,
   structured tasks, data, and a blind test (CASP).
4. **The L0–L5 maturity curve.** Ill-posed ("the Muddle"), then Measurable, Repeatable, Automated,
   Industrialised, and finally Commoditised ("Solved"). They call a field's sudden move from
   hand-craft to industry **"Domain Collapse"**.
5. **Maths goes first.** Maths is "solved" in their Phase 1 (2026–27) and becomes "a utility like tap
   water". It then knocks over physics, then materials, then fusion. Their evidence is FrontierMath
   Tier 4 scores rising from 13% to 19% "in mere months".
6. **Verification is one layer of a nine-layer "Industrial Intelligence Stack".** The stack runs from
   Purpose and Payoff to Distribution. Its verification mechanisms are:
   - **Two-Stack Rule:** two independent AI toolchains must agree before a safety-critical system goes
     live.
   - **Replication Packs:** "cryptographically signed" bundles of "code, proofs, and logs" that third
     parties can re-run.
   - **Proof Robustness:** tested against adversarial perturbations.
   - **Blinded Clears:** testing against hidden test sets that are "managed by independent third-party
     stewards and constantly shifted".
   - **Calibrated Abstention:** rewarding "I don't know" over guessing.
7. **Credit moves from people to infrastructure.** Prestige shifts from the individual "Hero" to the
   "Harness Builder". The expert becomes a "Conductor of Intelligence", an "Ethical Anchor" holding
   the kill switch, or an "Explorer of Purpose".
8. **Failure modes they name.** "Goodhart-Resistant Design"; **Spec Capture** ("when the measurement
   stops reflecting the real-world mission"); data leakage; gaming; monoculture; outcome gaming.
9. **Three scenarios.** A "Bright Path" to abundance; a "Muddle Path" in which AI is captured by ad
   optimisation and "grant theater"; and a "Dark Path" in which safety concerns freeze progress.

## Policy recommendations

- "Publish the Targets, Then the Budgets": create **Targeting Authorities** that accept blinded,
  rolling submissions.
- "Buy **proofs**, not hours": procure outcomes rather than projects.
- **Compute Escrow:** release funding only when benchmark gains are verified.
- Require **Decision Records for AI Systems (DR-AIS)** audit logs, and automatic safety brakes that
  trigger when reliability metrics fall. Fund Data Trusts and red-team bounties.

## Relevance to the session

- **It puts the bottleneck somewhere else.** The session's theme is that *generating results is now
  cheap; adjudicating them is not*. The manifesto agrees that cognition gets cheap. But it treats
  verification as just another layer the stack automates, so the new bottleneck becomes *choosing
  targets*. The withdrawals within a day, and Bastounis et al.'s "lost in translation" paper, suggest
  that checking is still the expensive, human part.
- **"Solved" versus understood.** Under their definition, maths is solved once it is compute-bound,
  whether or not anyone understands it. This is the opposite of the Fields Medallists' view that
  "problems are landmarks, not destinations". It sets up the proof-vs-understanding discussion well.
- **The Two-Stack Rule and Track A.** In the Navier–Stokes case, Google DeepMind's Formal Conjectures
  wrote the statement, OpenAI wrote the proof, and Comparator checked it. The manifesto would call
  this best practice. The forcing loophole shows the rule's limit: independent agreement on a formal
  statement doesn't guarantee that the statement says what the headline claims.
- **Spec Capture predicts the forcing loophole.** Reporting "Lean-verified finite-time blow-up with
  smooth forcing" as "AI solves Navier–Stokes" is exactly the measurement drifting away from the
  mission. The authors name this risk, but their remedy is more measurement.
- **Credit and a two-tier science.** "Harness Builder" prestige combined with outcome-based procurement
  assumes that whoever owns the stack takes the credit. With proprietary models, that owner is the AI
  lab, not the mathematicians whose earlier work the result builds on. This is the optimistic
  framing of the two-tier worry, and it connects to the Fortune piece on the priority dispute.
- **A test of their maturity curve.** Their maths timeline rests on benchmark scores. The `openai/math`
  release (around 4,000 open problems in, 722 manuscripts out) looks more like the industrial process
  they describe. Possible discussion question: **where is research maths on L0–L5 now?**

## Caveats for the session

- **Advocacy, not research.** The authors have commercial interests, and the site discloses that it
  "may contain errors typical of large language models". Treat its figures, such as the FrontierMath
  numbers, as secondary claims and hedge them.
- **It doesn't engage with how formal maths is done in practice.** The text never mentions Lean,
  theorem provers or peer review. Its verification story is generic (signed packs, hidden test sets)
  and doesn't address translating informal maths into formal statements.
- **Mixed reception.** Coverage such as
  [Daily Friend, "The giddy side of AI"](https://dailyfriend.co.za/2026/04/22/the-giddy-side-of-ai/)
  notes that its ambition has drawn both praise and derision.
- **Not fully read.** These notes cover nearly all of the page text, but not the last part of the
  glossary. The publication date comes from secondary sources.
