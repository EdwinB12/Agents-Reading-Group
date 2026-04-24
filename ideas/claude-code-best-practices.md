# Claude Code: Best Practices and Workflows

**Proposed by:** Joe Heffer
**Suggested format:** demo / exercise

## Why interesting

Claude Code is a powerful but easy-to-misuse tool — without deliberate practices around context management, project configuration, and token costs it quickly becomes expensive and unreliable. This session would give members practical, transferable habits for using it effectively on real RSE projects.

## Links

- [Claude Code best practices (official)](https://docs.anthropic.com/en/docs/claude-code/best-practices) — context management, verification strategies, explore→plan→code workflow, session management
- [Common workflows (official)](https://docs.anthropic.com/en/docs/claude-code/common-workflows) — codebase exploration, bug fixing, refactoring, PRs, subagents
- [Managing costs effectively (official)](https://docs.anthropic.com/en/docs/claude-code/costs) — `/usage` tracking, spend limits, context strategies, model selection
- [Hooks guide (official)](https://docs.anthropic.com/en/docs/claude-code/hooks-guide) — automating formatting, linting, security checks at lifecycle points
- [MCP: connecting Claude Code to tools (official)](https://docs.anthropic.com/en/docs/claude-code/mcp) — extending Claude Code with external services
- [50 Claude Code tips — Builder.io](https://www.builder.io/blog/claude-code-tips-best-practices) — practical daily-use tips from a production team
- [Claude Code best practices: lessons from real projects](https://ranthebuilder.cloud/blog/claude-code-best-practices-lessons-from-real-projects/) — real-world experience report
- [Claude Code best practices: planning, context transfer, TDD — DataCamp](https://www.datacamp.com/tutorial/claude-code-best-practices) — test-driven development workflow with Claude Code

## Notes

Suggested themes to cover:

1. **CLAUDE.md as shared team knowledge** — version-controlled conventions, environment setup, gotchas; makes agentic behaviour reproducible across contributors
2. **Context is the constraint** — understanding the context window, when to use `/clear`, compaction, and why specific prompts beat vague ones
3. **Token cost awareness** — reading `/usage` output, choosing the right model (Haiku vs Sonnet vs Opus) for the task, avoiding context bloat from large MCP servers
4. **Hooks for deterministic steps** — offloading formatting/linting/security checks from Claude to hooks so they always run
5. **Explore → plan → code workflow** — using subagents or read-only passes to understand a codebase before generating changes

A live demo on a real (or toy) RSE project would work well — e.g. adding a feature to a small Python package while narrating the context-management decisions in real time.

Prerequisites: members should have Claude Code installed (`npm install -g @anthropic-ai/claude-code`) and an Anthropic API key or Claude Pro/Max subscription.
