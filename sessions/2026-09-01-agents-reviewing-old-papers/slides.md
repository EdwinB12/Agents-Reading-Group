---
marp: true
theme: uos
paginate: true
---

<!-- _class: lead -->

![width:220px](images/UOSLogo_Primary_White_RGB.png)

# Agents Reviewing Old Research Outputs

**Session:** 1st September 2026
**Lead:** Joe Heffer

---

## Agenda

- What is agent discovery?
- Why now?
- A brief history
- Agentic research audit
- Agentic hypothesis generation
- State of the art
- Practical activity
- Discussion

---

<!-- _class: lead -->

# Introduction

_Agents re-reading the record_


---

## Why point agents backwards at old research?

A fast-growing use of AI agents: aim them at the **existing** body of research outputs such as published code, papers, and datasets — not new experiments.

Two modes:

- 🔍 **Audit** — finding errors, unreproducible results, inconsistencies, mis-reported numbers
- 💡 **Discovery** — connections across papers, re-analysis of open data, hypotheses no one followed up

<!-- Relevant for RSE work specifically: we already do reproducibility/data-integrity checks by hand. -->

---

## 💡 Different kinds of discoveries

1. **Recombination** — connecting findings that were published separately and never linked → hypothesis generation. (Similar to Google Co-Scientist approach we discussed previously.)
2. **Re-analysis** — applying better methods to old data that was under-exploited at the time.
3. **Retrieval** — locating results that already exist but have been effectively lost.

---

## Literature-based discovery

The classic model of result **recombination**:

- **Literature-based discovery (Swanson, 1986)** (LBD) generates hypotheses via the **ABC model**
  - **Connecting the dots:** _A_ relates to _B_ in one paper, _B_ relates to _C_ in another, so _A_ and _C_ may be related, though no paper ever says so
  - Two modes: **open discovery** (start from _A_, surface candidate Cs) and **closed discovery** (test a proposed _A_–_C_ link by searching for the Bs)
