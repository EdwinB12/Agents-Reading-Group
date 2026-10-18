# Mathpocalypse: research brief and discussion structure

Agents Reading Group, 27 October 2026. Background research for the session in [PR #14](https://github.com/EdwinB12/Agents-Reading-Group/pull/14). Compiled 18 October 2026; the story is moving daily, so recheck figures the day before.

The brief is organised around the six session questions. Each block gives the facts you need on a slide, the positions worth putting in front of the group, and the best things to read or watch. A suggested pre-reading list and a set of notes on the existing deck come at the end.

---

## 0. Timeline (for an opening slide)

| Date (2026) | Event |
|---|---|
| Feb | First Proof, first batch: 10 unpublished research lemmas set as an AI test; informal grading. |
| 2 Jun | Leiden Declaration on AI and Mathematics published; endorsed by the IMU. |
| 10 Jun | First Proof, second batch: formal grading by ~30 mathematicians; 6–7 of 10 problems solved by at least one public system. |
| Aug | OpenAI “Ten advances” (non-sofic group, multicolour Ramsey bound); Gowers asks what sort of maths LLMs are good at. |
| 4 Sep | Anthropic: Claude formalises Fermat’s Last Theorem in Lean (13 million lines, 11 days). |
| 7 Sep | Buckmaster and Alpöge post forced blow-up results (porous media, Boussinesq, 3D Euler) made with Claude and Codex, with Lean proofs. |
| 8 Sep | OpenAI claims finite-time blow-up for forced 3D Navier–Stokes (~10,000 agents, 88 hours); priority dispute with Buckmaster begins. Clay Institute does not accept the claim. |
| 11 Sep | “A Severe Misalignment of AI in Mathematics”: statement signed by 25 Fields Medallists. |
| 18 Sep | SAIR (Tao co-founder) announces the Open Math Model initiative. |
| 21 Sep | OpenAI announces an independent advisory group (AGMAI, hosted at IAS). |
| 29 Sep | AGMAI publishes recommendations on responsible release. |
| 5 Oct | Quanta: “Is AI the End of Math As We Know It?” |
| 5–6 Oct | Alman and Williams post sub-quadratic 3SUM (key idea from an Anthropic model, written up by humans). |
| 6 Oct | OpenAI releases `openai/math`: 722 manuscripts in 372 families from ~4,000 problems posed. |
| 6 Oct | Bastounis, Circelli and Hansen: “Navier–Stokes lost in translation” (Lean statement does not match the prose proof). |
| 7 Oct | Association for Human Mathematics calls on mathematicians to stop working with OpenAI. Aaronson: “The Mathocalypse”. |
| 8 Oct | Hodge-conjecture manuscript withdrawn (sign error). |
| 9 Oct | Tao’s “Math 2.0” lecture at Caltech. Hales guest post on Lean reliability. TheoPhysEval preprint (49/50 physics problems). |
| 15 Oct | Simons Foundation, Anthropic and OpenAI: $15M programme for mathematicians. |
| 16 Oct | SAIR soft-launches Open Math OS. NYT interview with Tao. |

---

## 1. What has happened recently?

### Facts for the slides

* **Navier–Stokes (8 Sep).** OpenAI’s internal system claims finite-time blow-up for the forced 3D equations. A group of roughly 10,000 concurrent agents reached the result about 88 hours after launch, exchanging 2.7 million messages and about 130 billion output tokens ([OpenAI](https://openai.com/index/navier-stokes-solution/)). A warm-up Euler result came first, after which OpenAI moved its resources to Navier–Stokes. The Clay Institute’s president said evaluation would be slow and rigorous, and the problem is still listed as unsolved ([Implicator](https://www.implicator.ai/clay-institute-navier-stokes-openai-proof-claim/)). The Clay problem concerns the unforced equations, which is the “smooth-forcing loophole” your deck already covers.
* **Priority dispute.** Buckmaster and Alpöge posted forced blow-up results for related systems on 7 September, after nearly a year working with Claude and Codex. OpenAI says it started after hearing a rumour on 1 September and did not see their work ([lilting.ch timeline](https://lilting.ch/en/articles/navier-stokes-openai-blowup-dispute); [NYU Shanghai RITS summary](https://rits.shanghai.nyu.edu/ai/openai-navier-stokes-proof-credit-dispute/)).
* **The bulk release (6 Oct).** The `openai/math` README now lists 719 manuscripts in 372 families, roughly 42% of top-line results formalised in Lean, and abridged reasoning summaries for ten families. Most results came from one fixed procedure on an unreleased model, averaging three hours of ChatGPT Pro thinking compute per result, from about 4,000 problems posed ([README](https://github.com/openai/math)). Reported count at release was 722; the drop to 719 matches the withdrawals.
* **Headline claims in the release** (as listed by [Aaronson](https://scottaaronson.blog/?p=10169)): the Unique Games Conjecture, L = BPL, integer multiplication and the DFT below n log n, Hilbert’s tenth problem over the rationals, parity not in QAC0, a 2D area law, deterministic polynomial factorisation over prime fields, and partial progress on Riemann and BSD. The Hodge manuscript was retracted for a sign error.
* **Anthropic’s different model.** Alman and Williams’ 3SUM and APSP preprint used a key idea from an Anthropic model, with the humans writing and announcing a digested version ([arXiv 2610.06783](https://arxiv.org/abs/2610.06783)). Anthropic also formalised FLT in Lean: 13 million lines, 29,500 intermediate theorems, 11 days, statement checked against Mathlib by a comparator ([Anthropic](https://www.anthropic.com/research/formalizing-fermats-last-theorem)).
* **Community responses.** Leiden Declaration (June), Fields Medallists’ statement (11 Sep), AGMAI recommendations (29 Sep), AHM boycott call (7 Oct), Simons $15M programme (15 Oct), SAIR Open Math OS (16 Oct).

### Discussion prompt

Two release models are now on the table. OpenAI posts undigested proofs for anyone to work through; Anthropic routes results through chosen human authors. Aaronson asks which is better and names the weakness of each: a thankless race to digest messy proofs, or a company choosing which mathematicians become the AI’s emissaries. This is a good five-minute opener because nobody needs technical background to have a view.

---

## 2. What is the significance?

### Positions to put on the slide

* **Historic, and the work counts.** Aaronson calls 6 October one of the biggest days in mathematical history and says any one of several results would have been result of the year in its area. He dismisses the objection that the model failed on ~3,600 other problems by comparing it to asking Wiles about the theorems he did not prove ([Shtetl-Optimized](https://scottaaronson.blog/?p=10169), comments #91–92).
* **Impressive, but the problems were ripe.** A commenter on the same post argues that the 4D Kakeya and related harmonic-analysis results build on Hong Wang’s programme and were probably within human reach in months to five years (comment #24). Aaronson agrees that many of the complexity results looked within reach.
* **Capability characterised.** Aaronson’s own estimate (comment #115) is a first-year graduate student who knows every published technique, applies them anywhere, and works at scale with unlimited persistence. Useful as a slide because it is concrete and contestable.
* **Significance depends on understanding.** The AGMAI statement on the release calls it the beginning, not the completion, of human understanding, and says only the community can assess the results ([AGMAI](https://agmai.org/)). Dana Moshkovitz’s first-day reading of the UGC proof (quoted in Aaronson’s post) describes it as badly written but full of new ideas; by the next day she reported mostly understanding it with AI help.
* **A demonstration of power.** The AHM statement calls the release a demonstration of power and notes that OpenAI ignored its own advisory group’s advice not to test advanced problems on proprietary models ([coverage](https://pasqualepillitteri.it/en/news/21555/ahm-openai-demonstration-of-power)).

### Discussion prompt

What would it take for the group to call a result “significant”? Candidate criteria: correctness, novelty of method, whether a human understands it, whether it changes what others work on next. Ask people to rank them before showing the positions above.

---

## 3. Is this a permanent change to frontier research?

### Arguments for permanence

* Diffusion: Aaronson expects these capabilities to reach anyone with a commercial subscription within months, which makes a boycott unenforceable ([post](https://scottaaronson.blog/?p=10169)).
* Costs are falling: TheoPhysEval reports research-level physics calculations solved at under $3 a problem ([coverage](https://officechai.com/ai/gpt-6-astra-solves-49-50-unpublished-physics-research-problems-under-theophyseval-benchmark-for-3-a-problem/)).
* Infrastructure is being built around it: arXiv has capped submissions at two a month per author, Simons has funded a programme, SAIR is building open models ([Quanta](https://www.quantamagazine.org/is-ai-the-end-of-math-as-we-know-it-20261005/)).
* Behaviour is already shifting. Quanta reports mathematicians no longer posting open conjectures at the end of papers for fear of scraping, posting early to avoid being scooped, and MathOverflow activity declining.

### Arguments for caution

* Hit rate: 372 families from ~4,000 problems is about 9%. One sceptical commenter argues this is in line with earlier controlled experiments and suggests a plateau (Shtetl-Optimized comment #119). Counter-argument: OpenAI’s Navier–Stokes post reported far higher pass rates on a curated set, so the denominator matters (comments #74, #77).
* Verification is not done. Clay has not accepted Navier–Stokes; one manuscript has been retracted; the release README says unformalised results may have issues.
* The institutions may not adapt in time. Quanta’s essay is about incentive structures built around problem-solving: Litt’s line is that “the existing equilibrium has broken”.

### Futures to compare (from Quanta and Tao)

* **Bad equilibrium:** a generation trained to press a button and not read the output; Litt’s scenario in which nobody, human or machine, is doing maths in fifty years.
* **Interpreter role:** mathematicians digest, rewrite and connect AI output (Etingof’s view in Quanta).
* **Math 2.0:** Tao’s proposal that AI tools sustain the human community and the role of mathematical understanding, with less emphasis on automated solving of open problems ([post and slides](https://terrytao.wordpress.com/2026/10/10/math-2-0/); [video](https://aimath.org/videos/terry-tao-pl/)).

### Discussion prompt

Historical analogues to test against: the four-colour theorem (1976) and computer-assisted proof; the calculator in teaching; photography and painting (raised in Hacker News discussion of the Fields Medallists’ statement); Mochizuki’s abc proof as an example of an unreadable proof that the community could not absorb. Which analogue fits, and where does each break?

---

## 4. What does this mean for other subjects?

### Evidence

* **Theoretical physics.** TheoPhysEval: 50 unpublished problems that a world expert could solve in about a day; GPT-6 Astra in Codex got 49 right. Accuracy changed little without web search, which the authors read as memorisation of the literature. In several cases the model was right and the expert’s reference solution was wrong ([arXiv 2610.16733](https://arxiv.org/abs/2610.16733); [excerpt](https://humanprogress.org/?p=53825)).
* **Open problems in maths and physics.** OpenProblemBench (82 literature-grounded open problems): best judged solve rate 14%, with open-weight models at 5–7% ([arXiv 2610.11118](https://arxiv.org/abs/2610.11118)). Note the grading is by AI evaluators.
* **Research governance across science.** Nature’s June editorial argues that the Leiden Declaration should be a model for other disciplines, and reports evidence that AI use correlates with narrower research topics across science.
* **Theoretical CS.** Alman and Williams (3SUM, APSP); Busy Beaver results from an amateur using Claude Code (Aaronson’s 12 October update).
* **A physicist’s satire.** Rikab Gambhir’s guest post on Tao’s blog, “Why are we even doing all this?”, compares the output to Borges’ Library of Babel and argues the labs have outsourced checking and understanding to the community ([post](https://terrytao.wordpress.com/2026/10/15/why-are-we-even-doing-all-this/)). Good for provoking discussion; the comments contain the strongest counter-arguments (biotech researchers who care about results over understanding).

### The verifiability argument

The recurring theory in the comment threads: AI succeeds first where answers can be checked automatically (reinforcement learning from verifiable rewards). Maths with Lean, physics calculations with a numerical answer, and algorithms with benchmarks fit; empirical science with noisy data and slow experiments fits less well. Aaronson’s reply (comment #67) is that this does not mean messier domains are safe.

### Discussion prompt

Tao’s Caltech lecture includes a thought experiment about an AI-designed cancer treatment that passes trials but that no human understands. The comment thread pushes back from biomedicine: aspirin, penicillin and anaesthesia were used for decades before anyone understood the mechanism, and phase 3 trials set the bar for approval whatever the state of understanding. This contrast between maths (where understanding is the product) and medicine (where outcomes are the product) is a strong prompt for a mixed RSE audience. Ask: in your own field, is understanding the product or a means to it?

---

## 5. How is it done, and what does it mean for research and research IT?

### How it is done (summary for one or two slides)

* **Single-procedure runs:** one model, a fixed prompt procedure, around three hours of compute per result, thousands of problems ([README](https://github.com/openai/math)).
* **Agent swarms:** tens of thousands of concurrent agents coordinating by message, with a warm-up problem used to choose where to concentrate compute ([OpenAI N–S post](https://openai.com/index/navier-stokes-solution/)). One newsletter estimated the N–S run at over $40M; treat as an outside estimate ([Latent Space](https://latent.space/p/ainews-openai-reports-navier-stokes)).
* **Autoformalisation:** prose proof translated to Lean, then checked by the kernel. Comparator checks the formal statement against an independently written one (your deck covers this). Anthropic split statements and proofs into separate files to cut compile times on the FLT run.
* **Known failure modes of the verification layer:**
  * The statement can be wrong while the proof is right. Bastounis, Circelli and Hansen argue that faithful translation of informal maths is formally harder than the halting problem and show the Navier–Stokes Lean proof does not match the prose ([arXiv 2610.08144](https://arxiv.org/abs/2610.08144)).
  * The kernel can be wrong. Hales describes a summer of Lean soundness bugs, found by AI and security researchers, and proposes independent kernels, a verified kernel and a consistency proof for Lean’s type theory ([summary](https://ai-tldr.dev/releases/thomas-hales-lean-reliability-ai/); [Tao’s blog](https://terrytao.wordpress.com/2026/10/09/what-mathematicians-should-know-about-the-lean-theorem-proverquestions-of-reliability-and-ai/)).
  * The formal code may be unusable as a library. A commenter on Tao’s Math 2.0 post says almost none of the FLT code went into Mathlib because it is not library-style and is slow to compile (single source, treat as a claim).

### Implications for universities and research IT (discussion prompts)

* **Access and equity.** AGMAI warns of a two-tier system: labs with internal models ahead of everyone, and wealthy institutions ahead of poorer ones ([recommendations, §3](https://agmai.org/general-sep29/)). What does Sheffield’s access look like compared with the labs, and with other UK institutions?
* **Open alternatives.** SAIR’s Open Math OS hosts open models that Tao says are about a year behind the frontier, uses team accounts where colleagues see each other’s prompts, and offers free academic accounts on donated compute ([report](https://letsdatascience.com/news/sair-soft-launches-open-math-os-2fac7184)). Could a university run something similar on its own HPC?
* **Who pays.** Simons, Anthropic and OpenAI are putting in $15M plus compute ([Hyper.ai summary](https://hyper.ai/en/stories/e1e916b3ddbf84de115af25599c17f5d)). Critics call it a fig leaf. Who should fund verification and exposition: research councils, foundations or the labs?
* **Formal verification as research software.** Lean projects need CI, version pinning, reproducible builds (`lake build`), metadata (AGMAI asks for `formalization.yaml` and Comparator challenge files) and kernel cross-checks. This is RSE work. Who in a maths department does it now?
* **Repositories and provenance.** AGMAI wants AI results deposited in repositories not controlled by labs, with persistent identifiers, version history and comments, plus disclosure of model, prompts, summarised reasoning, time and cost. Institutional repositories and research data management teams could take this on.
* **Peer review load.** A commenter on Math 2.0 reports spending 40–50 hours refereeing a 15-page LLM-assisted paper; the QRH manuscript is about 200 pages. The LMS has a policy on AI in publications ([LMS](https://www.lms.ac.uk/news/leiden-declaration-on-ai-and-mathematics)).
* **Confidentiality of unpublished ideas.** If mathematicians stop sharing conjectures for fear of scraping, what guidance do universities give on using commercial models with unpublished work?

---

## 6. The jagged frontier: what does the map look like?

Gowers’ August post is the best single reading here. He tests the idea that LLMs are especially good at counterexamples, finds it too crude, and suggests the strengths come from broad knowledge and many attempts. His proposed sign of human-level ability is proofs with new methods that come to seem natural in hindsight ([discussion and summary](https://zeli.app/story/49270022); original on Gowers’s Weblog).

### Draft map (for a slide or the activity)

| Looks strong | Looks weak or unknown |
|---|---|
| Applying known techniques across many problems at scale (Tao, Gowers) | Writing for human readers: unreadable manuscripts, irrelevant citations (Moshkovitz; AGMAI) |
| Ripe problems near the edge of an active programme (Kakeya, complexity separations) | The deepest open problems: no P ≠ NP, P = BPP or cryptography results in the release (Aaronson) |
| Concrete calculations with checkable answers (TheoPhysEval 49/50) | Open problems with no prepared context: 14% best rate (OpenProblemBench) |
| Formalising known proofs at large scale (FLT) | Faithful statement translation; library-quality formal code (Bastounis et al.; Hales) |
| Long-horizon agent work on a chosen target with huge compute (N–S) | Research-level problems on public models under controlled conditions: 6–7 of 10 (First Proof) |
| Finding errors in expert solutions (TheoPhysEval) | Self-checking: Hodge sign error; unformalised results flagged as possibly wrong |

### What we can learn (prompts)

* Is the frontier jagged by **topic** (combinatorics versus algebraic geometry), by **task type** (calculation, proof, exposition, problem choice), or by **verifiability**? The evidence above leans towards task type and verifiability.
* Controlled versus uncontrolled evidence. Tao’s ICM talk leaned on First Proof as the rigorous evidence and treated lab announcements as press releases ([report](https://www.besthub.dev/articles/terence-tao-25-fields-medalists-warn-ai-math-breakthroughs-cause-proof-indigestion-f0133e851e71)). Most headline numbers in this brief come from the labs.
* Survivorship. The denominator (~4,000 problems) is published for the bulk release but the failed attempts are not, which AGMAI’s recommendation 5 asks for.

### Suggested activity (10–15 minutes, no install)

Give pairs eight cards, each a claim from the table above with its source. Ask them to place each on two axes: how verifiable the task is, and how much human understanding the result needs before it is useful. Then compare placements. This makes the jaggedness visible and links straight to questions 4 and 5.

---

## 7. Reading list

### Pre-reading for attendees (about 60 minutes in total)

1. Jordana Cepelewicz, [“Is AI the End of Math As We Know It?”](https://www.quantamagazine.org/is-ai-the-end-of-math-as-we-know-it-20261005/), *Quanta*, 5 Oct. The best general-audience overview of the human side.
2. Scott Aaronson, [“The Mathocalypse”](https://scottaaronson.blog/?p=10169), 7 Oct, with updates. The enthusiastic case, the list of results, and the two release models. Comments #24, #35, #48, #86, #115 and #119 are worth reading.
3. AGMAI, [“Responsible Release of AI-Generated Mathematics”](https://agmai.org/general-sep29/), 29 Sep. Short and concrete; useful for the verification and research-IT discussion.
4. Tim Gowers, “What sort of maths are LLMs good at?”, Aug (Gowers’s Weblog). For the jagged-frontier block.

### Foundational reading (in the AI for Mathematics project)

* Terence Tao, [“Mathematics in the age of AI”](https://arxiv.org/abs/2608.16753), ICM 2026 essay, arXiv 2608.16753. Sets capability claims aside, assumes the capabilities arrive, and asks what the goals and values of mathematical research are. Frames the present as a crisis of values and practices comparable to the foundational crisis of 1900–1930. The best framing piece for question 3.
* William P. Thurston, “On proof and progress in mathematics” (1994). The classic argument that the product of mathematics is human understanding, not proofs as such. Every current essay on this topic draws on it; useful as a reference point for questions 2 and 6.
* Nature editorial, “Mathematicians are developing rules for AI use — other fields should follow”, 18 June 2026. Endorses the Leiden Declaration and argues other disciplines should copy the approach; cites evidence that AI use correlates with narrower research topics across science. Direct input for question 4.
* Leiden Declaration full text (PDF in the project).

### Primary sources

* [`openai/math` repository](https://github.com/openai/math): README, overview PDF, reasoning summaries, Lean catalogue.
* [OpenAI: On the Navier–Stokes Millennium Prize Problem](https://openai.com/index/navier-stokes-solution/), 8 Sep.
* [Anthropic: Formalizing Fermat’s Last Theorem](https://www.anthropic.com/research/formalizing-fermats-last-theorem), 4 Sep.
* Alman and Williams, [3SUM and APSP preprint](https://arxiv.org/abs/2610.06783).
* [Leiden Declaration](https://leidendeclaration.ai/), Jun.
* “A Severe Misalignment of AI in Mathematics”, Tao’s blog, 11 Sep ([coverage](https://www.implicator.ai/25-fields-medalists-say-ai-labs-race-to-solve-math-problems-is-harming-mathematics/)).
* [AHM statements](https://www.ahmath.org/statements).
* [First Proof](https://1stproof.org/) results, first and second batches.

### Critiques and verification

* Bastounis, Circelli and Hansen, [“Navier–Stokes lost in translation”](https://arxiv.org/abs/2610.08144).
* Thomas Hales, [“What mathematicians should know about the Lean Theorem Prover”](https://terrytao.wordpress.com/2026/10/09/what-mathematicians-should-know-about-the-lean-theorem-proverquestions-of-reliability-and-ai/), guest post on Tao’s blog, 9 Oct.
* Rikab Gambhir, [“Why are we even doing all this?”](https://terrytao.wordpress.com/2026/10/15/why-are-we-even-doing-all-this/), 15 Oct (satire).
* Lior Pachter, [post on the Fields Medallists’ statement](https://liorpachter.wordpress.com/2026/09/12/align-ai-and-mathematics-to-something-else/), 12 Sep. Agrees with the Fields Medallists about the labs but criticises their own haste.

### Essays collected by Tao (12 Oct), not yet read for this brief

Tao’s [list](https://terrytao.wordpress.com/2026/10/12/additional-recent-pieces-on-math-and-ai/) spans a wide range of views. Titles only; I have not checked their content.

* Kevin Buzzard, [“To grieve, or not to grieve?”](https://xenaproject.wordpress.com/2026/10/01/to-grieve-or-not-to-grieve/)
* Harald Helfgott, [“Mathematics and the AI crisis”](https://valuevar.wordpress.com/2026/10/01/mathematics-and-the-ai-crisis/)
* Gil Kalai, [“Be a Grothendieck!”](https://gilkalai.wordpress.com/2026/09/22/be-a-grothendieck-on-ai-and-mathematics/)
* Matilde Marcolli, [“Duet for the end of math”](https://www.its.caltech.edu/~matilde/AImathNew.pdf) (LMS Newsletter essay; quoted in Quanta)
* Alexander Gamburd, [“The Siren Call of Silicon Leviathan”](https://arxiv.org/abs/2609.28591)
* Fenner Stanley Tanswell, [“Enshittification of Mathematics”](https://link.springer.com/article/10.1007/s00283-026-10566-7)
* Asaf Karagila, [“OpenAI, the Partition Principle, and mathematics”](https://karagila.org/2026/openai-pp/)
* From the comments: David Roberts, [“What even is mathematical output?”](https://thehighergeometer.wordpress.com/2026/10/12/what-even-is-mathematical-output/); Aaron Slipper’s [response to the AHM](https://aaronslipper.github.io/assets/math-and-ai-response-to-the-ahm.pdf); Christian Szegedy, [“Is Mathematics Over, or Just Graduating?”](https://docs.google.com/document/d/e/2PACX-1vTSh-pyNP3Gi99WMmsinnLmE9V5CDI0HEm6WGbIPMNt3V5SGlClHF8-BetotKHOImrvQDSXmFdiOw8D/pub); Jason Polak on [whether to do a PhD](https://jasonpolak.substack.com/p/ai-does-math-should-you-get-a-phd).
* Dakshita Khurana, [“Classical at heart”](https://dakshitakhurana.substack.com/p/classical-at-heart): a researcher working through the AI proof of a problem she spent years on (linked by Aaronson).
* Kunal Marwaha, [World Mathematical Commons](https://worldmathcommons.org/).

### Video and audio

* Terence Tao, [“Math 2.0”](https://aimath.org/videos/terry-tao-pl/), Caltech public lecture, 9 Oct ([slides](https://teorth.github.io/tao-web/slides/math-2-0-caltech-2026.pdf)). The best single talk for this session.
* [“No More Heroes: Terence Tao Talks to Numberphile About AI”](https://www.youtube.com/watch?v=bAnwMdfcMVw), 15 Oct. Short and accessible; a clip could open the session.
* Tao, [“The integrated explicit analytic number theory network”](https://www.youtube.com/watch?v=Boo72U-9u3c), IPAM, 17 Sep: a working example of human–AI collaboration at scale.
* Hugo Duminil-Copin, [8 Oct talk](https://www.youtube.com/watch?v=iRjasLnigsU), reported for its personal and emotional candour (not checked).
* NYT *The Daily*, [mathematicians and AI jobs](https://www.nytimes.com/2026/10/13/podcasts/the-daily/mathematicians-problem-ai-jobs.html), with Steven Strogatz, 13 Oct (paywall).
* NYT, [“I’m on a War Footing”](https://www.nytimes.com/2026/10/16/us/math-ai-terence-tao.html), Tao interview, 16 Oct (paywall).

### Running trackers

* Tao’s AI-maintained [summary of his views](https://teorth.github.io/tao-web/ai-views.html) and [list of talks and posts](https://teorth.github.io/tao-web/mastodon-posts.html).
* [Proofs and Prompts](https://proofsandprompts.com/), including [“100+ reactions to 100+ solutions”](https://proofsandprompts.com/2026/10/08/100-reactions-to-100-solutions/).
* Klas M.’s (Umeå) [preprint growth tracker](http://abel.math.umu.se/~klasm/).

---

## 8. Notes on the existing deck (PR #14)

* **Manuscript count.** The README now says 719 manuscripts in 372 families; 722 was the count at release. Worth stating both and linking the difference to the withdrawals.
* **Aaronson’s numbers are inconsistent within his own post** (372 results in one place, 376 papers in another). Use the README’s figures.
* **Hit rate.** If you quote ~10%, say it is families over problems posed, and that the N–S curated set had a much higher pass rate. Both are lab-reported.
* **Formalisation coverage.** The README gives ~42% of top-line results formalised; useful alongside the “lost in translation” slide.
* **N–S cost.** The >$40M figure is a newsletter estimate. OpenAI published tokens and messages, not cost, which is one of AGMAI’s disclosure asks.
* **Missing from the deck, by the look of the PR summary:** the Fields Medallists’ statement, First Proof as the controlled counterpoint, TheoPhysEval for the “other subjects” question, SAIR and Simons for the research-IT question, and Anthropic’s FLT formalisation as the contrasting release model.
