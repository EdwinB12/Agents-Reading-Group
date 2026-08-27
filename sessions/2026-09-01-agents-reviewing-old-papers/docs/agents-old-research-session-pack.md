# AI agents that re-examine old research

**Session pack — facilitator materials**
Format: 30-minute landscape tour, then ~85-minute hands-on lab with report-back.

---

## Part 1 — Landscape tour (30 minutes)

Target: 25 minutes of talk, 5 minutes of questions. Fourteen beats. The spine of the argument is that **the maturity gradient runs opposite to the excitement gradient**, and that **verification capacity, not detection capacity, is the binding constraint**.

### Beat 1 — Framing (2 min)

Most agentic-science coverage points forward: new hypotheses, new experiments, the automated scientist. This session points backwards, at the record we already have. Two distinct pitches get bundled together and shouldn't be:

* **Audit** — the published record contains errors; agents can find them.
* **Discovery** — the published record contains unexploited value; agents can extract it.

They have different evidence bases, different maturity, and different failure modes. The tour separates them.

### Beat 2 — Why the Nature piece is not quite about papers (2 min)

Stokel-Walker, *Nature* 656, 278–279 (6 August 2026), doi:10.1038/d41586-026-02235-8. The headline example isn't a fraudulent paper — it's a reference database. Handbook boiling-point values that chemists have relied on for decades, wrong all along.

Worth dwelling on for a moment, because it reframes the target. Reference databases are structured, redundant, internally checkable, and consumed by everyone. They are the highest-value, lowest-ambiguity thing an agent can audit. Compare that to "is this paper's argument sound", which is the thing everyone imagines and the thing agents are worst at.

Underlying references worth having to hand: arXiv 2512.05925, arXiv 2606.28277, arXiv 2505.11855.

### Beat 3 — The audit stack, layer by layer (1 min setup)

Order the layers by *how verifiable the check is*, not by how impressive it sounds. Four layers plus a side channel. Precision falls and ambiguity rises as you go down.

### Beat 4 — Layer 0: deterministic checks (2 min)

statcheck, GRIM, SPRITE, metacheck (`scienceverse/metacheck`). Pre-LLM, rule-based, narrow. Recompute a p-value from the reported test statistic and degrees of freedom; check whether a reported mean is arithmetically attainable given the sample size and granularity.

The point to make: these work, they have been deployed at scale, and they are *boring*. The LLM adds parsing robustness and coverage of messy PDFs — not judgement. Several "AI error detection" claims are Layer 0 checks with an LLM front-end.

### Beat 5 — Layer 1: text-internal LLM checks (3 min)

* **Black Spatula Project** (`the-black-spatula-project.github.io`) — open community effort, born from the black-plastic-kitchenware paper where a 7,000 × 60 multiplication error produced a viral health scare. Explicitly framed around the right questions: how many errors, how serious, what false-positive rate, and how much work is verification.
* **Bianchi et al., "To Err Is Human"** (arXiv 2512.05925) — GPT-5-based Paper Correctness Checker run over papers from top AI venues. 316 potential mistakes flagged across 60 sampled papers, every flag hand-checked by the authors.

The headline finding inverts the intuition in most session plans: the system was **relatively precise but poor on recall**. It doesn't drown you in noise; it quietly misses most of what's there. Related work (Dycke & Gurevych 2026; Xi et al. 2025) injects known errors into papers and finds LLMs fail to detect most of them.

So the honest summary of Layer 1: *what it flags is often real; what it doesn't flag tells you nothing.*

### Beat 6 — Layer 2: paper ↔ code alignment (3 min)

This is the layer that is most obviously RSE territory and least covered in the popular reporting.

* **SciCoQA** (arXiv 2601.12910) — quality assurance for paper–code alignment. Catches cross-modal errors: the implementation deviates from the described method; something load-bearing is in the code but absent from the paper, or vice versa.
* **scicode-lint** (arXiv 2603.17893) — LLM-generated detection patterns for methodology bugs in scientific Python. Useful precision numbers to put on a slide: **54% overall precision on a clean holdout set**; **68–72%** for high and medium findings (missing `map_location`, CUDA non-determinism, loop vectorisation); but only **24%** for the critical category — data leakage, missing `zero_grad()`. Of papers with self-contained files, **75% yielded at least one verified valid finding**.

