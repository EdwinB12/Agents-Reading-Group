# Research note: Scott Aaronson, "The Mathocalypse"

**Source:** [The Mathocalypse](https://scottaaronson.blog/?p=10169), *Shtetl-Optimized*, posted
7 October 2026, updated 9 and 12 October. The notes also cover the comment thread, which had 338
responses (61 of them from Aaronson) when it was read.

**Added:** 18 October 2026

> These are summary notes with short quotes, not a transcript. Comment numbers link to the comment.
> Aaronson's counts are not consistent: the post says "372" results in one place and "376 papers" in
> another, and his first estimate of ~8,000 problems tried (~5% success) was corrected to ~4,000
> (~10%). Use the [`openai/math` README](https://github.com/openai/math) figures on slides (see the
> [research brief](claude-mathpocalypse-research-brief.md), §8). For his spoken version of the same
> argument, see the [Modern CTO interview note](aaronson-modern-cto-interview.md).

## 0. Where the session title comes from

- **Aaronson coined "Mathocalypse"** (no *p*) for the 6 October OpenAI release. He admits he
  "vacillated between the two spellings"
  ([#44](https://scottaaronson.blog/?p=10169#comment-2041125)).
- **A commenter pushed for the *p*.** Daniel Reeves "kept wanting to say 'mathpocalypse'"
  ([#40](https://scottaaronson.blog/?p=10169#comment-2041119)) and later voted to switch, because
  it keeps the "MATH" syllable intact
  ([#203](https://scottaaronson.blog/?p=10169#comment-2041354)). Aaronson stuck with his version
  because it "puts slightly more emphasis on the 'math' part, relative to the 'apocalypse' part"
  ([#204](https://scottaaronson.blog/?p=10169#comment-2041355)).
- So our title takes the commenter's side of a spelling argument. Aaronson's reason for his
  spelling (more maths, less apocalypse) also suits the session's tone.

## 1. The enthusiastic case

- **"One of the biggest days in mathematical history."** The post opens with Aaronson's
  9-year-old son teasing his mother, complexity theorist Dana Moshkovitz, that a robot had solved
  the problem she had worked on for her whole career (the Unique Games Conjecture). Aaronson's
  verdict: "while my son was being a brat, he also wasn't wrong."
- **Any one result could be "result of the year".** That applies within its area, and for UGC
  and L = BPL across all of CS theory. His shortlist of "treasures from Aladdin's cave", all from
  his own fields:
  - Unique Games Conjecture (with a Lean certificate)
  - L = BPL (probabilistic and deterministic logspace are equal)
  - Integer multiplication and the DFT below O(n log n), roughly O(n log^0.9999999999999 n)
  - Unitary Synthesis Problem, solved positively. Aaronson and Kuperberg posed it in 2007, and
    the answer is the opposite of what most people expected
  - Parity not in QAC0
  - A nearly quartic randomized-vs-quantum query separation (a favourite of his since 1998)
  - A superquadratic sensitivity vs block-sensitivity separation
  - An area law for 2D gapped Hamiltonians
  - Matrix multiplication in n^(9/4+o(1)), by a different route from the n^2.373 line
  - An Ω(n³) lower bound on the determinantal complexity of the permanent
  - Matching results: an FPRAS for counting perfect matchings, near-linear maximum matching
  - Deterministic polynomial factorisation over prime fields, without assuming GRH
  - Hilbert's tenth problem over the rationals shown undecidable
  - Partial progress on Riemann, Hodge (later retracted for a sign error) and Birch and
    Swinnerton-Dyer
- **What is missing.** P ≠ NP, P = BPP and NEXP ⊄ P/poly are absent, "and surely not for lack of
  trying". A later update notes that cryptography is "conspicuous by its absence". He also reports,
  from unnamed sources, that labs have started quietly testing whether internal models can break
  cryptographic primitives.
- **Not a bespoke super-system.** Navier–Stokes used a 10,000-agent run. This release came from
  the standard internal model, at about 3 hours of GPT-Pro-level compute per problem, and could
  reach paying customers "within the next couple of months". (Aaronson asked for a source for the
  3-hour figure in [#15](https://scottaaronson.blog/?p=10169#comment-2041082); the README now
  states it.)
- **No practical payoff yet, and that misses the point** (9 Oct update). Nobody will deploy the
  new FFT, but "anyone who harps on this, simply doesn't understand what mathematical progress
  looks like". The ideas pay off once humans understand them, and that is "yet another reason to
  try to keep human understanding at the center of our enterprise".

## 2. Two ways to release AI maths (the suggested opener)

One day before the OpenAI release, Alman and Williams posted sub-quadratic 3SUM and
sub-cubic APSP ([arXiv 2610.06783](https://arxiv.org/abs/2610.06783)), with the key idea from an
Anthropic model. Aaronson sets out the two release models:

| | "OpenAI model" | "Anthropic model" |
|---|---|---|
| What is released | Undigested AI proofs, posted to everyone at once | A digested version written and announced by chosen human authors, who are paid |
| Weakness Aaronson names | "a crazy race among humans to digest and explain a messy AI proof", work that could be "thankless, barely-credited, competitive, and unfun" | "puts a private company in the position of picking and choosing which human mathematicians get to be the emissaries of the AI" |

He leaves it open: "Dunno, what do you guys think?" In the comments, a third option comes up:
allocate model time the way astronomers allocate telescope time, with first-publication rights
for the people granted access. Aaronson likes the idea but points out the catch: it's like fighting
over JWST time "while … anything the JWST saw, could be seen just as well by next year's backyard
telescopes" ([#318](https://scottaaronson.blog/?p=10169#comment-2041635)).

## 3. What it feels like: Dana Moshkovitz's first-day reading of the UGC proof

Aaronson quotes his wife's texts, and they give the most concrete picture of what digesting
these results involves:

- "It feels like something written by someone who's on psychedelics."
- "The paper is so horribly written that it's impossible to read it without AI help."
- "It's not the long code, not the short code – some alien craziness."
- "A possible future is a math world that's heavenly if you have vision/creative ideas that AI
  could help check and implement … there's a lot for us to learn from the aliens."

The arc in the comments is the optimistic part. The same evening she was asking the model to
explain the construction and "starting to understand" it
([#32](https://scottaaronson.blog/?p=10169#comment-2041110)). By the next day she "now mostly
understands the proof … is amazed by the new ideas in it, and wants to give talks about it soon"
([#94](https://scottaaronson.blog/?p=10169#comment-2041191)).

Aaronson's metaphor for the field is a hunter-gatherer whose rainforest suddenly has a resort
hotel next door: "alright fine, so now my new job is to run wilderness retreats for the tourists,
or something." Responding to Quanta's teleported-to-a-foggy-peak image, he is optimistic that
"we can do as we always have: clear the fog and figure out the path, except now using the
teleportation machine to help guide us", and adds that "we still do have each other".

## 4. The three comments in the brief

### #24: "the problems were ripe anyway"

[Seb, #24](https://scottaaronson.blog/?p=10169#comment-2041098): the 4D Kakeya proof and the
3D harmonic-analysis breakthroughs "build heavily on the work that Hong [Wang] and other people
have been doing", and were "very likely … within human reach in anything from a few months to ~5
years".

Aaronson **agrees**
([#27](https://scottaaronson.blog/?p=10169#comment-2041102)): in complexity and quantum
information too, "many, many of these problems … looked in reach for humans and … humans were
maybe even closing in on". He then says how torn he is: "it's extremely important for me to
preserve a thriving human mathematical community, but it's also extremely important for me to
preserve the ideal that our problems are open to absolutely anyone … even if they're an 'evil
corporation'!"

*For discussion:* "ripe" cuts both ways. It deflates the achievement, but it also means the AI
took results that particular humans were about to claim. That is the scooping worry Quanta
reports.

### #115: "a first-year grad student who knows every published technique"

Asked whether the model is closer to a well-read grad student or "Gödel plucking novel methods
from the mind of God" ([Chris, #114](https://scottaaronson.blog/?p=10169#comment-2041219)),
Aaronson answers ([#115](https://scottaaronson.blog/?p=10169#comment-2041220)):

> closer to a normal first year math graduate student who happens to know every existing published
> technique and can apply them to arbitrary new domains, and can do for thousands of problems in a
> few weeks, with unlimited motivation and persistence …

He adds that such a human, "even 100x slower", would be spoken of alongside Euler or Erdős. He
notes that this is four years on from "struggling with basic arithmetic", and that the model has
creativity "exceeding 99.999% of humans'". Whether it can match the greatest mathematicians
"remains an open question".

Related replies from Aaronson that fill out his view of its abilities:

- **Strengths.** It is especially good at "weird counterexamples, algorithms, and
  constructions", where it can parallelise and "isn't discouraged by the possibility that what
  it's looking for doesn't exist" — but "it's increasingly beating us at the other stuff too"
  ([#307](https://scottaaronson.blog/?p=10169#comment-2041607)).
- **Conjectures.** The best models do "a creditable job — analogous to what a beginning grad
  student might do". Humans keep an edge for now, "but I wouldn't count on it"
  ([#276](https://scottaaronson.blog/?p=10169#comment-2041508)).
- **Why the write-ups are unreadable.** Partly the companies not putting effort in, and partly
  the models not yet having "a good enough model of what a human expert would or wouldn't care
  about or find obvious" ([#325](https://scottaaronson.blog/?p=10169#comment-2041662)).
- **No proof is "ungraspable" in principle.** Some proofs might take more than a human lifetime
  to understand, "a good time to ask the AIs to start working on radical life extension"
  ([#270](https://scottaaronson.blog/?p=10169#comment-2041500)).

### #119: "the hit rate shows a plateau"

[Anononan, #119](https://scottaaronson.blog/?p=10169#comment-2041228) makes four points:

1. 372/4,000 ≈ 10% is in line with earlier controlled experiments (the DeepMind report, First
   Proof, FrontierMath Erdős), so "it looks like these systems are plateauing". Problem
   difficulty is subjective.
2. OpenAI does not say the results came from a single standard prompt, so they may owe a lot to
   the humans who prompted.
3. Compute per problem was modest compared with Navier–Stokes, but the problems may also have
   been easier.
4. The output still needs the "full stack" of human expert work: interpretation, checking and
   novelty review. The commenter also suggests the release was timed to get ahead of the third
   First Proof batch.

Aaronson doesn't answer #119 directly, but he had already dismissed the hit-rate argument in
reply to similar comments. He compares it to asking Andrew Wiles about "all the math problems you
couldn't solve" ([#91](https://scottaaronson.blog/?p=10169#comment-2041180)), and calls dismissing
"376 major open math problems in a few weeks" over the failures "batshit insane"
([#92](https://scottaaronson.blog/?p=10169#comment-2041188)). Replies from other commenters:

- **Luke ([#151](https://scottaaronson.blog/?p=10169#comment-2041267))** argues there is no
  evidence of a plateau. We don't know that 372/4,000 is the full count; a hit rate on major open
  problems isn't comparable with one on Erdős problems; and unsaturated benchmarks still show
  gains (OpenAI's internal curated set at about 45% against below 20% for Astra; Astra's first
  non-zero FrontierMath Erdős score). These are lab-reported numbers.
- **The denominator matters**
  ([#74](https://scottaaronson.blog/?p=10169#comment-2041159),
  [#77](https://scottaaronson.blog/?p=10169#comment-2041162)). The Navier–Stokes post's
  "curated set of open math problems" peaked at a pass rate of about 44%, so 10% versus 45% may
  depend on who picked the problems.
- **Jair ([#136](https://scottaaronson.blog/?p=10169#comment-2041250))** replies with satire:
  an athlete who broke 300 world records in a few weeks, "but his dirty secret was, he just tried
  everything!" Aaronson: "ROFL".

*For discussion:* #119's criteria (a single prompt, no human help) set the bar at "fully
automated". Aaronson's bar is "did the theorem get proved". Which bar matters depends on whether
you are asking about AI capability or about mathematical progress.

## 5. Verification and trust

- **Could the model have gamed Lean?**
  ([Drescher, #35](https://scottaaronson.blog/?p=10169#comment-2041114)) Aaronson thinks it
  "extremely low probability". People he trusts, including Boaz Barak, have looked at the chains
  of thought, and the techniques "seem very commensurate with the problems being solved"
  ([#39](https://scottaaronson.blog/?p=10169#comment-2041118)).
  [Bakkot (#48)](https://scottaaronson.blog/?p=10169#comment-2041129) explains the remaining risk
  clearly: if the formal *statement* is right, a Lean proof is valid even when the prose proof
  doesn't match it. Only part of the release has Lean certificates.
- **Lean itself needs fixing.** Aaronson is "flabbergasted" that known Lean problems weren't
  "sorted out years ago" and says they "should urgently get fixed, like, yesterday"
  ([#269](https://scottaaronson.blog/?p=10169#comment-2041499)). Gödel is no excuse, because
  soundness without completeness is achievable.
- **"Navier–Stokes lost in translation"** (Bastounis et al.) doesn't persuade him that the
  blow-up proof is invalid, only that the Lean and informal proofs may differ
  ([#272](https://scottaaronson.blog/?p=10169#comment-2041503)).
- **Errors will happen.** After the Hodge retraction: "most of these will stand but this isn't the
  last one that will have some bug and need to be retracted … just like with human papers!"
  ([#132](https://scottaaronson.blog/?p=10169#comment-2041245)).

## 6. What mathematicians do next

- **Exposition becomes the main job.** What's needed now is "to simplify and re-explain the AI's
  results in more human-friendly terms". Exposition has always counted as "less than original
  discovery but more than mere verification"
  ([#294](https://scottaaronson.blog/?p=10169#comment-2041548)).
- **Maths becomes more like an experimental science**, with AI as "a telescope" (a commenter's
  phrase, which he endorses). To colleagues who say "we asked an LLM" isn't research, he answers:
  "what do you think papers are in every experimental science? … We'll just need to get off our
  high horse about it!" ([#18](https://scottaaronson.blog/?p=10169#comment-2041091)).
- **Training students.** He expects a mix of heavy work with AI tools to discover and explain
  maths, and "still learning lots of things the old-fashioned way — because otherwise, we'll no
  longer have any human minds capable of doing" the first part
  ([#73](https://scottaaronson.blog/?p=10169#comment-2041157)). The same reply blames NSF cuts as
  a more immediate threat to PhD places.
- **The AHM boycott call.** Aaronson finds "no one should spoil our fun by solving our open math
  problems using AI models" "totally untenable". He gives three reasons: it offers no
  public-interest argument, it breaks the principle that problems are open to anyone, and it can't
  be enforced once the capability diffuses. He mocks the line "Mathematicians did not ask for this
  work to be done" by imagining Hardy asking Ramanujan "who asked you to prove all these bizarre
  new identities?" He still wants the community to "hold the AI companies' feet to the fire"
  (9 Oct update; [#118](https://scottaaronson.blog/?p=10169#comment-2041227)).

## 7. Where the optimism stops

Aaronson is upbeat about the maths but not about AI generally. That matters when you place him
in the [accelerationist map](accelerationist-viewpoints.md):

- He calls himself "the opposite of a 'full steam ahead…' accelerationist AI-bro". He favours an
  international agreement to stop recursively self-improving superintelligence until alignment is
  better understood ([#50](https://scottaaronson.blog/?p=10169#comment-2041131)).
- On messier fields: the "giant mushroom cloud where 'mathematical research as we knew it' used to
  be" doesn't guarantee the same elsewhere, "but it certainly doesn't mean that those messy domains
  won't be covered … You should take the possibility extremely seriously!"
  ([#67](https://scottaaronson.blog/?p=10169#comment-2041150)).
- He claims labs are "already extremely close to full recursive self-improvement", with current
  models doing most of the work of training the next ones
  ([#290](https://scottaaronson.blog/?p=10169#comment-2041543)). This is his assertion, not a
  sourced fact.
- He closes the post with family movie night: *Terminator 2*.

**Tone of the thread.** Aaronson is openly scornful of sceptics: "cope", "conspiracy theories",
one commenter banned. He also explains why: the comment section had become "a grim obligation".
When presenting the critics (#24, #119), separate their arguments from his reactions to them.

## Relevance to the session

- **Opener (5 min):** the OpenAI vs Anthropic release models (§2), plus the telescope-time
  option. Nobody needs technical background to have a view.
- **"Significance" block:** the three comments make a ready debate. #24 says the problems were
  ripe, #115 offers a model of what the AI can do, and #119 reads the hit rate as a plateau. Show
  Aaronson's replies after the group has formed its own view.
- **Light-touch framing:** the Moshkovitz arc (§3) runs from "psychedelics" and "alien craziness"
  to "amazed by the new ideas … wants to give talks". It is a concrete, upbeat example of a
  researcher adapting within a day, which suits the session's tone.
- **RSE angle:** the Lean reliability points (§5) are a research-software problem: a tool
  "much of the mathematical world is increasingly coming to rely on" with known kernel issues.

## Caveats for the session

- **Counts.** The post says both 372 and 376, and its problem count was corrected from 8,000 to
  4,000. Quote the README instead (722 manuscripts at release, 719 now, in 372 families).
- **Second-hand claims.** The cryptography probing, the "3 hours per problem" figure and the
  recursive self-improvement claim come from Aaronson's sources or his own view. Hedge them if
  quoted.
- **The Moshkovitz quotes are informal texts** shared by her husband, not a published assessment.
- **References.** If this post is cited in the slides or README, add a BibTeX entry to
  `references.bib` (none exists yet).
