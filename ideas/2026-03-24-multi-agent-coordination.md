# Multi-Agent Coordination: Protocols, Observability & Human-in-the-Loop

**Proposed by:** Community
**Date added:** 2026-03-24
**Suggested format:** hybrid reading / discussion with optional hands-on component

## Why interesting

When tasks require multiple AI agents working together, naïve approaches ("just add more agents") lead to coordination collapse — agents overwriting each other's state, losing shared context, or silently failing. This session explores principled coordination design: explicit state management, role specialisation, observability, and treating humans as first-class participants rather than bolt-on approvers. Inspired by [CommonGround](https://github.com/Intelligent-Internet/CommonGround), an open-source multi-agent OS from Intelligent Internet.

## Links

- [CommonGround GitHub](https://github.com/Intelligent-Internet/CommonGround)
- [CommonGround paper / announcement](https://github.com/Intelligent-Internet/CommonGround)

## Notes

Full session content (agenda, background reading, practical activities) was drafted in the original PR. Key topics: Swarm vs. Pipeline vs. Hierarchy architectures, state vs. signal separation (PostgreSQL ledger + NATS doorbell pattern), three-view observability (Flow / Kanban / Timeline), and human-in-the-loop as coordination protocol. Can be developed into a full session when a lead is identified.