Two things to draw out. First, precision is worst exactly where the stakes are highest: data leakage is the finding you most want and the one the tool is least reliable about. Second, three-quarters of examined papers had a real, verifiable code defect. The base rate is not low.

### Beat 7 — Layer 3: execution and reproduction agents (3 min)

Clone the repo, rebuild the environment, run it, check whether the numbers regenerate.

* **CORE-Bench** (arXiv 2409.11363) — built from CodeOcean repositories verified to be locally reproducible, including R as well as Python. Its three difficulty tiers are the most useful conceptual artefact in the whole landscape, because they isolate exactly what is being tested: (1) code output supplied as if already run; (2) Dockerfile supplied, no output; (3) README only, no Dockerfile.
* **PaperBench**, **Paper2Code**, **AutoReproduce**, **FIRE-Bench** — ML-focused, reimplementation from the paper rather than reproduction from a package.
* **REPRO-Bench** (arXiv 2507.18901), **ReplicatorBench**, and a cluster of 2026 social-science systems — reproduce findings from original data and code, repair controlled reproducibility failures, reimplement from method description alone.
* **Reproducing ICML 2026** — community challenge on Hugging Face, July–August 2026, public logbooks per paper, bring-your-own coding agent. Messy, but the open traces make failures visible in a way leaderboards don't.

The line to land: **CORE-Bench's tiers show that most of "can an agent review old research" is really "can anything rebuild the environment".** That is a problem we have owned for a decade and have not solved. The agent inherits it.

### Beat 8 — Side channel: image and data integrity (2 min)

Different technology, much more mature, already in production. Imagetwin, Proofig, ReviewerZero, Imacheck, FigCheck. Imagetwin indexes 160M+ published figures, scans in seconds, claims 80–90% detection against PubPeer-flagged cases depending on image type, and is integrated into ScholarOne, Wiley Research Exchange and Editorial Manager. ASM has run it across 17 journals since 2023 and surfaced duplication in manuscripts that had already passed peer review.

Include this precisely because it is the counterexample to the rest of the tour: narrow task, dedicated models, huge reference index, human verification layer, institutional deployment. That's what mature looks like. Note that it is not an LLM story.

### Beat 9 — Crossing over: the discovery axis (1 min)

Same corpus, opposite direction. Three sub-claims, in descending order of evidential support.

### Beat 10 — Evidence synthesis at scale (3 min)

The strongest result on the discovery side, and it is worth being explicit that it is really an audit result wearing discovery clothes.

**otto-SR** (medRxiv 2025.06.13.25329541): end-to-end agentic systematic review. Screening at 96.7% sensitivity / 97.9% specificity against dual human reviewers at 81.7% / 98.1%. Extraction at 93.1% accuracy versus 79.7% human. Reproduced and updated an entire issue of Cochrane reviews — twelve reviews, roughly twelve work-years — in two days. Median zero studies incorrectly excluded. Median two eligible studies found that the original authors had missed. Meta-analyses produced newly significant findings in two reviews and removed significance in one.

That last sentence is the whole argument. Not a new hypothesis — a corrected one, from re-reading work that already existed. Also flag the authors' own observation that this changes publishing incentives: machine-readable formats and raw numerical data behind figures become infrastructure.

### Beat 11 — Re-analysis and hypothesis generation (3 min)

Weaker ground, more excitement.

* Re-analysis of open datasets with modern methods — plausible, under-evidenced, and bottlenecked on data availability and metadata quality rather than on agent capability.
* Literature-scale synthesis to surface under-explored links and contradictions.
* Hypothesis generation: *Nature* covered multi-agent systems accelerating research (doi:10.1038/d41586-026-01596-4, May 2026), alongside an editorial arguing AI cannot do good science without humans.

