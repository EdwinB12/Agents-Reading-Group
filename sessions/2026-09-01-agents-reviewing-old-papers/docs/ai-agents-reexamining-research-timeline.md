# Machines Re-Reading the Record

## A historical timeline of AI systems used to re-examine existing research

*Prepared August 2026*

---

## Scope and framing

This timeline covers a specific thing: the use of computational systems to **re-examine research that already exists** — published literature, archival datasets, reference databases, and prior claims — in order to extract something new from it. It deliberately excludes AI applied to fresh data collection or de novo simulation, which is a different lineage.

Four distinct modes recur, and it is worth keeping them separate because they have very different evidentiary standards, very different governance requirements, and very different institutional business cases:

1. **Recombination** — connecting findings that were published separately and never linked (Swanson's "undiscovered public knowledge").
2. **Re-analysis** — applying better methods to old data that was under-exploited at the time.
3. **Error detection** — finding mistakes, inconsistencies, and fabrication in the published record.
4. **Retrieval** — locating results that already exist but have been effectively lost.

Mode 4 is the least glamorous and, on the evidence below, has generated both the most reliable value and the most misleading headlines.

---

## Era 1 — Rule-based mining of the record (1965–1999)

**1965–1980 · DENDRAL and Meta-DENDRAL (Stanford).** Feigenbaum, Lederberg and Buchanan built systems that inferred molecular structure from mass spectrometry data and, in Meta-DENDRAL, induced new fragmentation rules from existing spectra. The first sustained demonstration that a machine could generate publishable domain knowledge from an existing data corpus.

**1979–1981 · BACON (Langley, Simon).** Rediscovered Kepler's third law, Ohm's law, and Boyle's law from the original historical datasets. Historically important as an existence proof, but also as the origin of a persistent critique: rediscovering a known law from data that has been pre-cleaned for exactly that purpose is not the same as discovery.

**1986 · Don Swanson: literature-based discovery.** The founding moment. Swanson's *Undiscovered Public Knowledge* argued that the literature contains logically implied but unstated findings, and demonstrated it by linking separate literatures on dietary fish oil and on blood rheology to hypothesise a treatment for Raynaud's syndrome — subsequently confirmed clinically. He repeated the trick in 1988 with magnesium and migraine.

**1997 · Arrowsmith (Swanson & Smalheiser).** The method became a tool. Publicly available ABC-model literature linking, and the direct ancestor of every modern hypothesis-generation agent.

---

## Era 2 — Closing the loop, and turning scrutiny on the record (2000–2015)

**2004–2009 · Robot Scientist "Adam" (Ross King, Aberystwyth/Manchester).** Adam formed hypotheses about orphan enzymes in yeast from existing genomic databases and literature, designed experiments, executed them robotically, and revised. Published in *Science* in 2009 as the first machine to autonomously discover novel scientific knowledge and validate it. The critical design feature — automatic, complete provenance logging for every hypothesis and assay — remains the gold standard that most 2026 LLM agents still do not match.

**2014 · KnIT (IBM Watson + Baylor College of Medicine).** The most methodologically rigorous demonstration of the era. KnIT mined the p53 kinase literature and generated candidate kinases. Crucially, the team ran a **retrospective holdout**: restricted to literature published before 2003, the system re-derived kinases that human researchers only identified years later. This "predict the future from the past" validation design is still the single most defensible way to evaluate a discovery agent, and it is underused.

**2015 · Robot Scientist "Eve".** Identified triclosan as active against the malaria parasite's DHFR — a repurposing hypothesis drawn from existing compound libraries and literature.

**2015–2016 · statcheck (Nuijten, Epskamp, et al.).** Not AI in the modern sense, but the pivotal moment for automated scrutiny. Scanning decades of psychology papers, statcheck found that roughly half contained at least one p-value inconsistent with its own reported test statistic, and around one in eight contained an inconsistency serious enough to affect the stated conclusion. This established that machine re-reading of the literature at scale finds problems reliably, cheaply, and in enormous quantity.

---

## Era 3 — Deep learning reads the archive (2016–2022)

**2017 · Kepler-90i (Shallue & Vanderburg, Google/NASA).** A convolutional network re-examined archival Kepler light curves that human vetting had already passed over, and found an eighth planet around Kepler-90. The canonical example of mode 2: the discovery was sitting in public data for years.

**2019 · Tshitoyan et al., *Nature*.** Word2vec embeddings trained on 3.3 million materials science abstracts. Without any supervision or chemical knowledge, the embedding space encoded latent structure–property relationships — and when the corpus was truncated at earlier dates, it recommended thermoelectric materials several years before their actual discovery. The strongest evidence to date that the literature contains more knowledge than the community has extracted from it.

**2020–2022 · Industrialised integrity screening.** Image-duplication detection (Proofig, ImageTwin) and the Problematic Paper Screener (Cabanac, Labbé, Magazinov), whose "tortured phrases" detector exposed paper mills at scale. Retrospective screening of the historic literature became routine publisher infrastructure rather than activist labour.

**2021 · ExoMiner (NASA).** 301 new validated planets from the existing Kepler archive in a single pass.

**2021 · DeepMind with Oxford and Sydney, *Nature*.** ML applied to existing mathematical datasets surfaced patterns that led human mathematicians to new theorems in knot theory and representation theory. The template for AI-as-conjecture-generator with human proof.

**2022 · AlphaTensor.** Improved on Strassen's 1969 matrix multiplication algorithm for certain cases — a fifty-three-year-old result in the textbooks, beaten by search.

**2023 · Youyou, Yang & Uzzi, *PNAS*.** A model trained on known replication outcomes was applied to 14,126 psychology papers spanning two decades, producing discipline-wide replicability estimates. Meta-research on the entire corpus, not a sample.

---

## Era 4 — LLM agents enter the loop (2023–2024)

**Dec 2023 · Coscientist (Boiko et al., *Nature*) and ChemCrow.** GPT-4-driven agents that read literature, planned syntheses, and drove automated laboratories. The first credible closed loop built on a general-purpose language model.

**Dec 2023 · FunSearch (*Nature*).** LLM-guided program search produced a new construction for the cap set problem — a genuine advance on a longstanding open problem in extremal combinatorics.

**Feb 2024 · Vesuvius Challenge.** Adjacent but instructive: ML applied to CT scans of carbonised Herculaneum scrolls recovered readable Greek text from artefacts excavated in 1752 and unreadable ever since. Verification was straightforward because the ground truth was physically present — a luxury most of this field does not have.

**Aug 2024 · The AI Scientist (Sakana AI).** End-to-end automated research pipeline, from idea to paper to review. Widely criticised for producing plausible-looking but weak work, and for a literature review stage that repeatedly failed to establish novelty. Its importance is as a warning: the component that consistently breaks is grounding claims in what already exists.

**Sep 2024 · PaperQA2 and CORE-Bench.** FutureHouse's PaperQA2 demonstrated superhuman performance on literature retrieval and, notably, on detecting contradictions between published claims. CORE-Bench (Siegel, Kapoor, Narayanan et al.) established a benchmark for agents attempting to computationally reproduce published papers — reframing reproduction as an agentic task.

**Sep 2024 · Nazca geoglyphs (Sakai et al., *PNAS*).** AI-assisted survey of existing aerial imagery nearly doubled the known catalogue of figurative geoglyphs, adding 303 in six months of fieldwork guided by model predictions.

---

## Era 5 — The co-scientist year (2025)

**Feb 2025 · Google's AI co-scientist.** A multi-agent Gemini system given an open question about how cf-PICI phage satellites acquire tails. In days it proposed the mechanism that José Penadés's group at Imperial had spent roughly a decade establishing and had not yet published. The most widely cited demonstration in the field — and the most contested, because the relevant literature was arguably sufficient to support the inference, which is precisely Swanson's point rather than a refutation of it.

**Feb 2025 · Black Spatula Project and YesNoError.** Volunteer and crypto-funded efforts to run LLMs across the published corpus hunting for errors. Covered by *Nature* as an emerging movement. Both surfaced real errors and generated substantial false-positive burden on authors — the first serious encounter with the asymmetry between the cost of generating a flag and the cost of adjudicating one.

**May 2025 · AlphaEvolve (DeepMind).** Found a way to multiply 4×4 complex matrices in 48 scalar multiplications, improving on Strassen's 49 for the first time in fifty-six years, and improved bounds on a range of open problems drawn from the existing mathematical literature.

**May 2025 · Robin (FutureHouse).** Literature-driven hypothesis generation plus automated data analysis identified ripasudil as a candidate for dry age-related macular degeneration, with experimental follow-through.

**2025 · The Virtual Lab (Swanson, Zou et al., *Nature*).** LLM agents in structured scientific "meetings" designed nanobody candidates against SARS-CoV-2 variants, grounded in the existing structural literature.

**Oct 2025 · "Erdősgate".** OpenAI staff publicly claimed GPT-5 had solved ten open Erdős problems. Thomas Bloom, who maintains the problem database, clarified that the model had located existing published solutions he personally had not been aware of; "open" on the site meant unknown to him, not unsolved. Posts were deleted; Demis Hassabis called the episode embarrassing. **This is the single most instructive event on this timeline for anyone building institutional policy.** The underlying achievement was real and valuable — literature retrieval at superhuman recall, closing problems the community believed open — but the framing collapsed the distinction between retrieval and discovery. Note also that in the course of the exercise the system surfaced an error in one of Erdős's own original papers.

**Nov 2025 · Kosmos (FutureHouse / Edison Scientific).** A single run reads around 1,500 papers, writes some 42,000 lines of analysis code across roughly 200 sub-agents, and runs up to twelve hours, maintaining a structured "world model" to sustain reasoning across tens of millions of tokens. Seven reported discoveries; three reproduced findings from unpublished or preprinted work, four claimed as novel. PhD evaluators judged around 79% of specific claims supported — but the breakdown matters enormously: roughly 85% for data-analysis claims, 82% for literature claims, and **only 58% for the system's own cross-domain syntheses**. The synthesis step is where the value is claimed and where the reliability is worst. The team also reported that output quality depended heavily on clean, well-labelled, properly normalised input data.

**Dec 2025 · "To Err Is Human" AI Checker (Bianchi, Zou et al.).** Systematic LLM scanning of published ML papers for objectively verifiable mistakes. Detected errors per paper rose from 3.8 at NeurIPS 2021 to 5.9 at NeurIPS 2025. Human experts confirmed 263 of 316 flagged items (83% precision), and the system proposed correct fixes for 76% of them.

---

## Era 6 — Institutionalisation, and the first hard evidence of limits (2026)

**Jan 2026 · Erdős problems, for real this time.** GPT-5.2 Pro paired with Harmonic's Aristotle Lean formalisation system produced original proofs for Erdős problems #728, #729 and #397 — verified formally and accepted by Terence Tao as autonomous and absent from prior literature. Tao's framing is the one to adopt: these are the "long tail" — problems solvable by standard techniques that nobody had bothered to write up. The pipeline that worked was human problem selection → model generation → formal verification → expert acceptance, not a chatbot left alone.

**Jan 2026 · Hubble Legacy Archive anomaly search (O'Ryan & Gómez, ESA).** Active-learning search across nearly 100 million image cutouts in two and a half days surfaced roughly 1,400 previously undocumented anomalous objects, including ring galaxies, mergers and lensed arcs. Archival return-on-investment at a scale no human survey could reach.

**Feb–Jun 2026 · Large-scale automated reanalysis becomes practical (Xu & Yang, Stanford/HKBU).** An AI-assisted workflow performed full-paper computational replication of 384 political science studies covering 3,382 empirical models — retrieving materials, rebuilding environments, executing code, and matching outputs to published regression tables. Full-paper reproducibility rose from 29.6% before data-availability mandates to 79.8% after. The authors note that their previous comparable reanalysis projects each took three to four years; the workflow makes periodic, systematic reassessment of whole literatures feasible for the first time.

**May 2026 · *Nature* publishes the co-scientist generation.** Google DeepMind's Co-Scientist, FutureHouse's Robin, and DeepMind's Empirical Research Assistance all appeared in *Nature* on the same day, moving the field from preprint-and-press-release into the peer-reviewed record.

**May 2026 · EinsteinArena (Together AI / Stanford).** An open platform where autonomous agents share partial results, inspect each other's failures, and build on public discussion. Twelve state-of-the-art results better than any prior human or AI solution, including improving the best known lower bound for the kissing number in dimension 11 from 593 to 604 — achieved not by one agent but through successive submissions and agent-to-agent borrowing.

**Jul 2026 · The most important negative result so far.** A study generating 219,655 research ideas across five agent frameworks and five models found that AI-generated ideas are more concentrated than human-authored work in the same area, stay much closer to the seed literature than human follow-on work does, and align *less* with the direction human research actually takes. Agents re-reading the literature reliably interpolate within it and rarely leave it.

**Aug 2026 · *Nature*: "AI agents are checking the scientific literature — and spotting decades-old errors."** The error-detection thread reaches maturity, with AI models identifying long-trusted reference values — including boiling points in chemical handbooks used for identification and distillation planning — as simply wrong. When the errors are in the reference infrastructure rather than in individual papers, the downstream contamination is unbounded.

---

## The achievements that actually matter

Stripping out the noise, six results carry most of the evidentiary weight:

* **Swanson, 1986** — established that the literature contains unstated implied knowledge. Everything since is engineering.
* **KnIT, 2014** — established the correct evaluation design: truncate the corpus, predict what came next, check.
* **Tshitoyan et al., 2019** — established that latent knowledge is recoverable statistically, without any explicit reasoning step.
* **AlphaEvolve, 2025** — established that search over the existing formal record can beat results that stood for half a century.
* **Kosmos, 2025** — established the current reliability frontier honestly, including the 58% figure for its own novel syntheses.
* **Xu & Yang, 2026** — established that whole-literature reanalysis has moved from a multi-year project to a workflow.

---

## What the record shows

**Retrieval is where the reliable value sits, and it is systematically undersold.** Erdősgate was reported as a failure. It was not: recovering forgotten solutions from the historical literature at superhuman recall is genuinely valuable, and Sébastien Bubeck's defence — that literature search is harder than people credit — was correct. The failure was purely one of framing. Institutions should expect the retrieval use case to deliver most of the near-term return and should describe it accurately.

**The attribution problem is structural, not incidental.** In almost every documented case, novelty belongs to the pipeline — the search process, the verifier, the human problem selection, the experimental follow-up — rather than to the language model component. The Erdős #728 resolution required GPT-5.2 *and* Aristotle *and* Tao. The cf-PICI result required a decade of Penadés lab work to be recognisable as correct. Governance frameworks that assign credit or accountability to "the AI" will misdescribe what happened in every case.

**Error detection scales faster than error adjudication.** From statcheck in 2016 to the Black Spatula Project in 2025 to handbook boiling points in 2026, machine re-reading finds problems in enormous volume at 80–85% precision. The bottleneck is the human cost of adjudicating each flag and the reputational cost of false accusations. Any institutional deployment needs the adjudication pathway designed before the detection is switched on.

**Data condition is the binding constraint.** Kosmos's own authors report that output quality tracked input data quality closely. Xu & Yang's reproducibility figures jumped from 30% to 80% not because of better AI but because of data availability mandates. FAIR compliance is not overhead alongside AI adoption — it is the thing that determines whether any of this works.

**Agents interpolate; they do not extrapolate.** The July 2026 concentration finding is the sharpest empirical statement of the Jagged Frontier for this task class. Re-examination of the existing record is exactly the task where agents perform best, and generating directions the literature does not already imply is exactly where they perform worst. That asymmetry is a feature to design around, not a defect to wait out.

**Verification asymmetry determines which domains move first.** Mathematics moved fastest because Lean provides mechanical verification. Astronomy moved fast because archival re-analysis is cheap to check against follow-up observation. Biology is slower because wet-lab validation is expensive. Fields without cheap verification will see the largest gap between claimed and real progress — and will need the heaviest governance.

---

## Implications worth carrying into Sheffield's planning

* **Archival re-analysis is a defensible institutional niche.** Sheffield holds decades of research data across departments that has been analysed once, with the methods available at the time. That is precisely the asset class the Hubble and Kepler results exploited. It requires no frontier capability — it requires curated data, domain experts, and compute.
* **Retrospective validation should be the standard we demand.** KnIT's 2014 design — truncate the corpus at a date, see whether the system predicts what actually followed — is cheap, rigorous, and almost nobody does it. Adopting it as a local evaluation requirement would be a genuine governance differentiator, not a compliance box.
* **Error-detection pilots need an adjudication protocol first.** Running literature-checking agents over Sheffield outputs is technically trivial and institutionally hazardous. The policy question — who sees a flag, what threshold triggers author contact, what happens to false positives — is the actual work.
* **The concentration finding is a REF-relevant risk.** If agent-generated research directions cluster tightly around existing literature, institution-wide adoption without countermeasures produces convergent, less distinctive research portfolios. That is a strategic argument for task-level stratification and for protecting the parts of the process where human divergence matters.
* **Provenance was solved in 2009 and forgotten.** Adam logged every hypothesis and every assay automatically. Kosmos's traceability design is a return to that principle after fifteen years of drift. Requiring provenance-by-default in any local agentic pipeline puts Sheffield ahead of most of the field.

---

## Selected sources

* Swanson, D. R. (1986). Undiscovered public knowledge. *Library Quarterly* 56(2).
* King, R. D. et al. (2009). The automation of science. *Science* 324.
* Spangler, S. et al. (2014). Automated hypothesis generation based on mining scientific literature. *KDD '14*.
* Nuijten, M. B. et al. (2016). The prevalence of statistical reporting errors in psychology. *Behavior Research Methods* 48.
* Shallue, C. & Vanderburg, A. (2018). Identifying exoplanets with deep learning. *Astronomical Journal* 155.
* Tshitoyan, V. et al. (2019). Unsupervised word embeddings capture latent knowledge from materials science literature. *Nature* 571.
* Youyou, W., Yang, Y. & Uzzi, B. (2023). A discipline-wide investigation of the replicability of psychology papers. *PNAS* 120.
* Siegel, Z. S. et al. (2024). CORE-Bench. arXiv:2409.11363.
* Mitchener, L. et al. (2025). Kosmos: an AI scientist for autonomous discovery. arXiv:2511.02824.
* Bianchi, F., Kwon, Y., Izzo, Z., Zhang, L. & Zou, J. (2025). To err is human: systematic quantification of errors in published AI papers. arXiv:2512.05925.
* OpenAI (2025). Early science acceleration experiments with GPT-5. arXiv:2511.16072.
* Resolution of Erdős problem #728: a writeup of Aristotle's Lean proof (2026). arXiv:2601.07421.
* Xu, Y. & Yang, L. Y. (2026). Scaling reproducibility: an AI-assisted workflow for large-scale replication and reanalysis. arXiv:2602.16733.
* Bianchi, F., Kwon, Y., Pappu, A. & Zou, J. (2026). Harnessing the collective intelligence of AI agents in the wild for new discoveries (EinsteinArena). arXiv:2606.10402.
* AI research agents narrow scientific exploration (2026). arXiv:2605.27905.
* Stokel-Walker, C. (2026). AI agents are checking the scientific literature — and spotting decades-old errors. *Nature* 656, 278–279.
* Robin: a multi-agent system for automating scientific discovery. *Nature* 655 (2026), 497–505.
* O'Ryan, D. & Gómez, P. (2026). Anomaly detection in the Hubble Legacy Archive. (See ESA/Hubble release, January 2026.)
