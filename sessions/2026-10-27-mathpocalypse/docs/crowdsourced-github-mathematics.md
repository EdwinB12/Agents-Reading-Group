# Research note: crowdsourced, open-source, GitHub-based mathematics

**Added:** 18 October 2026

**Prompted by:** a video in which Dr. Samuel Allen Alexander reviews Terence Tao's
[Math 2.0 slides](https://teorth.github.io/tao-web/slides/math-2-0-caltech-2026.pdf)
(see the [Math 2.0 note](tao-math-2-0.md)). Four of Tao's examples are open, crowdsourced projects
run from public repositories. This note covers those four and the tradition behind them.

**BibTeX:** `tao2025etp`, `tao2025etpblog`, `teorth_equationaltheories`, `tao2026igp`,
`tao2026ieantn`, `teorth_ieantn`, `teorth_erdosproblems`, `tao2026optconstants`,
`teorth_optimizationproblems`, `teorth_pfr`, `gowers2009polymath`, `polymath2014retrospective`,
`mathlib`

> **Corrections to the video summary we were given.** We checked it against the slide text.
>
> - It is the **Inverse *Galois* Problem** challenge (IGP24), not "Inverse Gowers", and the
>   groups are *Galois* groups. The slide reads: "The first stage of IGP24 was a successful
>   crowdsourced competition to locate degree 24 polynomials with each of the 25,000 possible Galois
>   groups at this degree. The second stage will be a collaborative effort to extend up to degree
>   31." So the degree-31 claim is Tao's own. We found no other source for it yet.
> - "Math lab platforms" is a mishearing of **Mathlib**. The slide says: "Creation of large,
>   high-quality libraries of formal mathematics, such as Mathlib."
> - The slide calls IEANTN a living "spreadsheet", not a "network spreadsheet". Its full name is
>   the *Integrated Explicit Analytic Number Theory Network*, abbreviated **IEANTN** (not "ANN").

## 1. The idea in one paragraph

Traditional maths research is done by one to three authors, who publish a static PDF that a few
referees check. The newer model runs a research programme like an open-source software project:

- a **public Git repository** holds the source of truth;
- **issues and pull requests** split the work into tasks anyone can claim;
- **continuous integration (CI)** runs a proof checker (usually Lean) as the referee;
- a **chat server** (usually Zulip) handles discussion;
- a **"blueprint"** (human-readable LaTeX linked to the formal code) shows what is done.

Anyone can join, including amateurs, students and, increasingly, AI tools. They can join because
the verifier checks the work, so organisers don't have to trust the contributors. In Tao's terms this turns
experimental maths from "case studies" into "population surveys"
([slides](https://teorth.github.io/tao-web/slides/math-2-0-caltech-2026.pdf)).

## 2. Prehistory: Polymath (2009 onwards)

- **Blog comments, not Git.** Tim Gowers asked in January 2009 whether "massively collaborative
  mathematics" was possible ([Gowers 2009](https://gowers.wordpress.com/2009/01/27/is-massively-collaborative-mathematics-possible/)).
  Polymath1 found a new combinatorial proof of the density Hales–Jewett theorem in about six
  weeks. Writing it up took months longer
  ([Wikipedia](https://en.wikipedia.org/wiki/Polymath_Project)).
- **Polymath8 (2013–14)** followed Yitang Zhang's bounded-gaps breakthrough. It cut the bound
  on gaps between primes that occur infinitely often from 70 million to 246
  ([retrospective, arXiv:1409.8361](https://arxiv.org/abs/1409.8361)).
- **Mixed record.** Several later Polymaths stalled. The Erdős discrepancy problem was finally
  solved by Tao alone, building on Polymath5's ideas.
- **What changed since.** Polymath needed experts to read and trust each other's comments. Lean
  and CI take most of that trust burden away, so participation can now scale to people the
  organisers have never met.

## 3. The formalisation turn: PFR and Mathlib (2023 onwards)

- **PFR (Nov–Dec 2023).** Gowers, Green, Manners and Tao proved the Polynomial Freiman–Ruzsa
  conjecture. Tao then launched a public Lean project that formalised the proof in about three
  weeks. It used Patrick Massot's blueprint tool, with tasks claimed on Zulip
  ([`teorth/pfr`](https://github.com/teorth/pfr)). This was the template for later projects.
- **Mathlib** is the community Lean library that the projects build on. Secondary sources put it
  at over 2 million lines and several hundred contributors in 2026, but they disagree. Check the
  [official stats page](https://leanprover-community.github.io/mathlib_stats.html) before
  quoting a figure.
- **Buzzard's FLT project (2024–2029)** is a funded, blueprint-driven community effort. Claude's
  autonomous 13M-line formalisation of FLT in September 2026 overtook it. For comments that this
  output is "not in library style", see the [Math 2.0 note](tao-math-2-0.md) and the brief, §5.
  The contrast is a good discussion point: one crowd building a maintainable library, against one
  machine producing a working but unidiomatic artefact.

## 4. Tao's four Math 2.0 examples

### 4.1 Equational Theories Project (ETP), Sept 2024 – 2025

- **Question.** Take 4,694 simple equational laws for magmas (a set with one binary operation).
  For every ordered pair of laws, does the first imply the second? That is
  **22,028,942 implications** in all.
- **Outcome.** Every implication was settled by **14 April 2025**, with proofs or
  counterexamples formalised in Lean. Informal resolution took about 2 months and Lean
  formalisation about 5 more ([Tao blog, Dec 2025](https://terrytao.wordpress.com/2025/12/09/the-equational-theories-project-advancing-collaborative-mathematical-research-at-scale/);
  [arXiv:2512.07087](https://arxiv.org/abs/2512.07087), 34 authors, contributions recorded with
  the CRediT taxonomy).
- **How it worked.** The work ran on GitHub, Zulip and a blueprint, with an "Equation Explorer"
  GUI for browsing. It came in waves:
  1. brute-force search over small finite magmas;
  2. automated theorem provers (Vampire, Prover9/Mace4);
  3. the literature;
  4. custom constructions for a hard core of about a thousand implications. One equation (E1729)
     took months.
- **The surprise for an AI reading group.** Tao writes that "modern AI tools did not play a major
  role in this project." The workhorse was "good old-fashioned AI", meaning classical provers,
  which were far cheaper. The crowd plus classical automation did the job. LLMs were not needed.
- **Still open:** for finite magmas, whether E677 implies E255.

### 4.2 SAIR/LMFDB Inverse Galois Problem challenge (IGP24), 2026

- **Question.** There are 25,000 transitive permutation groups of degree 24 (24T1 to 24T25000).
  For each one, and for each possible number of real roots, find an integer polynomial whose
  Galois group is that group. That gives 165,836 (group, real-roots) pairs. Before the challenge
  the LMFDB covered only 286 groups and 622 pairs
  ([announcement](https://terrytao.wordpress.com/2026/06/16/third-sair-competition-inverse-galois-challenge/)).
- **Format.** It was a *competition*, unlike ETP. Leaderboards scored submissions by smallest
  discriminant, with bonus credit for finding pairs other teams missed. "Unrestricted use of
  computational tools, including AI" was allowed. MAGMA provided a verification API, and the
  organisers encouraged teams to share techniques on Zulip. Stage 1 closed on 15 August 2026.
- **Outcome.** A secondary source reports that 98.4% of signatures were found, with 39
  non-solvable cases missing (likely around PSL₂(𝔽₂₃), PGL₂(𝔽₂₃) and M₂₄). The leading team was
  Klüners and Malle, two established human experts
  ([Persiflage, Aug 2026](https://galoisrepresentations.org/2026/08/16/the-inverse-galois-challenge-part-ii/)).
  We have not checked these figures against the official
  [leaderboard](https://competition.sair.foundation/competitions/igp24/leaderboard).
- **A sceptical data point.** The same blogger says their own Codex-driven attempt stalled at
  about 40,000 pairs and taught them nothing new mathematically. Their conclusion: hands-on
  polynomial and Galois-theoretic skill still mattered.
- **Next.** According to Tao's slides, stage 2 will be collaborative rather than competitive and
  will extend to degree 31.

### 4.3 Integrated Explicit Analytic Number Theory Network (IEANTN), 2026

- **Idea.** Explicit analytic number theory is full of numerical bounds that depend on each
  other (for example, bounds on π(x) depend on bounds on ψ(x)). Those dependencies are recorded
  only in prose across many papers. IEANTN turns them into a **graph of claims**. Each node records
  its assumptions and its evidence, which can be a Lean proof, a numerical computation or a
  citation. Then "for any result you can read off exactly what it rests on and how good that
  evidence is" ([`teorth/IEANTN`](https://github.com/teorth/IEANTN);
  [launch post, Jan 2026](https://terrytao.wordpress.com/2026/01/15/the-integrated-explicit-analytic-number-theory-network/)).
- **Why "living spreadsheet".** If someone improves an upstream bound, every downstream bound can
  be recomputed, much like changing a cell in a spreadsheet. A static paper can't do this. The plan
  is to absorb Ramaré's TME-EMT collection of explicit estimates over time. Tao is also working
  with Math, Inc. on it as their inaugural Veritas Fellow.
- **Workflow (an RSE's dream).**
  - Contributors comment `claim` or `disclaim` on an issue, or `propose PR #n` to link a pull
    request.
  - CI checks proofs with Lean's Comparator and writes a JSON "receipt" for each verified
    conclusion.
  - The repo has a `CLAUDE.md` and an `AGENTS.md` for coding agents, as this session folder
    does.
- **Status.** Early. The repo had around 580 commits and a few proof-of-concept nodes when we
  looked. Tao reports that AI help has sped up the tedious numerical-verification lemmas, which
  used to wait weeks for a volunteer to claim them.

### 4.4 Formal libraries and living databases

- Tao's slide only names Mathlib (§3). Two neighbouring GitHub databases fit the same pattern:
  - **Erdős problems database** ([`teorth/erdosproblems`](https://github.com/teorth/erdosproblems),
    Aug 2025). It is a community YAML mirror of Thomas Bloom's
    [erdosproblems.com](https://www.erdosproblems.com/), first set up to link problems to OEIS
    sequences. It now tracks status, whether the statement is formalised (via DeepMind's
    `formal-conjectures`), and an "AI attempts" link. Its wiki page on AI contributions was frozen
    on 30 June 2026 and is kept only as a historical record. The README gives no reason. It has become the main public scoreboard
    for AI claims about Erdős problems, including the 23 in OpenAI's 6 October release.
  - **Optimization constants** ([`teorth/optimizationproblems`](https://github.com/teorth/optimizationproblems),
    Jan 2026, maintained by Damek Davis, Paata Ivanisvili and Tao). It records the best known
    upper and lower bounds on constants such as the Erdős minimum-overlap constant, and invites
    "professionals, amateurs, and companies" to beat them. AI-generated contributions must say so.
    Some entries are marked unverified
    ([proposal post](https://terrytao.wordpress.com/2026/01/22/a-crowdsourced-repository-for-optimization-constants/)).

## 5. What makes it work (and what doesn't)

| Ingredient | Why it matters | Caveat |
| --- | --- | --- |
| Machine verification (Lean, MAGMA) | Strangers and AI can contribute without being trusted | Checks the *statement as formalised*: a mis-stated theorem is verified nonsense |
| Atomised tasks (issues, blueprints) | Low barrier: a student can do one lemma | Someone still has to do the decomposition, which is skilled work |
| Public repo + open licence (Apache-2.0) | Reproducible, forkable, citable | Static numbers and YAML schemas need ongoing curation |
| Problem *populations* rather than one big problem | Suits automation; produces data sets | Tao warns that blind problem-solving can "sterilize" a field |
| Leaderboards (IGP24) | Pulls in labs and amateurs | Rewards breadth and speed, not insight |

**Credit** remains the unsolved social problem. ETP lists 34 authors and uses CRediT. How do you
cite a lemma that an anonymous contributor's agent proved in a PR? Hiring committees still count
first-author papers.

## 6. Relevance to the session

- **The optimistic story.** This is the hopeful side of the Mathpocalypse. Mathematicians are not
  being replaced. They are acting as **maintainers**: they set problems, design schemas, review PRs
  and decide what counts as interesting. Tao's ETP finding that classical tools did most of the
  work is a useful corrective to "LLMs did everything".
- **The RSE hook.** Every ingredient here is research software engineering: Git workflows, CI,
  data schemas, contribution guides and agent instruction files. Maths is adopting our tools, and
  it could use our people.
- **The tension.** OpenAI's "drop 400 results in a repo" release
  ([`openai/math`](https://github.com/openai/math)) and ETP both use GitHub. One is a *broadcast*
  and the other is a *community*. Which model wins?

## Discussion prompts

1. Would your field benefit from an IEANTN-style "living network" of dependent results, such as
   benchmark numbers, model parameters or software versions? What would the "Lean" (the verifier)
   be?
2. ETP needed only classical automation, IGP24 allowed AI, and IEANTN ships `CLAUDE.md`. Is
   human-plus-agent crowdsourcing different in kind from human crowdsourcing, or only faster?
3. How should credit work for a PR whose proof came from someone's AI agent? Is CRediT enough?
4. Competition (IGP24 stage 1) or collaboration (stage 2): which gets better maths, and which gets
   better mathematicians?
