# NVIDIA NemoClaw & OpenShell — Secure Runtimes for Autonomous Agents

**Session:** 31 March 2026 · 3:00–4:30 pm
**Lead:** TBD

---

## Overview

As AI agents gain the ability to execute code, call APIs, and interact with file systems, the attack surface they expose grows dramatically. NVIDIA's NemoClaw and OpenShell — both announced at GTC 2026 — address this problem from complementary angles. **OpenShell** is a runtime confinement layer: it wraps agent tool-calls in a policy-enforced sandbox, controlling which binaries, paths, and network endpoints an agent may touch. **NemoClaw** is a broader safety stack built on top of NeMo that integrates guardrails, provenance tracking, and encrypted routing ("privacy routing") for sensitive workloads. Together they represent NVIDIA's answer to a key open question in production agentic AI: *how do you give an agent real capabilities without giving it unlimited access?*

---

## Background reading

Work through these before the session — in order if time is short:

1. **NemoClaw product page** — high-level pitch and architecture overview
   <https://www.nvidia.com/en-gb/ai/nemoclaw/>

2. **OpenShell GitHub repository** — source, README, and the policy schema
   <https://github.com/NVIDIA/OpenShell>

3. **NVIDIA developer blog** https://developer.nvidia.com/blog/run-autonomous-self-evolving-agents-more-safely-with-nvidia-openshell/ and https://nvidianews.nvidia.com/news/nvidia-announces-nemoclaw

---

## Timed agenda

| Time        | Activity                                          | Who        |
|-------------|---------------------------------------------------|------------|
| 3:00–3:15   | Intro & framing — why agent security matters now  | Lead       |
| 3:15–3:35   | OpenShell deep dive — policy model & runtime      | Lead       |
| 3:35–3:50   | NemoClaw stack overview — guardrails & routing    | Lead       |
| 3:50–4:15   | Practical activity (see below)                    | All        |
| 4:15–4:30   | Discussion & evaluation (see prompts below)       | All        |

Total: 90 minutes.

---

## Practical activity (~25 min)

**Goal:** hands-on exploration of the OpenShell policy model — no NVIDIA hardware or GPU required.

### Setup (5 min)

Each person or pair picks one of the fictional agent use-cases below:

| Use-case | Agent description |
|----------|-------------------|
| **A** | A research assistant that reads PDFs from a shared drive, queries PubMed, and writes summary reports to a results folder |
| **B** | A data-cleaning pipeline that reads CSVs from an S3 bucket, runs a Python transformation script, and writes cleaned output back |
| **C** | A code-review bot that clones a repo, runs tests, and posts a comment to GitHub via the API |

### Task (15 min)

Draft an OpenShell policy file (YAML) for your use-case. Your policy should specify:

- **`allowed_binaries`** — executables the agent may invoke (e.g. `python3`, `curl`, `git`)
- **`filesystem`** — paths the agent may read and/or write, with permissions (`ro`/`rw`)
- **`network`** — hostnames or CIDR ranges the agent may reach outbound

Use the OpenShell schema as your reference: <https://github.com/NVIDIA/OpenShell>

**Starter template:**

```yaml
# OpenShell policy — [your use-case label]
version: "1.0"

binaries:
  allowed:
    - /usr/bin/python3
    # add more…

filesystem:
  - path: /data/input
    mode: ro
  - path: /data/output
    mode: rw
  # add more…

network:
  allowed_hosts:
    - api.example.com
  # or use allowed_cidrs: ["10.0.0.0/8"]
```

### Swap & critique (5 min)

Swap policies with another person/pair. Review for:

- Over-permissive entries (e.g. `/` as a readable path)
- Missing restrictions (e.g. no network block when the agent doesn't need internet)
- Privilege creep — does the policy grant more than the stated use-case needs?

---

## Discussion & evaluation prompts

Use these to structure the final 15 minutes. Aim to cover at least three.

1. **Security guarantees vs. claims** — What does OpenShell *actually* prevent, and what does it leave open? Is a policy-file model sufficient, or does it just shift the attack surface?

2. **Comparison with existing sandboxing** — How does this compare to Docker, nsjail, Firecracker, or gVisor? What does OpenShell add, and what does it give up?

3. **Trust boundaries** — Who writes and audits the policies? What happens when the agent itself can suggest policy changes?

4. **Privacy routing credibility** — Is NVIDIA's "privacy routing" model a meaningful guarantee for sensitive research data, or is it marketing? What would you need to verify before relying on it?

5. **Adoption question** — Would you use this in your own work? What would need to change — technically, organisationally, or in terms of maturity?

6. **Ecosystem position** — How does the NemoClaw stack compare to alternatives like LangGraph + Docker, E2B, or Modal for sandboxed agent execution?