Then the counterweight, published three weeks before this session: **"AI isn't ready to research itself"** (doi:10.1038/d41586-026-02494-5, August 2026). An agentic system developed concepts from two computer-science papers, and the original authors were not impressed. Also worth the mention: Nature's own reporting that human scientists still beat the best agents on complex tasks.

### Beat 12 — The shape of the landscape (2 min)

Pull the tour together in one claim:

> Maturity is inversely proportional to ambition. The most reliable systems do the narrowest, most deterministic, most boring things. The most exciting claims — autonomous discovery from old work — have the thinnest evidence. And the best-evidenced "discovery" result in the field (otto-SR) is systematic audit performed properly at scale.

For RSEs specifically: Layers 2 and 3 are ours. Paper–code alignment and environment reconstruction are RSE problems that the agent story has rediscovered, not replaced.

### Beat 13 — The triage economics, and why security got there first (3 min)

The strongest available evidence about what happens when you point finders at a corpus at scale doesn't come from science. It comes from security bug bounties, where the experiment has already run.

* curl ended its paid bounty programme in January 2026, citing overwhelming volumes of low-quality AI-generated reports.
* Google stopped accepting AI-generated vulnerability reports in March 2026.
* HackerOne: submissions up 76% year-on-year through March 2026, while the proportion flagging genuine vulnerabilities held roughly flat at a quarter. Detection scaled; the noise floor scaled with it.
* GitHub restructured into a two-tier programme from July 2026. Apple imposed per-researcher caps and a 30-day cool-off after being swamped.
* Notably, curl reported that report *quality improved immediately* once financial rewards were removed.

Transfer the lesson directly. Science's equivalent triage capacity is journal integrity teams, PubPeer moderators, and individual authors. It is smaller than security's, slower, and unpaid. ERROR (the science bug-bounty programme paying reviewers 250–2,500 CHF per verified error) is an interesting design precisely because curl's experience suggests the incentive structure may be the problem rather than the solution.

**So: the binding constraint is not how many errors an agent can find. It is how many flags a human can adjudicate per hour, and what a false accusation costs.**

### Beat 14 — Handover to the lab (1 min)

Three things we can actually measure this afternoon, which almost nobody publishes: flags raised, flags verified, minutes per verification. That ratio is the number that decides whether any of this is useful.

---

## Part 2 — Hands-on lab (~85 minutes)

**Shape:** 10 min setup → 50 min work → 20 min report-back → 5 min close.

Teams of 3–4. Mixed agent access is fine and actually useful — cross-tool comparison in report-back is a bonus. Each team picks one track.

### Ground rules (put on a slide, read out)

