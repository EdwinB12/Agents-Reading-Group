# Literature-Based Discovery: A Concise Primer

## What it is

Literature-based discovery (LBD), sometimes called literature-related discovery (LRD), is a family of methods for generating new hypotheses by mining connections that are implicit across a body of published literature but have never been explicitly stated in any single paper. Rather than reading for confirmation of what is already known, LBD systems look for pairs of concepts that are individually well-connected to a common third concept but disconnected from each other — flagging that gap as a candidate for new knowledge.

The field originated in biomedicine and remains most developed there, but the underlying logic (connecting two disjoint literatures via a shared intermediate concept) generalises to any domain with a large enough corpus of structured text.

## The ABC paradigm

The core logic underpinning most LBD systems is the **ABC model**:

* If concept A is shown in one part of the literature to relate to concept B, and
* concept B is shown elsewhere to relate to concept C,
* then A and C may be related — even if no paper ever discusses A and C together.

This is often called **Swanson linking**, after the technique's originator. There are two standard modes of operation:

* **Open discovery** — starting from a single concept A, the system searches for intermediate Bs and surfaces candidate Cs, generating novel hypotheses.
* **Closed discovery** — given both A and C, the system searches for the Bs that plausibly connect them, effectively testing a hypothesis rather than generating one from scratch.

A frequent criticism of the ABC paradigm is that it presumes scientific knowledge can be reduced to simple pairwise assertions, when much of it is actually embedded in analogy, structure, and higher-level abstraction that a co-occurrence model cannot easily capture.

## Origins and key figures

* **Don R. Swanson** (University of Chicago) pioneered LBD in the 1980s. His best-known result linked fish oil to Raynaud's syndrome via their shared relationship to blood viscosity — a hypothesis proposed purely from disjoint literatures and later given some support by a prospective clinical study. He went on to propose several other candidate discoveries using the same method (e.g. migraine–magnesium, somatomedin C–arginine).
* **Neil R. Smalheiser** frequently collaborated with Swanson and has written extensively on the field's history and its methodological successors, including the Arrowsmith system.
* **Marc Weeber**, **Dimitar Hristovski**, and colleagues developed several early operational systems (DAD, BITOLA) and did significant work on integrating genetic and semantic knowledge into LBD.
* **Anna Korhonen**'s group (Cambridge) has been a notable UK contributor, particularly on applying neural network methods to open and closed discovery and on text-mining tools for cancer biology (e.g. LION LBD, built with Sampo Pyysalo and colleagues).
* **Trevor Cohen** has contributed methods based on distributional semantics (Reflective Random Indexing) for scaling discovery of implicit connections.

## Methods, in broad strokes

* **Co-occurrence and association-rule mining** — the earliest and still-common approach: identify terms that co-occur unusually often within abstracts, typically using MeSH (Medical Subject Headings) terms as the unit of representation.
* **Knowledge-graph and graph-database approaches** — represent concepts and relations as a graph (sometimes implemented in systems like Neo4j) and use graph traversal or query languages (e.g. Cypher) to find candidate paths between distant nodes.
* **Semantic relation extraction** — rather than raw co-occurrence, extract typed relations (e.g. "treats", "causes", "inhibits") often drawing on the UMLS Semantic Network, to make ABC links more meaningful than statistical coincidence.
* **Distributional and neural methods** — later systems apply embeddings and neural architectures to represent concepts and predict plausible but unstated links, moving beyond purely symbolic co-occurrence statistics.
* **Word-sense disambiguation** is a persistent technical prerequisite, since biomedical acronyms are highly ambiguous (a gene symbol may collide with an imaging-technique acronym, for instance).

## Notable systems

A rough chronology of published LBD systems includes: Arrowsmith (1986, later revised in 2007), BITOLA (2000, revised 2005), DAD (2001), LitLinker (2003, revised 2006), Manjal (2004), IRIDESCENT (2004), Anni 2.0 (2008), CoPub Discovery (2008), RajoLink (2009), Sem-BT (2010), Spark (2016), and LION LBD (2019). Arrowsmith remains the most widely cited "two-node search" tool, designed specifically to bridge two disjoint sets of articles.

