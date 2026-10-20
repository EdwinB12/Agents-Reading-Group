# Research note: Scott Aaronson on the Modern CTO podcast

**Source:** [Theoretical Computer Scientist: AI Just Changed Math Forever, with Scott Aaronson](https://www.youtube.com/watch?v=MZrXulP7sVc)
— interview by Joel Beasley, *Modern CTO* podcast (YouTube)

**Added:** 18 October 2026

> These are summary notes with timestamps, not a transcript. Figures and claims are as reported in
> the interview and have not yet been checked against primary sources — see
> [Caveats](#caveats-for-the-session) below.

## 1. The "Math Apocalypse" and AI breakthroughs

- **Hundreds of open problems solved at once.** OpenAI released solutions to ~400 major open
  mathematics problems that human research communities had worked on for decades; the unique games
  conjecture is mentioned as an example ([00:28](https://www.youtube.com/watch?v=MZrXulP7sVc&t=28s)).
- **Not Millennium Problems, but a serious tier.** These aren't the pinnacle problems (P vs NP, the
  Riemann Hypothesis), but they are a major tier where whole research communities were closing in
  ([06:15](https://www.youtube.com/watch?v=MZrXulP7sVc&t=375s)). Having ~400 solved at once
  fundamentally changes maths as a human subject
  ([00:54](https://www.youtube.com/watch?v=MZrXulP7sVc&t=54s)).
- **Software engineering went first.** Software engineers had their "AI apocalypse" a year or two
  earlier ([01:46](https://www.youtube.com/watch?v=MZrXulP7sVc&t=106s)). Mathematicians had told
  themselves maths was uniquely creative and safe from AI displacement; Aaronson says that belief is
  now untenable ([02:05](https://www.youtube.com/watch?v=MZrXulP7sVc&t=125s)).

## 2. The human role: verification and explanation

- **Terrible explanations.** The models explain their solutions poorly — "like a grad student who
  hasn't learned how to write yet" ([08:12](https://www.youtube.com/watch?v=MZrXulP7sVc&t=492s)).
- **Lean certificates.** Correctness is established by mechanically checkable formal versions (Lean
  certificates) ([08:32](https://www.youtube.com/watch?v=MZrXulP7sVc&t=512s)), but in most cases
  humans have not yet read or understood the proofs
  ([08:57](https://www.youtube.com/watch?v=MZrXulP7sVc&t=537s)).
- **The new job.** For mathematicians, theoretical computer scientists and physicists the immediate
  task shifts from solving to working *with* AIs — understanding, explaining, verifying and directing
  what they produce ([01:10](https://www.youtube.com/watch?v=MZrXulP7sVc&t=70s)).

## 3. Education and academic integrity

- **Homework is broken.** AI can complete traditional homework instantly
  ([18:46](https://www.youtube.com/watch?v=MZrXulP7sVc&t=1126s)), pushing assessment towards in-class
  exams, written tests and oral discussion
  ([27:52](https://www.youtube.com/watch?v=MZrXulP7sVc&t=1672s)).
- **The value of struggle.** A marathon runner doesn't train by driving round the track; students who
  lean entirely on AI won't build the skills needed to catch its hallucinations or deceptions
  ([28:51](https://www.youtube.com/watch?v=MZrXulP7sVc&t=1731s)).

## 4. AI safety, alignment and regulation

- **Alignment** is ensuring an AI reliably does what humans *mean*, rather than taking shortcuts or
  behaving in unintended ways ([39:44](https://www.youtube.com/watch?v=MZrXulP7sVc&t=2384s)).
  **Superalignment** is about safely managing something far more capable than us
  ([40:05](https://www.youtube.com/watch?v=MZrXulP7sVc&t=2405s)).
- **Regulation.** Heads of OpenAI, Anthropic and DeepMind are increasingly calling for government
  regulation and safety guardrails, with comparisons to aviation and nuclear energy
  ([45:28](https://www.youtube.com/watch?v=MZrXulP7sVc&t=2728s)).

## Relevance to the session

- Directly supports the session's recurring theme — *generating results is cheap; adjudicating them
  is not* — and the "proof vs understanding" discussion: Lean says a proof is correct, but nobody
  has necessarily understood it.
- The "software engineering went first" framing is a useful hook for an RSE audience.
- The education section could feed a discussion prompt on training PhD students when the solving
  can be delegated.

## Caveats for the session

- **Headline figure differs from our session plan.** The interview's "~400 problems" doesn't match
  the 6 October release figures in the session [README](../README.md) (722 manuscripts in 372
  result families, three withdrawn). It may be a rounded figure, or count something different —
  check against OpenAI's release before quoting.
- **Unique games conjecture.** Confirm whether it is actually among the released results, and in
  what form (full resolution vs partial result), before citing it on a slide.
- If this source is cited in the slides or README, add a BibTeX entry to `references.bib`.
