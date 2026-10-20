# Research note: temporary fluke or permanent sea-change?

- **Question:** are the 2026 AI maths results a one-off burst (a fluke, a PR spike, a plateau about
  to arrive), or a lasting change in how mathematics is done?
- **Main source:** Terence Tao, [*Mathematics in the age of AI*](https://arxiv.org/abs/2608.16753),
  arXiv 2608.16753 (v1, 17 August 2026). This is a 12-page essay submitted to the *Proceedings of
  the ICM 2026*, written up from his ICM public lecture in Philadelphia on 24 July 2026
  ([video](https://www.youtube.com/watch?v=sxAe4HJceFQ);
  [slides](https://teorth.github.io/tao-web/slides/age-of-ai-icm-2026.pdf)).
- **Also drawing on:** Quanta, Understanding AI and Scientific American (see
  [§3](#3-other-pieces-worth-reading)); Tao's [AI views page](https://teorth.github.io/tao-web/ai-views.html);
  and earlier notes in this folder.
- **BibTeX:** `tao2026ageofai`, `williams2026grappling`, `howlett2026sciam`
  (`quanta2026endofmath` was already in the file)
- **Added:** 18 October 2026

> The [research brief](claude-mathpocalypse-research-brief.md) (§3, "Foundational reading") calls
> Tao's essay the best framing piece for "is this permanent?". The essay summary comes from the
> arXiv HTML version, and its quotes have not been checked against the PDF. The Quanta, Understanding
> AI and Scientific American summaries come from the full article text. The Mastodon posts in §2
> were summarised from Tao's AI views page and have not been opened individually. The companion
> lecture note is [Math 2.0](tao-math-2-0.md).

## The short answer

Tao doesn't try to settle whether the change is real. **He assumes the capabilities arrive and
asks what maths is for when they do.** That turns "fluke or sea-change?" into a more useful
question. If it is a sea-change, which of our practices rest on proofs being scarce, and which of
them will break?

Most of the other pieces agree on one asymmetry. **Even if AI progress stopped today, much of the
change would stay.** Solved problems stay solved, the tools are spreading, and institutions have
already started to adapt. Whether progress continues decides *how big* the change is, not
*whether* there is one. The open question is which new equilibrium the field settles into. Tao
frames this as the field's second foundational crisis and expects it to come out
"much healthier and much more resilient" (quoted in Scientific American). That fits the session's
optimistic tone.

## 1. Tao, "Mathematics in the age of AI": section by section

1. **Historical prologue: a second foundational crisis.** Russell's paradox and Gödel caused a
   turbulent period (roughly 1900–1930) that ended with a rigorous, mechanisable foundation. Tao
   says we are entering a similar period, but this time "what is being stress-tested is not our
   foundational framework for mathematical truth". What is under stress is **values and practice**.
   Scientific American's reporter notes that Hilbert gave his famous problems address at the 1900
   ICM, in the middle of the first crisis. Tao seemed aware of the echo.
2. **The motivating question.** How should the community respond? Tao says this is a
   metamathematical, political, ethical and cultural question, not a mathematical one. He borrows
   mathematical language (conjectures, hypotheses) to give it structure.
3. **The AI Capability Conjecture.** This is a template with free parameters ("some tools", "some
   fields", "some success rate"). If even weak versions are false, it is business as usual. If
   strong versions are true, current practice cannot continue. The public evidence is poor: there
   is reporting bias ("successes are announced and failures are not"), and compute and scaffolding
   are not disclosed. The controlled data point is [First Proof](https://1stproof.org/). In its
   second batch, 7 of 10 research-level problems got at least one passing AI answer, at roughly
   tens to hundreds of dollars per problem.
4. **The Working Hypothesis.** Assume, without necessarily believing it, that a reasonably strong
   capability conjecture holds. **This is the step that sidesteps the fluke-vs-permanent debate.**
5. **Goals and values.** Mathematicians pursue many goals at once: solving problems, building
   theory, understanding the world, building community, training students, adding to shared
   knowledge, and making beautiful things. Historically these goals were **positively correlated**,
   so problem-solving could stand in for all of them. Optimise that proxy with AI and **Goodhart's
   law** kicks in: the goals come apart. AI is especially exposed to this, because it is
   "ungrounded" and its industry rewards benchmark wins.
6. **Case study: problem solving.** Tao refines the goal five times. Solving problems alone gives
   wrong "solutions", so add *verify* them. Verified proofs can be opaque, so add *communicate*
   them. Then the community has to *digest* them, and finally they have to be *canonicalised* into
   the standard theory. The result is a pipeline: generation → verification → exposition →
   publication → digestion → canonicalisation. Tao argues that the "natural friction" in human
   writing helps the reader, because "the 'mistakes' in human exposition can be genuinely helpful
   to the reader". His example is struggling through Bourgain's dense 1991 paper.
7. **From proof scarcity to proof abundance.** Without policy changes there will be **"proof
   indigestion"** at every stage. Unverified proofs pile up, then unwritten ones, then unrefereed
   ones, then undigested ones. Journals, priority rules, hiring and prizes were all built for
   scarcity. These strains existed before AI, but AI will "exacerbate these existing stresses
   markedly".
8. **Recommendations.** Tao endorses the [Leiden Declaration](leiden-declaration-summary.md):
   disclose tool use, support reviewing, affirm human authorship, and take care over attribution.
   He wants the field to value digestion more than being first. **The talk test:** if the authors
   cannot give a clear, correct, properly attributed expert-level talk on a result, it should not
   be published. A proof that no human can explain is "incomplete, even if it has been formally
   verified".
9. **Closing thoughts.** Teaching, hiring, grants and refereeing need the same analysis. In
   education Tao wants tight limits on AI, because "the goal of training a mathematician is not
   achieved by producing correct homework". He wants the community to set best practice on its
   own terms, not the vendors'. Appendix A lists new infrastructure: Mathlib, the Erdős problems
   database, the optimisation constants database, First Proof, SAIR and others.

**What the essay says about permanence.** It never says outright whether the change is temporary
or permanent. It treats the strains as getting worse and the transition as a lasting condition to
be managed, not waited out. It also treats the bad outcomes as avoidable with "suitable policy and
cultural changes".

## 2. The evidence, sorted

### Signs it is durable

- **Irreversibility.** Tao calls open problems a ["non-renewable resource"](https://mathstodon.xyz/@tao/117204929023813310)
  (2 September 2026). A solved problem cannot be unsolved, and its solution shapes every later
  attempt.
- **Even a halt keeps much of the change.** Understanding AI concludes that "if AI progress in
  mathematics stopped now, the fundamental structure of the field would stay the same". But that
  is only because mathematicians would lean into what AI is bad at and automate the routine work,
  which is itself a lasting change in day-to-day practice. The same piece adds that a stall
  "seems unlikely".
- **Diffusion and cost.** Aaronson expects these capabilities to reach anyone with a commercial
  subscription within months ([note](aaronson-mathocalypse.md)). The cost per problem is falling
  (brief §3).
- **Institutions are already changing.** arXiv limits authors to two submissions a month.
  Journals are experimenting with requiring a talk alongside a paper, which is close to Tao's
  talk test. The Leiden Declaration has IMU backing. The Association for Human Mathematics has
  formed (Quanta).
- **Behaviour is already changing.** Mathematicians are leaving open conjectures out of papers,
  posting early to avoid being scooped, and asking MathOverflow fewer questions (Quanta).
- **Structural asymmetry.** Generation is speeding up faster than digestion
  ([Tao, April 2026](https://mathstodon.xyz/@tao/116450581967483825)). In a Simpson's-paradox
  framing, each person's output rises while the field's signal-to-noise ratio falls
  ([August 2026](https://mathstodon.xyz/@tao/117169038028698262)). Neither effect reverses if
  model progress stalls.
- **The goalposts keep moving one way.** Tsimerman, a Fields Medallist who joined OpenAI's safety
  team, says sceptics claimed AI would never do maths, then never research maths. He expects the
  same with theory-building (Understanding AI).

### Signs of a fluke, or reasons for caution

- **Hit rates and denominators.** About 9% of roughly 4,000 problems were solved, and one
  sceptic reads that as a plateau (brief §3). Tao's January 2026 audit of the Erdős problems found
  success rates of a point or two, mostly at the easy end
  ([post](https://mathstodon.xyz/@tao/115911902186528812)). He later called that figure "a
  snapshot of a fast-moving capability, not a standing estimate".
- **Reporting bias.** Lab announcements are not controlled experiments. First Proof is the rare
  exception ([jagged frontier note](jagged-frontier-gowers.md)).
- **Verification isn't finished.** Clay has not accepted Navier–Stokes, a Hodge claim was
  retracted for a sign error, and most of the proofs have not yet been read by humans.
- **A ceiling is possible.** Greg Burnham (Epoch AI) says both a ceiling on genuinely new ideas
  and continued scaling into new mathematics are "consistent with the evidence we have so far"
  (Understanding AI).
- **History of absorbing automation.** Yu Deng (Fields 2026) and Jordan Ellenberg describe the
  usual pattern: whatever a computer can do gets reclassified as "computation", and
  mathematicians move on to new problems. On this view the change is real but familiar, a
  redefinition of "technical details" rather than a break.
- **Nobody can forecast this.** Tao says he is "not sure anyone is capable of any reliable
  forecasting beyond a year at best" (quoted on his
  [AI views page](https://teorth.github.io/tao-web/ai-views.html)).

### Possible equilibria

| Future | Who | What it looks like |
| --- | --- | --- |
| Bad equilibrium | Daniel Litt (Quanta) | People trained to press a button and not read the output. If nothing changes, "no more math in 50 years", with neither humans nor machines doing it. Litt adds: "I'm not saying it's likely." |
| Interpreter | Pavel Etingof (Quanta) | Less "pecking on the permafrost". Mathematicians read, rewrite and connect AI output: "There will be a lot more mathematics to make sense of." |
| Business as usual, redefined | Yu Deng, Ellenberg (Understanding AI) | Humans make theories and frameworks while AI handles more of the details: "the joy we get from studying math will not change." |
| Collapse, then rebuild | Javier Gómez-Serrano, Tsimerman (Scientific American) | Fewer jobs, and different ones. "The whole system is going to collapse… Better to do something now." Tsimerman also looks forward to "an infinite library" of results to explore. |
| Math 2.0 | Tao ([note](tao-math-2-0.md)) | AI at every link of the cycle, with human understanding at the hub. The community, not the labs, sets the goals. |

### Synthesis for the session

Even the sceptical reading leaves a sea-change. By old standards, a 9% hit rate over thousands of
problems at falling cost is already an abundance of proofs, and those problems can't be unsolved.
So the useful argument is not "fluke or permanent" but **which equilibrium the field lands in, and
who chooses it**. Tao's answer is that the community chooses. Litt's two sentences make a good pair
for the group: "The existing equilibrium has broken. We'll have to find a new one" and "I think
there is a good future where we come out way ahead of where we are now."

## 3. Other pieces worth reading

- **Jordana Cepelewicz, [Is AI the End of Math As We Know It?](https://www.quantamagazine.org/is-ai-the-end-of-math-as-we-know-it-20261005/)**,
  *Quanta*, 5 October 2026 (`quanta2026endofmath`). Starts at Ken Ono's tense two-hour Berkeley
  colloquium. Its main image: AI "teleports" you to a mountain peak in the fog, so you have the
  answer without the journey. The core diagnosis is that the incentives were built for a world
  where solving was hard. "It breaks our system" (Tasmin Chu, Caltech). It is the best source for
  the behavioural evidence and for the bad, interpreter and good futures. It also covers the
  emotional side: Marcel Goh's AI "vegetarians" and fears of a "lost generation". Its own view is
  hopeful: "the stakes are high enough that I think they'll succeed."
- **Kai Williams, [Mathematicians are grappling with the possibility that AI might eclipse them](https://www.understandingai.org/p/mathematicians-are-grappling-with)**,
  *Understanding AI*, 4 August 2026 (`williams2026grappling`). Based on interviews with more than
  20 mathematicians at the ICM. It is the clearest piece on the fluke question as such. It finds
  many mathematicians optimistic about their own near-term work, mostly using AI as a smart
  literature search. It concludes that a halt would leave the field's structure intact, but that a
  halt is unlikely. Good quotes from Deng, Tsimerman, Burnham and Avigad.
- **Joseph Howlett, [AI has finally come for math—mathematicians might never recover](https://www.scientificamerican.com/article/mathematicians-confront-the-ai-apocalypse/)**,
  *Scientific American* (`howlett2026sciam`). A report from the ICM. It covers Tao's lecture and
  the Hilbert parallel, Tsimerman's move to OpenAI and the backlash against it, and
  Gómez-Serrano's "five stages of AI grief" slide. Andrew Sutherland's line about mathematicians
  being "the canary in the coal mine for a lot of other professions" links to session question 4.
- **Tao, [AI views page](https://teorth.github.io/tao-web/ai-views.html)**. An index of Tao's
  essays, talks and posts on AI from 2023 onwards, including the Klowden–Tao essay
  ([arXiv 2603.26524](https://arxiv.org/abs/2603.26524)), the *New Scientist* interview (6 August
  2026, "temporarily lost the narrative"), and the Numberphile video *No More Heroes* (15 October
  2026, the end of maths' "romantic era"). Useful for tracking how his views have moved. In 2023 he
  predicted "2026-level" AI as a trustworthy co-author. By September 2026 he said he saw no
  constructive way to engage with OpenAI.
- **Classic background:** Thurston, "On proof and progress in mathematics" (1994,
  `thurston1994proof`). It is the source of the "understanding, not proofs" argument that Tao,
  Quanta and Understanding AI all build on.

Not yet read: the Klowden–Tao essay, the *New Scientist* interview (the site blocks automated
fetching), Bessis's "theorem economy" essay (cited by Tao in §8), and Marcolli's *LMS Newsletter*
essay (quoted in Quanta).

## Discussion prompts

1. Does Tao's "assume the capabilities arrive" step dodge the real question? Or is it the right way
   to handle a question nobody can forecast?
2. Suppose AI progress froze tomorrow. Which of the changes in §2 would undo themselves, and which
   would stay?
3. Which stage of Tao's pipeline is *our* bottleneck as RSEs: verification, exposition, review or
   digestion? Would AI ease it or make it worse?
4. Would you adopt the talk test as a referee or reviewer? Does it unfairly exclude results that
   are formally verified but hard to follow?
5. Which future in the equilibria table is most likely, and which is most attractive? Is the 1900
   foundational crisis a better analogy than the four-colour theorem or the calculator (brief §3)?
