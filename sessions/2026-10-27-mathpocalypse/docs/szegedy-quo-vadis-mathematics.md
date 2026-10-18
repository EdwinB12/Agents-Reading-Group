# Research note: Szegedy, "Quo Vadis, Mathematics?"

**Source:** Christian Szegedy, ["Quo Vadis, Mathematics?"](https://docs.google.com/document/d/e/2PACX-1vTSh-pyNP3Gi99WMmsinnLmE9V5CDI0HEm6WGbIPMNt3V5SGlClHF8-BetotKHOImrvQDSXmFdiOw8D/pub)
(public Google Doc, dated 3 October 2026)

**Secondary source:** Alexis Dufresne, ["Christian Szegedy says AI closes math's lone-climber age"](https://aiweekly.co/alerts/christian-szegedy-says-ai-closes-maths-lone-climber-age)
(AI News Weekly, 7 October 2026)

**Added:** 18 October 2026

**BibTeX:** `szegedy2026quovadis`, `dufresne2026szegedy`, `szegedy2020autoformalization`

> **What was and wasn't checked.**
>
> - We fetched the essay itself, but the tool returned a summary of it, not the verbatim text. The
>   section structure and the "Do not bet against the airplane" line come from that summary.
>   The other direct quotes below come from the AI News Weekly article, which quotes the essay.
>   Check them against the Google Doc before putting any on a slide.
> - Szegedy's essay is a personal opinion piece, not a study. The predictions are his own.
> - Christian Szegedy is not Balázs Szegedy (his brother, a mathematician) or Mario Szegedy
>   (a computer scientist). Web searches mix these three up.
> - Editorial comments in the AI News Weekly piece (on prestige and problem selection) are the
>   publication's, not Szegedy's.

## 1. Who is Szegedy, and why does this carry weight?

- A former Google research scientist, best known for the Inception image-recognition architecture.
  His PhD is in applied and discrete mathematics.
- He has argued for automating mathematics for years. Since founding the N2Formal team at Google in
  2016 he has called **autoformalisation** (AI that reads natural-language maths and turns it into
  machine-checkable form) "the unifying theme" of his research. A 2026 Bonn seminar listing
  gives his affiliation as AletheAI.
  His 2020 paper
  ["A Promising Path Towards Autoformalization and General Artificial Intelligence"](https://research.google/pubs/a-promising-path-towards-autoformalization-and-general-artificial-intelligence/)
  makes the case.
- So the essay is the latest step in a long-held view, not a new conversion. It is also written by
  someone who builds these systems, which is worth saying out loud in discussion.

## 2. The essay in brief

The essay has four parts, each built on a metaphor.

| Section | What it says |
| --- | --- |
| **Graduation** | Szegedy's own story. He trained in a maths-specialised class in Hungary and in IMO-style competitions, never made the national team, and felt an "emptiness" when the competition years ended. This sets up his claim that the upheaval is emotional as well as technical. |
| **The Jungle** | Pure maths is an "endless, unmapped wilderness". Explorers map terrain, find resources to fund expeditions, and build tools. The most respect goes to climbing a hard "rock" (a famous open problem; the Langlands programme is his example). Useful tools (the matrix pseudo-inverse, NP-completeness of 3-SAT) win recognition but less prestige. Applications such as elliptic curves in cryptography matter mainly for funding. |
| **The Airplane** | AI today is like the Wright brothers' twelve-second flight: low, short, costly, but it has begun to solve conjectures nobody had solved. AI companies "planted flags" on rocks that explorers were already approaching. The explorers objected: *"Please don't put flags on our rocks. It stops other explorers from trying to climb them."* Szegedy calls criticism of current limits a "static-thinking fallacy". He expects cheap private planes, then mapping satellites, then commercial extraction that will be "messy and dirty". |
| **Quo Vadis?** | "Do not bet against the airplane." Academia will change slowly. Rewards will shift towards choosing worthwhile terrain, directing AI systems, and explaining results. Maths is "about to graduate" into a full-scale industry and infrastructure for the other sciences. |

## 3. The thesis we want to explore: from lone heroes to infrastructure

Szegedy's claim, in his words: *"The age of lone climbers is closing, and the age of mapping the whole
continent is opening."* Maths "will grow into a full-scale industry".

### What "industry" implies

His metaphor stages the change like the development of aviation:

1. **Pioneer flights.** Costly, brief, mostly proofs of concept (where he puts AI maths now).
2. **Cheap private planes.** Individual mathematicians fly their own AI tools.
3. **Satellites.** Systematic mapping of the whole terrain, not selected peaks.
4. **Commercial extraction.** Maths output at industrial scale, with the mess that brings.

The shift is from **craft** (a hero picks a peak and spends years on it) to **infrastructure**
(a shared platform produces, checks and indexes results continuously).

### What is likely to matter more and less

| Gains value | Loses value |
| --- | --- |
| Choosing which terrain is worth exploring ("taste") | Climbing rocks "just to hone climbing tools" (training by solving hard problems) |
| Directing and supervising AI tools | Solo proof credit |
| Explaining and communicating results | Competition-style problem solving as an identity |

### Why this is a fair reading of the wider evidence

The session's other notes already describe the pieces of such infrastructure:

- **Verification as shared infrastructure.** Lean, Mathlib and CI act as the referee, so
  contributors need not be trusted ([crowdsourced GitHub maths](crowdsourced-github-mathematics.md)).
- **Mapping, not summiting.** Tao's "population surveys" and the Erdős problems and
  optimisation-constants repositories are catalogues of whole terrain, which is the "satellite"
  stage ([Tao's Math 2.0](tao-math-2-0.md)).
- **Agent platforms.** Surveyed in [AI mathematics research tools](ai-mathematics-research-tools.md).
- **Where the metaphor strains.** Gowers's "jagged frontier" ([note](jagged-frontier-gowers.md))
  says AI is strong in some regions and weak in others, which a smooth "airplane gets better"
  story hides. Opaque "alien" proofs ([note](opacity-alien-proofs.md)) are a map that
  humans cannot read.

### The "flags on rocks" dispute

This is the most concrete point in the essay for our session. The complaint is about **credit and
motivation**: if an AI lab announces a solution to a problem on which people were making progress,
others stop. Szegedy sides with the explorers' *request* (test the planes on something else) but
not with their *scepticism* about the planes. This links to the Erdős-problems dispute over what counts
as an "autonomous" solution, in the research brief.

## 4. Critical points for discussion

These are our observations, not claims in the essay.

- **Industrial maths needs an industrial economy.** Who pays, who owns the output, and who sets
  the "terrain" priorities? Szegedy says the funding comes from applications. That is a strong
  claim and he doesn't test it.
- **Verification is the bottleneck, not generation.** Infrastructure works only if checking is
  cheap and trusted. See the autoformalisation fidelity problem ("is the formal statement the one we meant?")
  in the research brief.
- **Is "lone hero" an accurate picture of the past?** Polymath, Bourbaki and large collaborations
  (classification of finite simple groups) already show maths done at scale. The essay arguably
  describes prestige more than practice.
- **Training pipeline.** If "climbing rocks to hone tools" loses its point, how do future
  mathematicians acquire the taste that the essay says will matter most?
- **Author's position.** Szegedy builds autoformalisation systems, so his predictions are also
  advocacy. He says himself that his view is not consensus.
- **Pace.** The essay predicts slow institutional change and fast technical change. The gap is
  where the tension in the Fields Medallists' and Leiden statements sits.

## 5. Suggested discussion prompts

1. Is the "lone hero" model of maths a historical reality or a story we tell about prestige?
2. Which stage of the aviation analogy are we in, and what would count as evidence of the next one?
3. If taste and problem selection become the scarce skill, what should RSEs learn from how software
   moved from craft to infrastructure?
4. Who should own the "map" produced by industrial maths, and who maintains it?
5. Do "flags on rocks" matter? What credit norms would let AI results and human explorers coexist?

## 6. Allies named in the essay

Szegedy names his brother **Balázs Szegedy** (early adopter) and **Jared Duker Lichtman** and
**Michael R. Douglas** ("very outspoken, working toward the same vision"). We haven't yet checked
what each has said publicly; a follow-up note could. Reactions found so far are brief: two Bluesky
posts, one mostly agreeing with some nuance
([Jake](https://bsky.app/profile/yetanotheruseless.com/post/3mxch2tjlwk22)), one calling it a "great essay"
([Alex Rubinsteyn](https://bsky.app/profile/alexr.bsky.social/post/3mwzc5hrjv22r)).
