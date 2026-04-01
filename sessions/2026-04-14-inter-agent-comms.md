# Inter-Agent Communication Protocols — A2A and Beyond

- **Session:** 14th April 2026
- **Lead:** Chris Wild

---

## Overview

As multi-agent systems move from research curiosity to production infrastructure, a critical question emerges: *how should agents talk to each other?* Each agent framework — LangGraph, CrewAI, Semantic Kernel, AutoGen — has historically invented its own conventions, making cross-framework collaboration fragile or impossible. Standardised inter-agent protocols aim to fix this.

The **Agent2Agent (A2A) Protocol**, originally developed by Google and now stewarded by the Linux Foundation, is the most prominent current proposal. It defines a common language for agent interoperability: how one agent advertises its capabilities, how another delegates a task to it, and how results flow back — all without either agent needing to expose its internal memory, tools, or reasoning. A2A sits alongside Anthropic's **Model Context Protocol (MCP)**, which handles agent-to-tool communication, forming a complementary pair that together cover most of the message-passing surface in a modern agentic system.

This session examines A2A in depth, compares it with MCP and HTTP/REST conventions, and asks what adoption would look like in a research computing context.

---

## Background reading

Work through these before the session — in order if time is short:

1. **A2A specification** — the authoritative protocol reference; focus on "Life of a Task" and "Capabilities Discovery"
   <https://a2a-protocol.org/latest/>

2. **A2A GitHub repository** — source, JSON schemas, and sample agents
   <https://github.com/a2aproject/A2A>

3. **A2A samples** — worked examples of multi-agent task delegation in Python and JavaScript
   <https://github.com/a2aproject/a2a-samples>

4. **MCP specification** (Anthropic) — skim the overview to understand how A2A and MCP divide responsibilities
   <https://spec.modelcontextprotocol.io/>

---

## Timed agenda

| Time        | Activity                                                        | Who   |
|-------------|-----------------------------------------------------------------|-------|
| 3:00–3:10   | Intro & framing — the interoperability problem                  | Lead  |
| 3:10–3:30   | A2A deep dive — capabilities discovery, task lifecycle, streaming | Lead  |
| 3:30–3:45   | A2A vs MCP — how the two protocols divide the message space     | Lead  |
| 3:45–4:10   | Practical activity (see below)                                  | All   |
| 4:10–4:30   | Discussion & evaluation (see prompts below)                     | All   |

Total: 90 minutes.

---

## Practical activity (~25 min)

**Goal:** hands-on design exercise mapping a realistic multi-agent workflow onto A2A concepts — no running code or special tooling required.

### Setup (5 min)

Each person or pair picks one of the fictional multi-agent scenarios below:

| Scenario | Description |
|----------|-------------|
| **A** | A **literature-review pipeline**: an orchestrator agent delegates to a search agent (PubMed queries), a summarisation agent (abstracts → bullet points), and a citation-formatter agent (BibTeX output) |
| **B** | A **data-cleaning workflow**: a coordinator delegates raw CSV ingestion to a validation agent, outlier detection to a statistics agent, and report generation to a visualisation agent |
| **C** | A **code-review system**: a triage agent routes incoming PRs to a style-checker agent, a security-scanner agent, and a test-runner agent; results are aggregated back to the triage agent |

### Task (15 min)

Sketch the A2A interactions for your scenario. For each agent-to-agent call, note:

- **Caller** and **Callee** — which agent is delegating, which is receiving
- **Task description** — one sentence stating what is being requested
- **Input message** — the key fields the caller sends (e.g. document text, file path, query string)
- **Output message** — what the callee returns on success
- **Failure mode** — one realistic way this call could go wrong, and how the caller should handle it

Use this table template:

| Caller | Callee | Task description | Input fields | Output fields | Failure mode |
|--------|--------|-----------------|--------------|---------------|--------------|
| … | … | … | … | … | … |

Reference the A2A "Life of a Task" section for the correct state transitions: `submitted → working → completed / failed`.

### Swap & critique (5 min)

Exchange sketches with another pair. Review for:

- **Missing capability discovery** — does the caller know the callee exists and what it accepts?
- **Implicit trust** — is any agent assumed to always succeed, or is error handling explicit?
- **Leaky internals** — does the caller need to know more about the callee's implementation than it should?

---

## Discussion & evaluation prompts

Use these to structure the final 20 minutes. Aim to cover at least four.

1. **Protocol necessity** — Is a formal inter-agent protocol actually needed, or is REST + OpenAPI sufficient? What does A2A add that you couldn't get from a well-documented HTTP API?

2. **Trust and identity** — A2A emphasises that agents collaborate *without* exposing their internals. But who authenticates whom? How does an agent know the callee is the agent it claims to be, and not a rogue or compromised agent?

3. **MCP vs A2A boundary** — The positioning is: MCP for agent-to-tool, A2A for agent-to-agent. In practice, is this boundary clean? Can you think of cases where it blurs?

4. **Streaming and async** — A2A explicitly supports streaming and long-running asynchronous tasks. Why does this matter for agent workflows that plain request/response HTTP would struggle with?

5. **Governance and standards process** — A2A moved from Google to the Linux Foundation. What does that mean for adoption, fragmentation risk, and long-term stability? How does it compare to how MCP is governed?

6. **Research computing fit** — Most RSE and research contexts involve bespoke pipelines, HPC clusters, and constrained budgets. What assumptions in A2A (persistent services, public endpoints, enterprise auth) *don't* hold in a typical university research setting? What would need to change?

7. **Ecosystem momentum** — A2A already has SDKs in Python, JavaScript, Java, Go, and C#. Does early SDK breadth signal genuine adoption or vendor positioning? What would you look for to judge whether a protocol is becoming a genuine standard?

---

# Links

Specification and reference

- [A2A Protocol specification](https://a2a-protocol.org/latest/)
- [A2A GitHub repository](https://github.com/a2aproject/A2A)
- [A2A sample agents](https://github.com/a2aproject/a2a-samples)

Related protocols

- [Model Context Protocol specification](https://spec.modelcontextprotocol.io/)
- [Model Context Protocol GitHub](https://github.com/modelcontextprotocol/specification)