## Evaluation challenges

Evaluating LBD is genuinely difficult, for a few structural reasons:

* There is no consensus on what counts as a successful "discovery," making standard test sets hard to construct.
* **Replication of known discoveries** (e.g. re-deriving the fish oil–Raynaud's link from pre-1985 literature) is the most common evaluation method, but there are only a handful of canonical cases to test against, risking overfitting of methods to these specific examples.
* **Time-slicing** — training a system only on literature up to a cut-off date, then checking whether it "predicts" links that later appeared — allows evaluation at much larger scale, using standard information-retrieval metrics (precision, recall, AUC, mean average precision).
* A high-precision but expensive alternative is expert-generated gold standards, which tend to have low recall.

## Applications beyond drug repurposing

While LBD is best known for **drug repurposing and identifying candidate genes for disease** (its original domain), it has also been applied to:

* predicting adverse drug reactions;
* identifying disease biomarkers (e.g. for type 2 diabetes);
* uncovering confounding factors in observational clinical data;
* studying disease comorbidity and shared aetiology (e.g. gene overlap between myocardial infarction and depression);
* a small number of applications outside biomedicine, including water purification research and identifying promising cross-disciplinary research collaborations.

## Key papers and further reading

* Swanson, D. R. (1986). *Fish Oil, Raynaud's Syndrome, and Undiscovered Public Knowledge*. Perspectives in Biology and Medicine, 30(1), 7–18. — The foundational paper.
* Swanson, D. R., & Smalheiser, N. R. (1997). *An interactive system for finding complementary literatures: a stimulus to scientific discovery*. Artificial Intelligence, 91(2), 183–203.
* Smalheiser, N. R. (2017). *Rediscovering Don Swanson: The Past, Present and Future of Literature-based Discovery*. Journal of Data and Information Science, 2(4), 43–64. — A good historical overview from a close collaborator.
* Yetisgen-Yildiz, M., & Pratt, W. (2006, 2008, 2009). Several papers establishing statistical/knowledge-based approaches and evaluation methodology for LBD systems.
* Henry, M. S. S., & McInnes, B. T. (2017). *Literature Based Discovery: models, methods, and trends*. Journal of Biomedical Informatics, 74, 20–32. — A useful modern survey.
* Gopalakrishnan, V., Jha, K., Jin, W., & Zhang, A. (2019). *A survey on literature based discovery approaches in biomedical domain*. Journal of Biomedical Informatics, 93, 103141.
* Pyysalo, S., et al. (2018). *LION LBD: a literature-based discovery system for cancer biology*. Bioinformatics, 35(9), 1553–1561. — Anna Korhonen's group, relevant given the UK angle.
* Crichton, G., Baker, S., Guo, Y., & Korhonen, A. (2020). *Neural networks for open and closed Literature-based Discovery*. PLOS ONE, 15(5), e0232891. — Marks the shift toward neural approaches.
* Bruza, P., & Weeber, M. (eds.) (2008). *Literature-based Discovery*. Springer (Information Science and Knowledge Management series). — The closest thing the field has to an edited reference volume, bringing together contributions from most of the major figures above.
* Wilson, P. (1977). *Public Knowledge, Private Ignorance: Toward a Library and Information Policy*. Greenwood Publishing Group. — An earlier, foundational information-science text on the general problem LBD later formalised: that useful connections can sit unrecognised across separately published, mutually unaware bodies of literature.

## A note on relevance to your work

LBD is conceptually adjacent to, but distinct from, the literature-review pipeline you've been sketching (OpenAlex, Semantic Scholar, ASReview, Claude). A review pipeline aggregates and filters existing knowledge; LBD tries to generate genuinely new hypotheses from the structure of disconnected literatures. The evaluation difficulties documented above — no consensus on what counts as a discovery, reliance on a handful of replicable historical cases, the gap between statistical plausibility and actual causal validity — are a useful cautionary parallel to the attribution problem you've flagged elsewhere: in LBD, as in AI-assisted discovery more broadly, novelty tends to belong to the search process and its human interpreter rather than to any single algorithmic step in isolation.
