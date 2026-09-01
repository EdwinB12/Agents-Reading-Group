# Model Hardware Standard: agents that drive lab instruments

**Proposed by:** Joe Heffer
**Suggested format:** paper + discussion

## Why interesting

Most of what this group has discussed keeps the agent inside the computer — reading, writing, calling APIs. The Model Hardware Standard (MHS) is Anthropic's research-preview attempt to let agents discover and operate *physical* instruments: microscopes, liquid handlers, lasers, manufacturing kit. Three things make it worth a session. First, the failure mode changes character — a bad tool call is no longer a bad commit but a broken sample or a damaged instrument, which reframes everything we've said about guardrails and human-in-the-loop. Second, MCP appears here as one of three control surfaces alongside a CLI and code-file APIs, so it's a useful test of how far that abstraction stretches beyond software. Third, it's squarely RSE work: writing bespoke integration glue between instruments and analysis code is a job many of us have actually done, and the claim is that it drops from weeks to hours.

## Links

- [Previewing the Model Hardware Standard (Anthropic announcement)](https://www.anthropic.com/news/model-hardware-standard-research-preview) — the article that prompted this idea
- [Related in-repo idea: Claude Science workbench](claude-science-workbench.md) — the software-side counterpart; same "agents in the lab" theme, but stops at the compute boundary

## Notes

**What it actually is**

- A shared specification that makes each device discoverable in a standard format, so agents and instruments can find each other across a network without a bespoke translator program for every pairing.
- Standardised **drivers** that translate between the operating system and the hardware, exposing simple primitives — essentially `read` and `write`.
- **Natural-language tags** attached to each device, recording its characteristics and safe operating parameters so an agent can reason about what it is allowed to do to the thing.
- A shared **state dictionary in memory**: per the HHMI Janelia example, each device's variables, controls, and sensor values live in one dictionary in shared memory, so several programs can read device state at once without custom bridges.
- Three ways to drive it: **MCP**, a **command-line interface**, and **code-file APIs**.
- Currently a research preview limited to scientific research labs and advanced manufacturers, with open-sourcing gated behind a "physical safety roadmap".

**What the partners reported** (claims from the announcement, not independently verified)

- **Carnegie Mellon** — serial dilution dose-response experiments roughly 3x faster; integration took about eight hours rather than weeks.
- **University of Washington** — six instruments integrated in under a week.
- **QuEra Computing** — laser-locking recovery improved from 58% success in ~150 seconds to 99.3% in 0.9–14 seconds.
- **Genentech** — autonomous optimisation of BCA protein assay parameters that would normally need manual specialist work.

**Stated limitations** — unusually candid, and the most interesting part

- Claude struggles with physical, chemical, and biological constraints. In the Genentech case it didn't initially grasp that bubble formation was a *physical* problem, and went looking for a software bug.
- Spatial and physical reasoning are limited because the model learned the physical world through text and images.
- MHS doesn't work with hardware that has no programming interface at all.
- Running an agent continuously over long monitoring windows costs compute, which UW notes has to be weighed against the researcher time saved.

### Discussion prompts

- Our usual safety story assumes mistakes are cheap and reversible — you revert the commit. What has to change in an agent's design when the action is irreversible and physical?
- Safe operating parameters are encoded as *natural-language tags*. Is that a real safety mechanism, or a soft one dressed up as a spec? What would a hard interlock look like instead, and should the standard mandate one?
- The bubble-formation example — an agent misclassifying a physical problem as a software bug — looks like a general failure mode: agents debug in the domain they know. Where have we seen the software equivalent in our own work?
- Is MCP the right abstraction for hardware? A device driver has latency, state, and exclusivity constraints that a tool call doesn't. What does MCP hide here that matters?
- UW's point about continuous-agent compute cost vs researcher time is the honest version of the ROI question. How would you actually decide, for a workflow you own, whether an always-on agent pays for itself?

### Practical things to try

No preview access needed for any of these:

- Compare the MHS model (standardised driver + device tags + shared state dictionary) against the MCP servers already wired into our own environments. Same protocol in the mix — what does the hardware case need that our software servers don't provide?
- Pick one instrument or piece of kit someone in the group genuinely uses, and sketch its MHS-style description: what tags would you write, and what is its safe operating envelope in words? The exercise usually exposes how much of that knowledge is tacit.
- Audit our own agent workflows for irreversible side effects — deploys, emails, data deletion, spend — and work out which gating pattern each one needs. Useful even for those of us nowhere near a lab bench.
