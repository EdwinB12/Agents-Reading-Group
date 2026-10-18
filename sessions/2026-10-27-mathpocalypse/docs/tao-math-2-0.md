# Research note: Terence Tao, "Math 2.0" (Caltech, 9 October 2026)

- **Sources:**
  - [Video](https://aimath.org/videos/terry-tao-pl/): the American Institute of Mathematics (AIM)
    second annual public lecture, given on the Caltech campus on 9 October 2026. Its original title
    was "Machine assisted proof" and it was postponed from May.
  - [Slides (PDF)](https://teorth.github.io/tao-web/slides/math-2-0-caltech-2026.pdf).
  - [Blog post and comment thread](https://terrytao.wordpress.com/2026/10/10/math-2-0/) on
    *What's new*, 10 October 2026.
- **BibTeX:** `tao2026math20talk`, `tao2026math20slides`, `tao2026math20blog`
- **Added:** 18 October 2026

> The [research brief](claude-mathpocalypse-research-brief.md) calls this "the best single talk for
> this session". It suits the session's optimistic stance. Tao does not say AI replaces
> mathematicians. He says AI should be used to *strengthen* the human community and human
> understanding. Nothing from Tao's 2026 talks is in the deck yet. These notes come from the slide
> text and the blog thread; the video has not been rewatched.

## The argument in brief

1. **Math 1.0 assumed proofs were scarce.** Solving an open problem used to be hard and rare, and
   it needed experts. Maths built its institutions, incentives and goals around that scarcity.
2. **Maths is unusually well suited to AI.** Proofs are *objectively verifiable*, even
   mechanically in Lean. They are *digitisable*: no lab work or real-world data is needed. And the
   literature is a *large, high-quality data set*. So frontier labs targeted maths first, and we are
   now in an **"era of proof abundance"**.
3. **Capability is jagged.** AI is astounding at some tasks and inadequate at others, both in maths
   and beyond. Press releases and social media suffer from **reporting bias**, so most
   frontier problems are still unsolved. Tao calls for assessments that report compute used and
   failed attempts, and points to [First Proof](https://1stproof.org/) as one example.
4. **Problem-solving was only ever a proxy.** Open problems are "lighthouses": guides for exploring
   the landscape around them, not destinations. Reaching them early with automated tools can
   "sterilize the surrounding field". Now that proofs are abundant, the proxy points the wrong way,
   and "further blind optimization of problem-solving alone is now actively harmful".
5. **Math 2.0 means expanding the frontier *and* decentring problem-solving.** Tao's diagram of
   the maths ecosystem puts **human understanding** at the hub. Understanding is what carries
   insight from pure maths, where results can be checked objectively, to applied maths, which needs
   subjective judgement. When AI bypasses the hub, the applied solutions it produces are
   "misaligned". In Math 2.0, AI is added to *every* link in the cycle, including understanding
   itself.
6. **Four types of mathematisation.** Tao sorts fields by how heavily they use AI and how well
   humans understand them:

   |                              | Light AI use | Heavy AI use   |
   | ---------------------------- | ------------ | -------------- |
   | **Weak human understanding** | Pre-math     | Misaligned math |
   | **Strong human understanding** | Math 1.0   | **Math 2.0**   |

   Weak understanding is not dangerous in itself. It just means the field has not been mathematised
   yet. The risk comes when weak understanding is combined with AI's optimising power.

## The cancer-treatment thought experiment

An AI is asked to "Find a cure for cancer that passes a stage 3 clinical trial. Make no
mistakes." It produces a cocktail of unknown chemicals. Nobody knows how the AI found it, but the
cocktail comes with a Lean certificate and passes the trial. Tao then asks:

- Could the solution be misaligned, exploiting a weakness in the trial process or in the maths
  models?
- Suppose you have just been diagnosed and a chatbot recommends this treatment to *you*. Would it
  reassure you to know that at least one human expert understands the mechanism, even partially?

The slide that follows draws the conclusion: **"Powerful AI + lack of human understanding =
misalignment risk."**

### Pushback in the blog comments

- **Medicine has always used drugs it didn't understand.** joey.li notes that phase 3 trials are
  the approval standard whether or not anyone understands the mechanism. They ask whether a
  life-saving drug should be withheld because no human understands it. D. Flood gives examples:
  - penicillin was in use from the 1940s, but its mechanism was understood only in the 1960s;
  - aspirin's mechanism was found in 1971, after about 70 years of use;
  - general anaesthesia has been used since 1846 without a full understanding of how it works.
- **Would understanding change behaviour?** Logan Lee asks whether a Lean certificate plus a trial
  record would actually change whether patients take the drug.
- **The opposite worry.** jaikrishnanj reads the scenario as an AI optimising to *pass the trial*
  while hiding long-term harms. That is Tao's misalignment point.

This is the strongest **"is understanding the product?"** prompt for a mixed RSE audience. In maths,
understanding arguably *is* the output. In medicine, outcomes are the output, and understanding is a
means to them. Most RSE disciplines sit somewhere in between.

## What Math 2.0 looks like in practice (Tao's examples)

- **Experimental maths at scale:** "population surveys" rather than "case studies". Two examples:
  - the Equational Theories Project, which settled over 22 million true/false statements in
    universal algebra (see `tao2025etp`);
  - the SAIR/LMFDB Inverse Galois Problem challenge, which found degree-24 polynomials for all of
    the roughly 25,000 possible Galois groups at that degree.
- **"Open exposition problems":** finding motivated explanations for results whose known proofs are
  opaque. The student-run Caltech Mathathon (13–15 Nov) does this with open-source AI tools.
- **Living networks of results:** the Integrated Explicit Analytic Number Theory Network is a
  "spreadsheet" of interconnected results that can be updated in real time.
- **Formal libraries** such as Mathlib.
- **"Ablation studies"** on known theorems: can it still be proved without input X? Also
  exploring the **"neighbourhood of a theorem"** by dropping or changing hypotheses.
- **Open, interpretable maths models.** The slides promise "some open math models to be released
  very soon". This probably refers to SAIR's Open Math OS, soft-launched on 16 Oct (see the brief).
- Using the understanding of maths models to **probe the failure modes** of AI when it is applied
  to real-world problems.

Closing line: "The primary bottleneck to achieving 'Math 2.0' is not technology, or even
institutional culture. It is imagination."

## Other notable comments (single-source; treat as claims)

- **Formal code isn't library code.** Nurma says little of Anthropic's roughly 13M-line Lean
  formalisation of Fermat's Last Theorem (FLT) went into Mathlib. It is "not in library style",
  "6x as big as Mathlib" and takes "20x as long to compile". The brief already quotes this (§5).
- **Refereeing load.** An anonymous referee reports spending 40–50 hours on an LLM-assisted paper
  under 15 pages, citing non-standard notation and skipped steps. They will no longer review such
  papers unless the result matters to their own work.
- **Dissent.**
  - jpolak calls Math 2.0 "an insult to the human soul".
  - Adrian points out a tension between "most problems remain unsolved" and "AI devalues human
    problem-solving".
  - alexsotirov prefers an "abundance of beauty" to competing over a "scarcity of proofs".

## Relevance to the session

- **The optimistic centre of gravity.** Tao takes the dread seriously but argues for using AI more
  imaginatively, not less. This fits with [3Blue1Brown](3blue1brown-better-time-for-math.md),
  which treats proofs as raw data and theory-building as the craft, and with the
  [Fields Medallists' statement](mathandai-statement-summary.md). It contrasts with
  [Solve Everything](solve-everything-summary.md), which treats "solving" as the goal.
- **The deck already quotes Tao's earlier posts but not this talk.** It has the "strip-mining of
  open problems" quote and a slide on "prompters" with no interest in the broader field. Math 2.0
  is the constructive follow-up to those critiques. A slide built on the 2×2 table and the cancer
  prompt would fill the gap.
- **RSE hooks:**
  - reporting negative results and compute used (reproducibility);
  - living networks of results and formal libraries (research software and data infrastructure);
  - open models running on institutional compute (see the brief, §5).

## Discussion prompts

1. In your field, is understanding the product or a means to an end? Would you take the AI
   cocktail?
2. Which of Tao's examples has an analogue in research software: ablation studies, exposition
   problems or living networks?
3. Tao says the bottleneck is "imagination". Is that optimistic, or does it underplay incentives
   and funding?