1. **Nothing leaves the room.** No contacting authors, no PubPeer posts, no tweets, no issues filed on anyone's repo. Every finding today is session-internal and unverified.
2. **Prefer targets where the answer is already known or the work is your own.** Withdrawn papers, ReScience C replications, or your own past outputs. No target lined up? [ar5iv.labs.arxiv.org/feeling_lucky](https://ar5iv.labs.arxiv.org/feeling_lucky) redirects to a random arXiv paper rendered as HTML — no ground truth attached, so it's a fallback for Track C, not A/B.
3. **Record the failures.** A team that gets nowhere in 50 minutes has produced the most useful data point in the room.
4. **Verify by hand.** An unverified flag is not a finding. If you can't check it in the time available, log it as *uncertain* — don't round it up.

### Track A — Reproduce one number

Point an agent at a small, self-contained published repository and regenerate exactly **one** headline figure or number. Not the paper. One number.

Where to find targets: JOSS papers with archived repos; ReScience C; CodeOcean capsules; any paper with a Zenodo DOI and a `figures/` directory.

Log: time to first blocker; what the blocker was (dependency resolution, data access, undocumented preprocessing, hardware); whether the agent *told* you it was blocked or worked around it silently; whether the final number matched.

Prompt to start from:

> Clone this repository and reproduce the value reported as [X] in the paper. Before you run anything, tell me what you expect the blockers to be. If you cannot reproduce it exactly, say so explicitly and state what differs. Do not substitute an approximation without flagging it.

### Track B — Statistical consistency, with a precision estimate

Take a methods and results section. Ask an agent to check internal consistency of reported statistics — degrees of freedom against sample sizes, p-values against test statistics, group sizes summing to the reported total, percentages against counts.

Then hand-verify **every single flag**. This is the point of the track.

Good targets: the WithdrarXiv dataset (arXiv papers with known errors, maintained by the Black Spatula community); or a paper of your own with a known erratum.

Produce: flags raised, verified real, false positive, uncertain, and total minutes spent verifying. Divide.

### Track C — Finder versus verifier

Two agents, or two sessions of the same agent. The first proposes candidate errors. The second is given only the paper and the flag, and instructed that its sole job is to **refute** the flag.

No ground truth is needed here, so it's the one track where [ar5iv.labs.arxiv.org/feeling_lucky](https://ar5iv.labs.arxiv.org/feeling_lucky) — a random arXiv paper, HTML-rendered, one redirect per visit — is a reasonable target picker if a team hasn't got one.

Log: how many flags survive refutation; whether the verifier ever refutes something that turns out to be a genuine error (the expensive failure mode); whether the verifier is simply agreeable.

Verifier prompt:

> Here is a claimed error in a published paper. Your task is to refute it. Assume the original authors were competent and the flag is wrong until proven otherwise. State the strongest case that this is a false positive. Only if you cannot construct such a case should you concede the flag may be valid.

### What to watch for (facilitator prompt during the work phase)

Circulate and look for these, because they're the interesting material for report-back:

* **Silent fudging** — the agent reports success having quietly changed a parameter, subsampled the data, or skipped a step.
* **Fabricated confirmation** — a number that matches the paper, produced by no execution at all.
* **Fixing the test rather than the code** — familiar from ordinary agentic coding, and it shows up here too.
* **Environment collapse** — 40 minutes on a dependency graph, zero minutes on science. Very common. Call it out as the CORE-Bench tier-3 problem made flesh.
* **Confident domain errors** — the agent misreads a statistical convention and flags a non-error with total assurance.

### Report-back (20 min)

Each team, three minutes, three numbers on a shared whiteboard or spreadsheet:

| Team | Track | Tool | Flags raised | Verified real | Minutes/verification |
|---|---|---|---|---|---|

Then, as a group, one derived figure: **minutes of human time per verified finding.** Compare it across tracks and tools. Sanity-check it against the Bianchi precision result and the scicode-lint 54%.

### Closing discussion (5–10 min, whatever's left)

Four prompts, in priority order — expect to reach two:

1. Given the number we just computed, does agent-assisted checking pay for itself? At what error severity does it start to?
2. If your own last paper went through Track B tomorrow, what would you want to happen to the flags — and who would you want to see them first?
3. curl's experience was that removing payment improved report quality. What does that imply for ERROR and for any institutional error-checking scheme?
4. We found the base rate is not low — scicode-lint found a verifiable defect in three-quarters of examined papers. Is the honest conclusion that the literature is riddled with errors, or that our definition of "error" is doing a lot of work?

---

## Appendix — sources

* Stokel-Walker, C. *Nature* **656**, 278–279 (2026). doi:10.1038/d41586-026-02235-8
* Bianchi, F. *et al.* "To Err Is Human." arXiv:2512.05925
* "SciCoQA: Quality Assurance for Scientific Paper–Code Alignment." arXiv:2601.12910
* "scicode-lint: Detecting Methodology Bugs in Scientific Python Code." arXiv:2603.17893
* Siegel, Z. *et al.* "CORE-Bench." arXiv:2409.11363
* Hu, C. *et al.* "REPRO-Bench." arXiv:2507.18901
* "Automation of Systematic Reviews with Large Language Models" (otto-SR). medRxiv 2025.06.13.25329541
* *Nature*, "Teams of AI agents boost speed of research." doi:10.1038/d41586-026-01596-4
* *Nature*, "AI isn't ready to research itself." doi:10.1038/d41586-026-02494-5
* The Black Spatula Project — the-black-spatula-project.github.io
* Reproducing ICML 2026 — Hugging Face Space, `ICML-2026-agent-repro/challenge`
* Imagetwin / ASM pilot — PMC12505991
