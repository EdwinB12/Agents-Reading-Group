# Research note: the "jagged frontier" and what sort of maths LLMs are good at

**Main source:** Tim Gowers, [What sort of maths are LLMs good at?](https://gowers.wordpress.com/2026/08/12/what-sort-of-maths-are-llms-good-at/),
Gowers's Weblog, 12 August 2026
([Hacker News discussion](https://news.ycombinator.com/item?id=49270022)).

**Also drawing on:** Dell'Acqua, Mollick et al. (2023) for the term "jagged frontier"; Karpathy
(2024) for "jagged intelligence"; Sarnak's "AlphaZero test"; Zahavy's "LLMs can't jump"; Gangloff's
taxonomy of mathematical creativity; and Tao's [Math 2.0](tao-math-2-0.md) lecture. Full links are
under [Sources](#sources).

**Added:** 18 October 2026

> The research brief ([§6](claude-mathpocalypse-research-brief.md)) calls Gowers's post the best
> single reading on the jagged frontier. These notes summarise it section by section, put it next
> to a few other analyses, and end with a working map that can be used for a slide or the card
> activity. The 3Blue1Brown video ([notes](3blue1brown-better-time-for-math.md)) raises the same
> question from the other end: if proofs become cheap, what do humans do? Gowers instead asks which
> proofs are becoming cheap, and which are not cheap yet.

## 1. Where the phrase comes from

- **"Jagged technological frontier" (2023).** The phrase comes from a pre-registered field
  experiment with 758 Boston Consulting Group consultants using GPT-4. The authors suggest AI
  capability forms a frontier "where some tasks are easily done by AI, while others, though
  seemingly similar in difficulty level, are outside the current capability of AI". On 18 tasks
  inside the frontier, consultants with AI completed 12.2% more tasks, worked 25.1% faster and
  produced work rated more than 40% higher in quality. On one task chosen to sit *outside* the
  frontier, consultants with AI were **19 percentage points less likely** to get the right answer
  than those without it. (These figures are from the working paper's abstract. Secondary write-ups
  often say 12.5%.)
- **"Jagged intelligence" (2024).** Andrej Karpathy's term for the same shape seen from the model's
  side: a model that does very hard things and then fails a trivial one, such as saying 9.11 is
  bigger than 9.9. His point is that human abilities tend to improve together, while a model's
  peaks and troughs are neither correlated nor easy to predict.
- **In maths (2026).** Tao's Math 2.0 lecture lists "capability is jagged" as one of his framing
  points. AI is astounding at some tasks and inadequate at others, and reporting bias hides the
  failures ([notes](tao-math-2-0.md)).

There are two lessons for the session. First, the edge is **invisible**: you cannot tell from how
hard a task looks which side of the line it falls on. Second, the costly mistakes happen just
**outside** the edge, where people trust the tool and should not.

## 2. Gowers: "What sort of maths are LLMs good at?"

### 2.1 Context and framing

- The post came out days after OpenAI's "ten advances" announcement, which included the first
  construction of a **non-sofic group** and a **superexponential lower bound for the multicolour
  Ramsey number R(3,3,…,3)**.
- Gowers calls the post a snapshot of early August 2026. He expects it to date quickly.
- His starting point: LLMs are clearly very strong, but they are not better than every human at
  every kind of maths. If they were, their speed would already have produced a far larger flood of
  results. So the interesting question is *which* kinds.

### 2.2 The counterexample hypothesis, and why it is too crude

The obvious observation is that the most famous LLM results are counterexamples: the non-sofic
group, the Ramsey bound, and claims on the Jacobian conjecture and the unit distance problem.
Gowers takes this seriously and then breaks it down.

- **Logical form doesn't settle it.** Vinogradov's three-primes theorem can be written in a
  form whose negation is "there is a counterexample". Yet nobody calls it a counterexample result,
  because the work goes into handling a large *n*, not into hunting for a bad case. Gluskin's
  Banach–Mazur result has the same ∃∀∃ shape but *is* thought of as a counterexample, because
  choosing the dimensions is trivial and separating the spaces is the real work. Whether something
  counts as "finding an example" depends on where the difficulty lies, not on the quantifiers.
- **Many proofs are existence proofs in disguise.** You prove the torus and the sphere are not
  homeomorphic by *exhibiting* an invariant. A separation theorem is equivalent to a linear
  functional *existing*. In everyday research you are constantly looking for an object: a
  strengthened statement to induct on, or an intermediate property. Gowers says his real question
  about Goldbach would be "what could a proof be like?" rather than "why is it true?".
- **Example versus counterexample.** A counterexample disproves something people had reason to
  believe. Showing ℓ∞ is non-separable gives an *example*, because nobody expected all Banach spaces
  to be separable. On the Ramsey result, Gowers had worked on the problem himself, and says that
  "for me OpenAI found an example of what I (weakly) expected."

He concludes with three facts. (1) The most notable LLM results are examples or counterexamples.
(2) What counts as an example depends on context and phrasing. (3) LLMs **can** prove universal
statements, but their best proofs are not yet at the level of their best counterexamples.

> Several press headlines turned this into "the breakthroughs are counterexamples, not proofs".
> That is a flattening Gowers explicitly rejects: "LLMs are not just good at finding
> counterexamples: they can find proofs of difficult statements as well."

### 2.3 The real explanation: breadth and volume

Gowers thinks LLMs are good at something more basic, which happens to favour existence problems.

- **Broad knowledge.** If a problem gives way to a "relatively standard argument" from *somewhere*
  in the literature, an LLM is likely to find it. No human knows that much of the literature.
- **Speed and volume.** They can afford a great many failed attempts.

He contrasts an **"LLM style"** of "try-lots-of-things-till-you-get-lucky" with a **human style** of
digging deeper until the solution reveals itself. Experts often react in the same sequence: first
amazement that the problem was solved, then the realisation that the approach was not very novel.

### 2.4 Eight ways to search for a counterexample

This section is the most useful one for the session: it is a concrete account of where the jagged
edge falls inside a single task type.

| # | Method | Suits LLMs? |
|---|---|---|
| 1 | **Off-the-shelf examples.** Try the standard zoo first; O'Donnell's advice for Boolean functions is "dictators, majority, parity, tribes" | Yes: breadth |
| 2 | **Build from basic examples** using products, quotients and limits | Yes: breadth |
| 3 | **Metavariables:** "where *x* is to be chosen later" | Needs a "nose" |
| 4 | **Try to prove the negation** to find the key obstacle | Needs a "nose" |
| 5 | **Successive approximation** | Needs a "nose" |
| 6 | **Just-do-it inductive constructions** | Yes: volume |
| 7 | **Random examples** (the probabilistic method) | Yes: volume |
| 8 | **Generic examples** (the bad set is small or has measure zero) | Yes: breadth |

Methods 3–5 depend on judging, part-way through, which direction looks promising. That is where
Gowers thinks humans may still have an edge: a **nose for pruning a huge search tree**.

### 2.5 Doubts about the LLM "nose"

- **First-hand experience.** In his own use of GPT-5.6 Pro, approaches that look promising tend to
  fall apart when he examines them. Answers often end "I have not managed to answer the question
  you asked, but have managed to reduce it to…", and the next round does the same without
  progress.
- **Possible reasons:**
  - The training data is full of tidied-up proofs, not the thinking that found them.
  - Humans learn "by *doing* rather than *emulating*".
  - LLMs "will lack the incentive that humans have to prune the search tree ruthlessly". Brute
    force hides the inefficiency.
- **Suggested experiments.** Test weaker models kept away from the relevant literature, and
  change the rewards so that dead ends and copying from the literature are penalised.

### 2.6 A test for human-level ability

- Gowers would be convinced by a proof "as surprising to me as the solution of the cap-set
  problem" (2016), where the previous bounds were blown away by a new method.
- More generally, the sign would be proofs that are **"new and surprising but that with hindsight
  come to seem beautiful and natural"**, and that would be hard to stumble on by accident.
- He admits "it is hard to say precisely" what counts, but adds "I think we'll recognise it when
  we see it."

This test cuts *against* the try-lots-of-things style. A lucky hit is rarely natural in
hindsight, while a method that becomes the obvious way to do it afterwards usually came from
understanding. So Gowers's bar is not about difficulty. It asks whether the result changes what
mathematicians find natural, which links straight to the [3Blue1Brown](3blue1brown-better-time-for-math.md)
theme of theory building as the real creative work.

### 2.7 From the comments

The visible comments are mixed. Many are off topic, and some are hostile or spam; I have not
treated those as evidence. Three are worth knowing about:

- A heavy daily user of Pro models argues that the skill lies in asking the next good question and
  managing context, and that benchmark scores don't reflect real use.
- An anonymous commenter suggests LLMs favour counterexamples partly because *true* conjectures are
  harder to state well. They also argue that success should be measured as pass@k (success within
  *k* attempts), which fits the volume explanation.
- Another suggests that a statement and its negation sit close together in embedding space, which
  might make "try the negation" cheap for a model.

## 3. Other analyses of the same question

### 3.1 Sarnak: the "AlphaZero test"

As reported in Gamburd's essay (below) and *The Decoder*, Peter Sarnak's July 2026 AMS *Notices*
piece proposes this test: give a prover **no outside data or theory**, and ask it to prove the
Ramanujan conjecture as Ramanujan stated it. He predicts failure on theorems "whose present-day
proofs make use of abstraction, conceptualization and the development of a body of theorems". What
it would produce instead is "the elementary statistical derivatives of the theories", in the way
Stockfish extends human chess theory. If it *did* succeed, "we will have to rethink what mathematics
is." This is Gowers's "nose" point pushed further: the hard part is not pruning a search tree but
**building the abstractions that make the tree small**.

### 3.2 Gamburd: Stockfish, not AlphaZero

Alexander Gamburd's long essay
[The Siren Call of Silicon Leviathan](https://arxiv.org/abs/2609.28591) (arXiv, Sept 2026) is
mainly about understanding versus certification. Section II applies Gowers and Sarnak to the
8 September Navier–Stokes run and argues that it was **more Stockfish than AlphaZero**, because it
started from the existing literature (including the Córdoba–Martínez-Zoroa construction, which he
calls "analysis and not search"). It also says the 166 pages have not yet faced Gowers's
natural-in-hindsight test. The essay is gloomier than this session's framing, and is useful as the
strongest form of the sceptical case.

### 3.3 Zahavy: "LLMs can't jump"

Tom Zahavy (Google DeepMind) argues in a position paper (January 2026) that generative AI has
mastered induction and is quickly mastering deduction, but lacks **abduction**: coming up with new
explanatory hypotheses. Ordinary abduction (picking the best explanation from known candidates)
models can do. What they lack is **"manipulative abduction"**: inventing a cause or framework for
which no linguistic template yet exists. His case study is general relativity, and he suggests
grounded world models as a way forward. *The Decoder* paired this with Gowers and Sarnak under the
headline "LLMs can't jump, Part II".

### 3.4 Gangloff: creativity is several capabilities, not one

Silvère Gangloff, [Assessing LLMs' mathematical abilities requires understanding the various
mechanisms of mathematical creativity](https://arxiv.org/abs/2608.16118) (arXiv, 17 August 2026),
proposes four distinct modes of mathematical creativity:

1. reflecting on mathematical practice itself;
2. importing analogies from the sciences;
3. construction driven by a specific problem;
4. bridging distant domains.

He argues the modes are **non-substitutable**: being good at one says little about the others.
Current systems concentrate their competence in the modes that rest on recombination and search
(roughly mode 3). He wants evaluations organised by mode rather than aggregate benchmarks, which
"conflate" them. This is the most useful *structural* explanation of jaggedness here. The frontier
is jagged because "maths ability" was never one thing.

### 3.5 Tao: jaggedness plus reporting bias

Tao's contribution (see [Math 2.0 notes](tao-math-2-0.md)) is methodological. We see the peaks
because successes are press-released and failures are not. He asks for assessments that report
compute and failed attempts, and points to [First Proof](https://1stproof.org/) as a controlled
example. Without that, any map of the frontier is drawn from survivors.

## 4. A working map

Putting these together, the evidence suggests the frontier is jagged along **task type** more than
**topic**. Three questions seem to predict which side a task falls on:

1. **Can the answer be checked mechanically?** Lean, a computation, an explicit object. If so,
   volume pays off, because failed attempts are cheap to throw away.
2. **Is there a known technique somewhere in the literature that, suitably combined, does the
   job?** If so, breadth pays off.
3. **Does progress need judgement mid-search, or a new abstraction?** If so, this is where Gowers
   (nose), Sarnak (abstraction), Zahavy (abduction) and Gangloff (non-search modes) all place the
   current limit.

| Probably inside the frontier | Probably at or outside the edge |
|---|---|
| Finding explicit (counter)examples, especially from standard families or random constructions (Gowers methods 1, 2, 6–8) | Constructions needing metavariables, successive approximation, or a feel for where to aim (methods 3–5) |
| Problems that fall to a "relatively standard argument" someone, somewhere, has used before | Proofs that are surprising yet natural in hindsight, such as the cap-set solution (Gowers's bar) |
| Extending an existing theory: "statistical derivatives" (Sarnak) | Building the theory or abstraction first (Sarnak's AlphaZero test; Zahavy's "jump") |
| Long, checkable, compute-heavy agent runs on a chosen target that starts from the literature (N–S, as Gamburd reads it) | Knowing which questions are worth asking (3Blue1Brown; Gangloff's "strategic" conjectures) |
| Recombining and searching over existing building blocks (Gangloff mode 3) | Analogy from the sciences, bridging distant fields, reflecting on practice (Gangloff modes 1, 2, 4) |

This agrees with the brief's draft map, which leans towards "task type and verifiability". It
adds Gowers's sharper point that the edge cuts *through* a single task type, such as counterexample
search, depending on how much pruning the search needs.

**Two caveats on any map.** The frontier **moves**: Gowers dates his post, and the BCG paper's
frontier is GPT-4's. And the evidence is **survivor-biased** (Tao), so the right-hand column may
partly reflect what nobody has reported trying.

## 5. Why this is good news (the session's angle)

- **A division of labour is emerging.** The left-hand column is a lot of the routine work in
  research: checking the standard examples, recalling the right lemma, grinding through cases. If
  machines take that on, more human time goes to the right-hand column, which is the part most
  mathematicians say they came for. Gowers's tests describe what humans are still uniquely good
  at, not a ceiling on what AI can do.
- **The BCG warning carries over.** Consultants did worse when they trusted AI on a task just
  outside the frontier. The maths equivalents are accepting a faithful-looking but wrong Lean
  statement, or a "reduction" that goes nowhere. Knowing where the edge is is the skill: the
  centaur or cyborg working patterns from the BCG paper, applied to proofs. RSEs will recognise
  this from agent-written code.
- **Tests that can be falsified.** Gowers's natural-in-hindsight test and Sarnak's AlphaZero test
  are concrete. They give the group something to watch for rather than something to dread.

## Discussion prompts

1. Gowers's eight search methods split into "breadth/volume" and "needs a nose". Is there an
   equivalent split in *your* research software work, between what agents do well and what still
   needs you?
2. Is "natural in hindsight" a fair test for AI, or one that most human papers would fail too?
3. Sarnak's AlphaZero test bans outside data. Is that a test of *mathematical* ability, or an
   unfair handicap no human works under?
4. The BCG study found people did *worse* with AI on tasks just past the frontier. Where is the
   "19-point drop" most likely to bite in AI-assisted maths: statement faithfulness, citations,
   or plausible-looking dead ends?
5. If the frontier moves every few months, what is the durable skill: knowing where it is today,
   or knowing how to find out?

## Caveats for the session

- **Gowers post:** the summary comes from a full read of the post body. The comment thread was only
  partly read (about 90%), and the comment summaries are of the more substantive ones only.
- **Sarnak:** the *Notices* article itself was not found. His quotes here come from Gamburd's essay
  and *The Decoder*; check them against the AMS original before quoting on a slide.
- **Zahavy:** read via secondary sources and the PhilSci-Archive listing. I could not confirm an
  arXiv ID.
- **Gangloff:** summarised from the abstract only; the historical case studies were not read.
- **BCG figures** come from the working paper (HBS 24-013, 22 Sept 2023). A revised version was
  later published in *Organization Science*, and its figures may differ slightly.
- If any of these are cited in the slides or README, add BibTeX entries to `references.bib`.

## Sources

- T. Gowers, [What sort of maths are LLMs good at?](https://gowers.wordpress.com/2026/08/12/what-sort-of-maths-are-llms-good-at/), 12 Aug 2026.
- F. Dell'Acqua, E. McFowland III, E. Mollick, H. Lifshitz-Assaf, K. C. Kellogg, S. Rajendran,
  L. Krayer, F. Candelon, K. R. Lakhani, [Navigating the Jagged Technological Frontier](https://papers.ssrn.com/abstract=4573321),
  HBS Working Paper 24-013, Sept 2023.
- A. Karpathy, "jagged intelligence" post on X, July 2024 (as reported in
  [AOL/Business Insider](https://www.aol.com/ai-leaders-term-fact-models-205518002.html)).
- M. Bastian, [Top mathematicians say LLMs are strong calculators but poor creative thinkers](https://the-decoder.com/top-mathematicians-say-llms-are-strong-calculators-but-poor-creative-thinkers/),
  *The Decoder*, 16 Aug 2026 (Gowers, Sarnak, Zahavy).
- A. Gamburd, [The Siren Call of Silicon Leviathan: Reflections on blowup and Aufklärungsdämmerung](https://arxiv.org/abs/2609.28591),
  arXiv:2609.28591, Sept 2026.
- T. Zahavy, [LLMs can't jump](https://philsci-archive.pitt.edu/28024/), PhilSci-Archive, Jan 2026.
- S. Gangloff, [Assessing LLMs' mathematical abilities requires understanding the various mechanisms of mathematical creativity](https://arxiv.org/abs/2608.16118),
  arXiv:2608.16118, Aug 2026.
- T. Tao, Math 2.0 lecture: see [tao-math-2-0.md](tao-math-2-0.md).
