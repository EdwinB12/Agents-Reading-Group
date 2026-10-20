# Research note: opacity and "alien" AI proofs

- **Question:** many of the 2026 AI proofs are correct (or Lean-checked) but hard or impossible to
  read. What do authoritative voices say about this, and is it a permanent problem or a "six
  fingers" problem?
- **BibTeX:** keys are given next to each source below; all are in `references.bib`
- **Added:** 18 October 2026

> Supports the "Opacity" bullet on the *Why "Mathpocalypse"?* slide and the closing *"six fingers"*
> slide. All quotes below were checked against the source on 18 October 2026, unless marked
> otherwise.

## The argument in brief

1. **The opacity is real and widely reported.** Mathematicians who believe the Navier–Stokes proof
   is correct still say it teaches them almost nothing yet.
2. **It is not new.** The 1976 four-colour proof raised the same worry. Thurston argued that the
   real complaint was never about *truth*. It was about the lack of *understanding*.
3. **AI opacity is a different kind of opacity.** The four-colour program was opaque because it
   had too many steps, but each step was transparent. LLM reasoning is opaque in a deeper way.
   Philosophers argue a proof checker (Lean) is what makes the output trustworthy anyway.
4. **Opacity is already being worked down, often with AI help.** Human teams have rewritten AI
   proofs into readable papers within weeks, and some mathematicians use AI to explain AI proofs
   to themselves. This is the strongest evidence for the "six fingers" reading.

## 1. 2026 reactions: correct but unreadable

- **NPR, Geoff Brumfiel, "AI solved one of math's hardest problems. Humanity learned nothing (so
  far)"** (22 Sep 2026) — `npr2026learnednothing`. The best single source for quotes:
  - James Maynard (Oxford): "So far it's been very difficult to really extract any human
    understanding from this new AI proof."
  - Javier Gómez-Serrano (Brown, who uses AI in his own research): "The paper is not written for
    humans." He thinks it could help the field after "some serious re-writing", but "as of today,
    the paper doesn't teach us much."
  - Gómez-Serrano: "The paper doesn't explain what parts are important. What parts are routine?
    How does the idea feed into other places?"
  - Tristan Buckmaster (NYU): "It's a terribly written paper." He says his own rushed,
    AI-influenced preprint is "not very well written" either.
  - Crucially, few doubt correctness: the Lean code compiled, and "the community seems to have the
    consensus that it is correct" (Gómez-Serrano).
  - Maynard: "It wasn't about only answering this problem, it was about the human understanding
    behind it."
  - Tone check: NPR found mathematicians "embracing AI". The problem is "how the humans used it",
    not the AI.
- **Quanta, Jordana Cepelewicz, "Is AI the End of Math As We Know It?"** (5 Oct 2026) —
  `quanta2026endofmath`. The best long-form explainer:
  - "AI models skip to the end. At the moment, their proofs are nearly impossible to read."
  - The proofs "fail to demonstrate how the new work builds on or connects to other results".
    Mathematicians "know that the proofs are true … but have no idea why. What's missing is
    understanding, the currency that mathematicians trade in."
  - Teleportation metaphor: you are "perched on the peak but in the dark".
  - Daniel Litt (Toronto): "there's no amount of well-writtenness that lets you understand math."
  - Pavel Etingof (MIT): the papers "will only become a part of mathematical culture when some
    human reads them and understands them".
  - The article offers two futures: mathematicians who run AI tools without reading the output, or
    mathematicians who interpret, explain and build on AI results.
- **Scott Aaronson, "The Mathocalypse"**, *Shtetl-Optimized* (7 Oct 2026) — `aaronson2026mathocalypse`.
  - "no human has understood just about *any* of these proofs yet; the race to do so has just
    started."
  - Dana Moshkovitz (UT Austin) on the Unique Games proof: "some alien craziness". This is the
    source for the **"alien"** framing.
  - **But see §4:** Moshkovitz then spent a day asking an AI to explain the proof, and she "now
    *mostly* understands" it (Aaronson, in the comments).
- **Terence Tao, blog post on finite-time blowup with smooth forcing** (7 Sep 2026) —
  `tao2026blowup` (already in the bib). Tao says the related, heavily AI-assisted human preprints
  are being rewritten from what the authors "literally call 'the worst writeup we had ever seen in
  the history of mathematics' into something far more readable". He plans to digest the work "with
  some combination of a blackboard and modern AI tools". The post itself is a human-written,
  heuristic overview of the construction, an early piece of exposition.

## 2. History: this is the four-colour debate again

