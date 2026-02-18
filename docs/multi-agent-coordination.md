# Multi-Agent Coordination: Protocols, Observability & Human-in-the-Loop

> Reference document for the reading group session on coordinating teams of AI agents.
> Inspired by [CommonGround](https://github.com/Intelligent-Internet/CommonGround) — an open-source multi-agent OS from Intelligent Internet.

---

## Session Overview

**Duration**: 2.5–3 hours
**Format**: Hybrid reading/discussion with optional hands-on component
**Audience Level**: Intermediate (assumes familiarity with single-agent systems; no distributed systems background required)
**Primary Question**: *When a task requires multiple AI agents working together, how do we design coordination protocols that prevent chaos — and keep humans genuinely in control?*

---

## Background

Single-agent systems are well understood. But real-world tasks — literature reviews, software projects, complex research — quickly exceed what one agent can handle. The naive solution (just add more agents) breaks down: agents overwrite each other's state, lose shared context, produce contradictory outputs, or silently fail. CommonGround calls this **"coordination collapse."**

The interesting design challenge is not making agents smarter in isolation — it's making *teams* of agents coherent. This requires:

- **Explicit state management**: who owns what truth, and how is it updated atomically?
- **Role specialisation**: how do you decompose work without losing coherent intent?
- **Observability**: how do humans (and other agents) understand what's happening inside a multi-agent run?
- **Human participation as first-class**: humans aren't just initiators or approvers — they can inject intent mid-flight, the same way agents do

---

## Learning Objectives

By the end of this session, participants should be able to:

1. Explain "coordination collapse" and why naively scaling agents causes it
2. Compare protocol-first vs. framework-first approaches to multi-agent architecture
3. Evaluate the trade-offs of hierarchical agent roles (Partner / Principal / Associate pattern)
4. Articulate how state-vs-signal separation prevents distributed split-brain failures
5. Design an observability strategy for a multi-agent pipeline they're building or considering
6. Assess when human-in-the-loop should be baked into the coordination protocol vs. bolted on

---

## Core Architecture Concepts

### The Coordination Problem

```
Single agent:    [User] → [Agent] → [Result]       ✓ Simple, controllable

Naive multi:     [User] → [Agent A] ↔ [Agent B]    ✗ Who owns state?
                              ↕
                          [Agent C]                 ✗ Context fragmentation

Principled:      [User] → [Partner]
                              ↓ plan
                          [Principal] → [Associate A]
                                      → [Associate B]   ✓ Clear delegation,
                                      → [Associate C]     shared state ledger
```

### State vs. Signal Separation (CommonGround Core)

CommonGround's kernel separates two concerns that naive systems conflate:

| Concern | Component | Guarantee |
|---------|-----------|-----------|
| **Authoritative state** | PostgreSQL with CAS locks on `turn_epoch` | Single source of truth; no split-brain |
| **Wakeup signalling** | NATS JetStream | Low-latency "doorbell"; purely ephemeral |

The key insight: **messages are not state**. If the message queue is the source of truth, you get race conditions and reordering bugs. If the database is the source of truth and messages are merely notifications, the system is resilient to network hiccups, crashes, and redelivery.

### Human as Agent (Not Just User)

CommonGround treats humans as participants in the same coordination protocol as AI agents. Rather than the typical pattern:

```
Human → prompt → Agent → result → Human
```

The protocol supports:

```
Human ⟷ [shared state ledger] ⟷ AI Agent A
                               ⟷ AI Agent B
```

Humans can inject intent, approve actions, or redirect mid-flight — not via special "human-in-the-loop hooks" bolted on, but through the same universal tool protocol (UTP) that agents use.

### Observability: Three Views

CommonGround exposes three complementary interfaces, each surfacing different information:

| View | What it shows | Best for |
|------|---------------|----------|
| **Flow** | Reasoning graph — how decisions connect | Debugging agent logic |
| **Kanban** | Work module status — what's in progress | Project tracking |
| **Timeline** | Chronological execution trace | Auditing and replay |

The design principle: no single view is sufficient. You need structural, progress, and temporal perspectives simultaneously.

---

## Pre-Session Reading (~2–3 hours total)

### 1. The CommonGround System (45 mins)

- **Blog post** — "Common Ground" (Intelligent Internet)
  https://ii.inc/web/blog/post/common-ground
  *Why*: High-level vision and motivation for the system

- **GitHub README** — CommonGround Core
  https://github.com/Intelligent-Internet/CommonGround
  *Focus*: Architecture layers (L0/L1/L2), state-vs-signal separation, universal tool protocol

### 2. Foundational Multi-Agent Thinking (45 mins)

- **Anthropic** — "Building Effective Agents" (Dec 2024) — "Multi-Agent Systems" section
  https://www.anthropic.com/research/building-effective-agents
  *Why*: Practical patterns from production systems; sceptical view of unnecessary complexity

- **Harrison Chase (LangChain)** — "The Many Ways Agents Call Other Agents"
  https://blog.langchain.dev/the-many-ways-agents-call-other-agents/
  *Why*: Taxonomy of subagent patterns — useful contrast to CommonGround's approach

### 3. Observability & Debugging (30 mins)

- **Eugene Yan** — "Patterns for Building LLM-based Systems & Products" — observability section
  https://eugeneyan.com/writing/llm-patterns/
  *Focus*: Evals, tracing, and monitoring in production; what makes agents debuggable?

### 4. Human-AI Teaming (30 mins)

- **Anthropic** — "Human-AI Collaboration" (model card / usage guidelines section on agentic tasks)
  https://www.anthropic.com/claude/model-spec — Section on "Agentic settings"
  *Why*: How to think about human oversight when agents act autonomously

### Optional Deep Dives

- **Original Actors model** — Hewitt, Bishop & Steiger (1973) — for those curious about the theoretical roots of message-passing coordination: https://dl.acm.org/doi/10.1145/1045948.1045954

- **CAP theorem primer** — relevant to why state-vs-signal separation matters in distributed systems: https://www.ibm.com/topics/cap-theorem

- **LangGraph documentation** — state graph approach to multi-agent coordination: https://langchain-ai.github.io/langgraph/

### Pre-Session Task (optional but recommended)

Try to break a simple multi-agent pipeline:

1. Set up two agents that share a task — e.g. one plans, one executes
2. Introduce a failure: kill the executor mid-task, or have both try to write the same output
3. Document: what state was lost? Could you recover? Would CommonGround's CAS-locked ledger have helped?
4. Bring a short description of what broke and why

---

## Session Structure

### Part 1: Framing the Problem (25 mins)

**Opening Exercise** (10 mins):

Prompt: *"You want an agent to do a thorough literature review — reading 50 papers, cross-referencing themes, spotting contradictions, and writing a structured report. Why can't one agent just do this?"*

- Pairs: list the bottlenecks (context window, time, specialisation, parallelism)
- Regroup: which bottlenecks require *coordination* vs. which are just *compute*?

**Key distinctions to draw out**:
- Context window limits → parallelism; but who reconciles parallel work?
- Specialisation (deep reader vs. synthesiser) → role decomposition; but who owns the shared state?
- Long-running tasks → persistence; but what happens on failure mid-flight?

---

### Part 2: Architecture Patterns (40 mins)

**Three coordination models to compare**:

**Model A — The Swarm**
All agents operate independently, communicating via shared memory or message queues. No fixed hierarchy.

**Model B — The Pipeline**
Agents are chained: A's output is B's input. Strict sequential dependency.

**Model C — The Hierarchy (CommonGround's approach)**
Partner (strategy) → Principal (decomposition) → Associates (execution). Shared state ledger, not message passing, as source of truth.

**For each model, evaluate**:

| Criterion | Swarm | Pipeline | Hierarchy |
|-----------|-------|----------|-----------|
| How is shared state managed? | | | |
| What happens on agent failure? | | | |
| Where does human intent live? | | | |
| How do you debug it? | | | |
| When does it break down? | | | |

*Fill in together — there are no objectively correct answers; the goal is to surface trade-offs.*

**Discussion**: CommonGround's YAML-defined roles vs. code-defined roles — what do you gain and lose from declarative agent configuration?

---

### Part 3: The Observability Gap (35 mins)

**Problem statement**: Multi-agent systems are often described as "black boxes within black boxes." Each agent's reasoning is opaque; their interactions even more so.

**Small group exercise** — design an observability system for a 3-agent pipeline:

Scenario: Partner agent takes a user's research question → Principal breaks it into subtasks → Three Associates each search different databases and return summaries → Principal synthesises → Partner presents.

For your observability design, specify:
1. **What** do you log at each step? (inputs, outputs, intermediate reasoning, tool calls?)
2. **When** do you surface information to the human? (continuously, on completion, only on error?)
3. **How** do you represent causality — which Associate's output influenced which part of the synthesis?
4. **What** does "replay" look like if something went wrong three steps ago?

Compare designs across groups. What did different teams prioritise?

**CommonGround's answer**: Flow (causal graph) + Kanban (progress) + Timeline (replay). Discuss: is three views the right answer, or the right starting point?

---

### Part 4: Human-in-the-Loop as Protocol (30 mins)

**The spectrum of human involvement**:

```
Fully autonomous ←————————————————————→ Fully manual
    [agent decides]    [agent proposes,   [human decides,
                        human approves]    agent assists]
```

**CommonGround's claim**: humans should participate via the *same protocol* as agents — not through a special "approval API" bolted on. Discuss: does this matter architecturally? Or is it just aesthetics?

**Case studies** — for each, where on the spectrum is right, and why?

1. An agent summarising 100 emails for a busy researcher
2. An agent drafting and scheduling social media posts for a brand
3. An agent autonomously patching security vulnerabilities in production code
4. An agent coordinating travel bookings across multiple suppliers

**Key tensions**:
- More human oversight → safer but slower and more expensive
- Less oversight → faster but harder to catch subtle errors or value misalignment
- Mid-flight injection (changing intent partway through) — when is this a feature vs. a footgun?

---

### Part 5: Building on CommonGround (20 mins)

**Hands-on exploration** (if time allows):

CommonGround Core is open source. Look at the repository structure together:
- Where does the CAS lock live in the schema?
- How is a "worker" defined? What does the Universal Tool Protocol require?
- How do you add a new Associate with a custom capability?

**Discussion prompts**:
- "This is described as a 'sociotechnical OS.' What does that mean for how you'd deploy it in a research software context?"
- "The README warns: 'unauthenticated endpoints with RCE capabilities should never be exposed publicly.' What does that tell you about the current maturity level?"
- "If you were building a literature review pipeline for your team tomorrow, would you use CommonGround, LangGraph, or something else? Why?"

---

### Part 6: Synthesis & Action Planning (10 mins)

Each participant writes down:
1. One coordination pattern from today they want to try in a real project
2. One aspect of multi-agent observability they hadn't considered before
3. One open question — about the architecture, the theory, or the practice

---

## Optional Hands-On Lab (+60 mins)

**Goal**: Build a minimal 3-agent coordination system and observe its failure modes.

**Setup**:
1. Start with a simple LangGraph (or plain Python) pipeline: Planner → [Researcher A, Researcher B] → Synthesiser
2. Give it a research task (e.g. "summarise the last 5 years of work on RAG evaluation")

**Experiments**:

| Experiment | What to observe |
|------------|-----------------|
| Kill Researcher A mid-run | Does the Synthesiser handle partial results gracefully? |
| Inject a contradictory finding | Does the Synthesiser surface the contradiction or silently reconcile? |
| Change the task mid-flight | Can you redirect the Planner without restarting? |
| Scale to 5 Associates | Does anything break at the coordination layer? |

**Debrief**: What would a state ledger (rather than message passing) have changed in each case?

---

## Tools & Resources

### Projects to explore

- **CommonGround Core** — https://github.com/Intelligent-Internet/CommonGround
- **LangGraph** — graph-based state machine approach to multi-agent coordination: https://langchain-ai.github.io/langgraph/
- **CrewAI** — role-based multi-agent framework: https://docs.crewai.com/
- **AutoGen** — Microsoft's conversation-based multi-agent system: https://microsoft.github.io/autogen/

### Observability tools

- **LangSmith** — tracing and debugging for LangChain/LangGraph pipelines
- **Arize Phoenix** — open-source LLM observability with trace visualisation
- **Weights & Biases Weave** — experiment tracking extended to agent traces

### Further reading

- "Agent Protocol" (AI Engineer Foundation) — an attempt at a standard API for agent task management
- "ReAct: Synergizing Reasoning and Acting in Language Models" — foundational paper on the action-observation loop that underlies most agent architectures
- Anthropic's "Multi-agent framework" section in their API docs

### Video resources

- CommonGround demo walkthrough: https://ii.inc/web/blog/post/common-ground (embedded)
- LangGraph multi-agent tutorial (LangChain YouTube channel)
