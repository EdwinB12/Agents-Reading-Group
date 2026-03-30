# Agent benchmarks and evaluation science

**Proposed by:**
**Suggested format:** paper + discussion

## Why interesting

Evaluating agents is hard: standard LLM benchmarks (MMLU, GSM8K, etc.) are largely irrelevant for agentic systems, because what matters is the *trajectory* — the sequence of tool calls, reasoning steps, and self-corrections — not just the final answer. Benchmarks saturate quickly, tasks leak into training data, and aggregate scores can hide brittle failure modes. Understanding how benchmarks are built — and where they break — is essential for any team building or deploying agents.

## Links

- [GAIA benchmark (Princeton HAL)](https://hal.cs.princeton.edu/gaia) — general AI assistants benchmark with real-world tasks
- [Agent Research Lab benchmark index](https://agentresearchlab.com/benchmarks/index.html) — curated index of agent evals
- [Definitive AI agent evaluation guide (Confident AI)](https://www.confident-ai.com/blog/definitive-ai-agent-evaluation-guide) — practitioner-oriented evaluation framework
- [AI agent evaluation overview (IBM Think)](https://www.ibm.com/think/topics/ai-agent-evaluation) — introductory conceptual overview
- [SWE-bench](https://www.swebench.com/) — software engineering tasks as an agent benchmark (browse repo, reproduce bug, submit PR)
- [TAU-bench](https://github.com/sierra-research/tau-bench) — business/customer-service agent benchmark with strict policy adherence and messy human users

## Notes

Possible discussion angles:
- What makes a good benchmark? (coverage, difficulty, contamination risk, cost to run)
- How quickly do benchmarks saturate, and what happens next?
- Trajectory metrics vs. outcome metrics: grading the path, not just the answer (tool-call accuracy, self-correction rate, redundant steps)
- The reliability/compounding-failure problem: a 90% per-step success rate over 8 steps yields only ~43% end-to-end success — how should benchmarks surface this?
- GAIA vs SWE-bench vs TAU-bench: different task types, different failure modes
- Evaluation in production vs. in research: where they diverge
- LLM-as-judge approaches and their limitations