- **William Thurston, "On proof and progress in mathematics"**, *Bull. AMS* 30(2), 1994 —
  `thurston1994proof`. The classic text on proof versus understanding. Thurston says the
  controversy over the computer-assisted four-colour proof was not really doubt about the theorem
  or the proof's correctness. It was a continuing desire for *human understanding* of a proof, in
  addition to knowing that the theorem is true. He also notes that people who start using computers
  often find that what they want is understanding, not a collection of "answers". Free on
  [arXiv](https://arxiv.org/abs/math/9404236).
- **Thomas Tymoczko, "The Four-Color Problem and Its Philosophical Significance"**, *J. Phil.*
  76(2), 1979 — `tymoczko1979fourcolor`. The paper that started the "surveyability" debate. It
  argues that a proof no human can survey changes what "proof" means, because it brings
  experiment into mathematics.
- **Epilogue:** Gonthier's 2005 Coq formalisation reduced the trust needed for the four-colour
  theorem to a single proof assistant. Today Lean plays the same role. Nobody now treats the
  four-colour theorem as a crisis.

## 3. Philosophy: what kind of opacity is this?

- **Eamon Duede & Kevin Davey, "A Priori Knowledge in an Era of Computational Opacity: The Role of
  Artificial Intelligence in Mathematical Discovery"**, *Philosophy of Science* 92(5), 2025 —
  `duede2025apriori`. The most rigorous treatment found. The four-colour program automated forms of
  reasoning humans already use, so Appel and Haken gained a priori knowledge from it. The opacity of
  modern LLMs and neural networks blocks that route. **But** attaching a proof checker that mirrors
  human proof-checking restores it. In other words, Lean-style verification is what lets us know
  things from opaque machines. This maps directly onto the session's "cheap, trustworthy verifier"
  slide.
- **Runlong Yu & Xiaowei Jia, "Truth Without Comprehension: A BlueSky Agenda for Steering the
  Fourth Mathematical Crisis"** (arXiv:2509.17290, 2025) — `yu2025truth`. A preprint, not peer
  reviewed. It names a "Fourth Mathematical Crisis" with three parts: trusting proofs no human can
  inspect, understanding results no one can fully read, and verifying systems that resist
  verification. It proposes a "Human Understandability meta-axiom": every proof should come with a
  bounded, human-accessible projection that a verifier accepts. Useful as a provocation.
- **Amir Moradifam, "What Remains Human in Mathematics in the Age of AI"** (arXiv:2607.28791,
  accepted by the *EMS Magazine*) — `moradifam2026human`. As routine work is automated, conceptual
  insight, problem framing and genuine understanding become *more* valuable. It warns about the
  "illusion of explanatory depth" when fluent AI explanations stand in for understanding.

## 4. Optimism: opacity is being worked down

This section is the evidence for the "six fingers" slide. The unreadable first drafts are not
staying unreadable.

- **Alon, Bloom, Gowers, Litt, Sawin, Shankar, Tsimerman, Wang & Wood, "Remarks on the disproof of
  the unit distance conjecture"** (arXiv:2605.20695, 20 May 2026) — `alon2026unitdistance`. Nine
  leading mathematicians published a short, human-checked, simplified and somewhat generalised
  version of OpenAI's counterexample to Erdős's unit distance conjecture. It is dated 20 May,
  the same day as OpenAI's announcement. With hindsight, they connect it to work by Ellenberg–Venkatesh, Golod–Shafarevich and
  Hajir–Maire–Ramakrishna. Opaque output became readable and connected mathematics almost
  immediately.
- **The Alpöge–Buckmaster rewrite** (via `tao2026blowup`, `npr2026learnednothing`). The human
  team's heavily AI-assisted preprint is being rewritten into "professional quality" over weeks.
- **AI explaining AI** (via `aaronson2026mathocalypse`). Moshkovitz asked an AI to explain the
  "alien" Unique Games proof. Aaronson reports it did "an amazing job", and she was "amazed by the
  new ideas in it". This is anecdotal but vivid: the tool that made the mess can help clean it up.
- **Tao's "open exposition problems"** (`tao2026math20slides`, see [tao-math-2-0.md](tao-math-2-0.md)).
  He proposes treating the explanation of opaque proofs as a research problem in its own right.
- **Human-style automated proof** (`ganesalingam2017humanstyle`). Ganesalingam & Gowers built a
  prover designed to write proofs the way humans do. Gowers later ran a blind test on his blog,
  mixing its proofs with human-written ones. Readability is an engineering target, not a law of
  nature.

## Using this in the session

- **"Six fingers" framing.** Today's AI proofs are like early AI images. They are obviously
  machine-made, they skip the parts humans need, and they say nothing about which steps matter. The
  unit-distance and Alpöge–Buckmaster rewrites show the fix already happening, partly *with* AI.
- **Fair critical view.** Etingof and Litt make a stronger claim that does not fade with better
  writing: understanding has to happen in a human head ("no amount of well-writtenness"). The
  question is whether AI can speed that up (Moshkovitz) or only replace it (Quanta's first
  future).

### Discussion prompts

1. Thurston said the four-colour complaint was about understanding, not truth. Fifty years later,
   nobody worries about it. Will the Navier–Stokes proof feel the same in 2040?
2. Duede & Davey say a proof checker lets us *know* things from opaque machines. Is knowing enough,
   or is understanding the product (cf. Tao's cancer-cocktail thought experiment)?
3. If an AI explains an AI proof to you and you come away convinced, do you *understand* it, or do
   you have the "illusion of explanatory depth" (Moradifam)?
4. In your field, who does the "rewrite for humans" work, and does it get credit?

## Searched for but not used

- **"Alien" framings in aggregator outlets** (36kr, HTX, MindStudio). They claim experts "cannot
  understand it at all" and that a Millennium Problem was solved outright. These are unreliable and
  overstate the case, so they were excluded.
- **"Why are we even doing all this?"** (Tao's blog, 15 Oct 2026). This is a *satirical guest post
  by Rikab Gambhir*, not Tao's own view. It is a fun read on output-over-understanding, but don't
  attribute it to Tao.
- **"Mathematical anxiety in the age of AI: Opacity, role inversion…"** (ScienceDirect). It
  appeared in search results with the terms "hermeneutical" and "structural opacity", but the page
  returned 403 and no independent record of the title was found, so it is unverified.
- **Futurism coverage** (23 Sep 2026). Its quotes are lifted from NPR, so cite NPR directly.
- **Max Weinreich, "The crisis of AI-generated mathematics"** (arXiv:2608.02859). This is an
  essay making "the case for total opposition" to AI in mathematics. Its abstract doesn't address
  opacity, and it is a useful contrast only if a strongly anti-AI voice is wanted.
- **Daniel Litt's blog/a16z interview.** Secondary summaries only. His original wording couldn't be
  checked, so only the Quanta quote is used.