- **Limitations:** no consensus on what counts as a "discovery", only a handful of canonical replicated cases (fish oil–Raynaud's, magnesium–migraine) to evaluate against, and a standing critique that it reduces knowledge to pairwise co-occurrence

---

## Why now?

- Frontier models (Opus, Fable, OpenAI Sol) have crossed a threshold: reliably strong at long-context reading and reasoning — enough to check claims, not just summarise them
- Two capabilities now compound: reading/reasoning over text (papers, citations, reference data) + agentic coding (cloning repos, rebuilding environments, re-running analysis)
- Robotics/embodied AI remains comparatively limited, so "wet lab" science stays bottlenecked — literature- and code-based science does not
- Net effect: the highest-leverage target for today's agents is the **existing** corpus, not new experiments

---

## What prompted this

**Nature, August 2026:** "AI agents are spotting decades-old errors in scientific papers" (Stokel-Walker, *Nature* 656, 278–279)

- Models are flagging long-trusted reference values — e.g. boiling points in chemical handbooks used for identification and distillation planning — as simply wrong
- When the error sits in the reference infrastructure, not one paper, the downstream contamination is unbounded
- Same month: Google published its own **Paper Assistant Tool** for automating parts of scientific review (Jayaram et al., 2026)

---

<!-- _class: lead -->

# A brief history

_From algorithms, to machine learning, to autonomous agent swarms..._

---

## The founding decades (1965–2015)

- **1965–80 — DENDRAL / Meta-DENDRAL:** first machine to generate publishable knowledge from an existing data corpus
- **1986 — Don Swanson:** linked separate literatures (fish oil ↔ blood rheology) to predict a treatment — the founding move
- **2009 — Robot Scientist "Adam":** closed the loop end-to-end, with full provenance logging still unmatched by most agents today
- **2014 — KnIT:** set the gold-standard test — truncate the literature, predict what came next, check
- **2015–16 — statcheck:** scanned decades of psychology papers; roughly half had a p-value inconsistency

---

## Deep learning reads the archive (2016–2022)

- **2017 — Kepler-90i (Google/NASA):** a CNN re-examined archival Kepler light curves that human vetting had already passed over, and found an eighth planet
- **2019 — Tshitoyan et al.:** word2vec embeddings on 3.3M materials-science abstracts recommended thermoelectric materials years before their discovery
- **2021 — DeepMind with Oxford & Sydney:** ML over existing mathematical datasets led human mathematicians to new theorems — the template for AI-as-conjecture-generator with human proof
- **2022 — AlphaTensor:** beat Strassen's 1969 matrix multiplication algorithm for certain cases — a 53-year-old textbook result, beaten by search
- Still precursors, not agents — static or one-shot models, before the agent era starts

---

## The agent era (2023–2026)

- **2024 — PaperQA2 / The AI Scientist:** superhuman literature retrieval, but grounding claims in what already exists is where agents still break
- **2025 — Kosmos:** 79% of claims supported overall — but only 58% for its own cross-domain syntheses
- **2025 — AlphaEvolve (DeepMind):** an LLM-driven evolutionary coding agent improved on Strassen's 1969 algorithm for 4×4 complex matrix multiplication — a direct sequel to AlphaTensor, this time via search over code rather than a static model
- **2025 — "Erdősgate":** GPT-5 "solved" ten open problems — it had retrieved existing solutions, not found new ones
- **Feb–Jun 2026**  Large-scale automated reanalysis becomes practical (Xu & Yang, Stanford/HKBU)

---

<!-- _class: lead -->

# 🔍 Agentic research auditing

_Finding errors in the existing literature_

---

## The Pios case

An AI agent finds an error in research database

- Sebastian Pios (theoretical chemist, Zhejiang Lab) used an AI model to predict molecular boiling points
- Predictions repeatedly clashed with a trusted 75-year-old reference database
- Manual check of the original literature confirmed: the AI was right, the database was wrong
- Two further finds the same way: a typo in a published paper, and century-old boiling-point measurements baked into the canon — both long embedded in the scientific record

[_Nature_ AI agents are checking the scientific literature by Chris Stokel Walker, 6 August 2026.]

---

## Statistical error detection

- Rule-based checks (statcheck, GRIM) test whether reported statistics are internally consistent — decades old, pre-LLM, narrow, still working at scale
- The LLM front-end adds parsing robustness and messy-PDF coverage, not judgement — several "AI error detection" claims are really this

---

## Reporting error detection

- Dec 2025 — Bianchi & Zou's AI checker: errors per paper at NeurIPS rose from 3.8 (2021) to 5.9 (2025)
  - 83% of flags (263/316) confirmed by human experts; correct fixes proposed for 76% of them
  - But recall is the weak side: injected-error studies show most real mistakes still go undetected — what it flags is usually real, what it misses tells you nothing
- Opposite failure mode to Black Spatula-style checkers (next slide): precise-but-incomplete vs. high-volume-but-noisy — same human adjudication bottleneck either way

---

## Paper ↔ code alignment

- SciCoQA — quality assurance for paper–code alignment: implementation deviates from the described method, or something load-bearing is in the code but absent from the paper (or vice versa)
- scicode-lint — LLM-generated detection patterns for methodology bugs in scientific Python
  - 54% overall precision on a clean holdout; 68–72% for high/medium findings (missing `map_location`, CUDA non-determinism, loop vectorisation) — but only 24% for the critical category: data leakage, missing `zero_grad()`
  - 75% of papers with self-contained files yielded at least one verified valid finding
- Precision is worst exactly where the stakes are highest — and this is the layer most obviously RSE territory, least covered in the popular reporting

---

## Reproducibility agents

Clone the repo, rebuild the environment, run the code, check whether the published figures/numbers regenerate

- Sep 2024 — CORE-Bench: a benchmark for agents computationally reproducing published papers
- Feb–Jun 2026 — Xu & Yang: full-paper reanalysis of 384 political science studies (3,382 empirical models); reproducibility rose from 29.6% to 79.8% after data-availability mandates
  - A job that used to take 3–4 years by hand now runs as a workflow

---

## What "reproduction" actually tests

CORE-Bench's three difficulty tiers isolate what's really being measured:

1. Code output supplied as if already run
2. Dockerfile supplied, no output
3. README only, no Dockerfile

- Most of "can an agent review old research" reduces to "can it rebuild the environment" — tier 3 is where most agents stall
- A problem RSEs have owned for a decade, not one the agent story replaces

---

## Image & data-integrity checks

- Duplicated figures (e.g. western blots) and manipulated data — historically specialist tools (Proofig, ImageTwin)
- 2020–22 — the Problematic Paper Screener's "tortured phrases" detector exposed paper mills at scale
- Now combined with agentic triage rather than manual screening alone

---

<!-- _class: lead -->

# 💡 Agentic discovery

_Generating hypotheses and results from old outputs_

---

## Re-analysis of open datasets

- 2017 — Kepler-90i: a CNN found an 8th planet sitting in public Kepler data that human vetting had already passed over
- 2021 — ExoMiner: 301 new validated planets from the same archive, in a single pass
- Jan 2026 — Hubble Legacy Archive: ~1,400 undocumented objects surfaced from 100M image cutouts in two and a half days

---

## Literature-scale synthesis

- 2019 — Tshitoyan et al.: embeddings on 3.3M materials-science abstracts predicted thermoelectric materials years before their discovery
- cf. the Allen Institute's multi-agent literature-review case study
- Nov 2025 — Kosmos: ~1,500 papers read per run, ~200 sub-agents, a structured "world model" sustained across tens of millions of tokens

---

## Evidence synthesis at scale: otto-SR

- End-to-end agentic systematic review, benchmarked against dual human reviewers
- Screening: 96.7% sensitivity / 97.9% specificity (humans: 81.7% / 98.1%)
- Extraction: 93.1% accuracy (humans: 79.7%)
- Reproduced and updated a full Cochrane issue — 12 reviews, ~12 work-years of human effort — in two days; median 0 studies wrongly excluded, median 2 eligible studies found that the original authors missed
- Meta-analyses changed: newly significant findings in two reviews, significance removed in one
- Not a new hypothesis — a corrected one, from re-reading work that already existed. The best-evidenced "discovery" result in this deck is systematic audit done properly, at scale

---

## Hypothesis generation

- 1986 — Swanson: fish oil ↔ blood rheology → a Raynaud's treatment, later confirmed clinically
- Feb 2025 — AI co-scientist: proposed in days a phage-tail mechanism a lab had spent a decade establishing
- May 2025 — Robin (FutureHouse): identified ripasudil as a candidate for dry age-related macular degeneration

---

## Counter-examples: where it breaks

Sometimes agents **interpolate** within the literature reliably but struggle to **extrapolate** beyond it.

- Aug 2024 — **The AI Scientist** (Sakana AI): a full idea→paper pipeline that produced plausible-looking but weak work; its literature-review stage repeatedly failed to establish novelty
- Oct 2025 — **"Erdősgate":** GPT-5 was reported to have "solved" ten open Erdős problems — it had actually retrieved existing solutions the maintainer wasn't aware of; "open" meant unknown to him, not unsolved. Real value, wrong label
- Jul 2026 — **The concentration finding:** across 219,655 AI-generated research ideas (5 frameworks × 5 models), outputs clustered tighter around the seed literature than human follow-on work does, and aligned *less* with the direction human research actually took

---

## Evaluating "Erdősgate"

- Oct 2025: OpenAI staff claimed GPT-5 had "solved" ten open Erdős problems — Thomas Bloom, who maintains the problem database, clarified the model had located existing published solutions he personally wasn't aware of; "open" on the site meant unknown to him, not unsolved
- **Reported as a failure. It wasn't.** Recovering forgotten solutions from the historical literature at superhuman recall is a genuinely valuable capability — Sébastien Bubeck's defence, that literature search is harder than people credit, was correct
- The actual failure was framing — conflating retrieval with discovery — not the underlying capability
- Bonus: along the way, the exercise also surfaced an error in one of Erdős's own original papers
- **Implication:** retrieval is where the reliable near-term value sits and it is systematically undersold — institutions should expect it to deliver most of the near-term return, and describe it accurately rather than oversell it as "solving open problems" or write it off as a failure

---

<!-- _class: lead -->

# State of the art

---

## Tool maturity & the false-positive problem

- Feb 2025 — Black Spatula Project / YesNoError: real errors found, but a heavy false-positive burden landed on authors
- The core asymmetry: flagging is cheap, adjudicating each flag is not
- An agent that flags 100 "errors", 90 of them spurious, creates work rather than saving it
- Kosmos's own 58% figure for cross-domain synthesis is a fair read of today's ceiling

---

## The triage economics: security got there first

Same experiment already ran in security bug bounties — the pattern transfers directly:

- curl ended its paid bounty (Jan 2026): overwhelming volumes of low-quality AI-generated reports — and quality improved immediately once payment was removed
- Google stopped accepting AI-generated vulnerability reports (Mar 2026)
- HackerOne: submissions up 76% YoY through Mar 2026; genuine-vulnerability rate held flat at ~25% — detection scaled, the noise floor scaled with it
- GitHub moved to a two-tier programme; Apple imposed per-researcher caps and a cool-off

Science's triage capacity (journal integrity teams, PubPeer moderators, individual authors) is smaller, slower, and unpaid. ERROR pays reviewers 250–2,500 CHF per verified error — an interesting design precisely because curl's experience suggests the incentive structure may be the problem, not the fix.

**The binding constraint isn't how many errors an agent can find — it's how many flags a human can adjudicate per hour, and what a false accusation costs.**

---

## Why some domains move first

> **Verification asymmetry determines which domains move first.** Mathematics moved fastest because Lean provides mechanical verification. Astronomy moved fast because archival re-analysis is cheap to check against follow-up observation. Biology is slower because wet-lab validation is expensive. Fields without cheap verification will see the largest gap between claimed and real progress — and will need the heaviest governance.

- Every fast-moving case in this deck sits on a cheap verifier: Lean for AlphaTensor/AlphaEvolve, follow-up telescope time for Kepler-90i/ExoMiner, re-running code for Xu & Yang
- Biology, materials synthesis, and other wet-lab fields lack that shortcut — a predicted result still needs a bench experiment to confirm
- Practical implication: expect the claimed/real progress gap to track verification cost, not model capability — and weight scrutiny accordingly

---

## FAIR is AI-ready

> **Data condition is the binding constraint.** Kosmos's own authors report that output quality tracked input data quality closely. Xu & Yang's reproducibility figures jumped from 30% to 80% not because of better AI but because of data availability mandates. FAIR compliance is not overhead alongside AI adoption — it is the thing that determines whether any of this works.

- **F**indable, **A**ccessible, **I**nteroperable, **R**eusable — a 2016 data-stewardship principle, now doubling as the precondition for agentic reanalysis
- Every case in this deck that worked at scale (Kepler archive, Hubble Legacy Archive, Xu & Yang's political science corpus) ran on data that was already open and well-described
- Reframe for funders/authors: FAIR was pitched as good practice; it's now the difference between "an agent can check this" and "an agent can't get in the door"

---

<!-- _class: lead -->

# Practical activity

---

## Activity options

- Point an agent at a small, self-contained published repo (paper + data + figures) and ask it to reproduce one headline number or figure. Narrate where it succeeds, where it silently fudges, and where it gives up.
- Take a short methods/results section and ask an agent to check internal consistency of the reported statistics. Manually verify a sample of its flags to estimate its precision.
- Sketch a two-agent design — a "finder" that proposes possible errors and an independent "verifier" whose only job is to try to refute each flag — and discuss whether that lowers the false-positive rate enough to be useful.

---

<!-- _class: lead -->

# Discussion

---

## Human-in-the-loop

- 2009 — Robot Scientist Adam logged every hypothesis and assay automatically; most 2026 agents still don't match that
- Triage assistant (surfaces candidates for a human to judge) vs. autonomous auditor (acts or reports directly) — very different risk profiles
- Where should we land for our own RSE work?

---

## Incentives & ethics

- Who acts on an agent-flagged error, and how are authors notified?
- Risk of automated accusations at scale — a false positive has a reputational cost, not just a review cost
- Attribution is structural: in almost every documented case, credit belongs to the pipeline (search + verifier + human judgement), not "the AI" alone

---

## Retrospective validation as a standard

> **Retrospective validation should be the standard we demand.** KnIT's 2014 design — truncate the corpus at a date, see whether the system predicts what actually followed — is cheap, rigorous, and almost nobody does it. Adopting it as a local evaluation requirement would be a genuine governance differentiator, not a compliance box.

- **Critique:** to what extent is this actually possible? Today's discoveries are rapidly folded back into the research culture — and into the training data of new foundation models — so does "truncate and predict" still isolate genuine prediction, or does it just measure how much of the held-out future the model already memorised?

---

## Discussion prompts (1/2)

- If an agent flags a possible error in a published paper, what's the responsible workflow from "flag" to "correction/retraction"? Who is in the loop?
- Verification is the hard part: how do you keep the false-positive rate low enough that flags are worth acting on? What does "adversarially verify each finding before reporting it" look like in practice?

---

## Discussion prompts (2/2)

- Re-running old code is a reproducibility problem we know well — how much of "review old research" is really just "can we rebuild the environment", and where do agents genuinely add value beyond that?
- Discovery vs. audit: is the bigger payoff finding *mistakes* in old work or finding *missed insights*? Which is more tractable for current agents?
- What would we, as RSEs, want an agent to check on our *own* past outputs before we'd trust it on someone else's?
- To what degree can/will AI systems be able to innovate and be original, creatively extrapolating new ideas, compared to just interpolating between existing results? (cf. the concentration finding, slide "Counter-examples: where it breaks")
- To what degree is fully-autonomous agentic research discovery/error-finding wanted and wise? (cf. triage assistant vs. autonomous auditor, slide "Human-in-the-loop")

---

## Links & resources

- [Nature: AI agents are spotting decades-old errors in scientific papers](https://doi.org/10.1038/d41586-026-02235-8) (Stokel-Walker, 2026) — the article that prompted this session
- [Black Spatula Project](https://github.com/The-Black-Spatula-Project) — community effort using LLMs to find errors in published papers at scale
- Jayaram et al. (2026) — Google's Paper Assistant Tool
- Related idea in this repo: [Claude Science workbench](../../ideas/claude-science-workbench.md) — a dedicated "reviewer" agent that verifies reported numbers against underlying code
- Full citations in `references.bib`
