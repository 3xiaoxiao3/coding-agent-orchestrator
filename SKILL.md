---
name: coding-agent-orchestrator
description: Route software-engineering work among the main agent, subagents, and GPT-5.6 Luna/Sol or GPT-6 Astra based on reading breadth, decision risk, review depth, context cost, and parallelism. Use for complex coding tasks, broad repository exploration, formal code review, architecture work, or when the user asks to optimize agent/model routing or token usage. Skip for trivial, narrow tasks where dispatch overhead exceeds its value.
---

# Coding Agent Orchestrator

Optimize for total useful work, not agent count: minimize irrelevant context and latency while preserving decision quality.

## Classify the work

Assess three axes before acting:

- **Breadth:** how much code, documentation, or output must be read.
- **Risk:** the consequence of a wrong implementation or judgment.
- **Coupling:** whether subtasks are independent enough to run concurrently.

Use the main agent for narrow reading, edits, final decisions, and verification. When delegation is available and authorized, use subagents for broad read-only exploration, evidence collection, compression, or independent checks whose results can be summarized sharply.

Keep foundational architecture, design, ADR, handoff, and core business-rule documents in the main agent's context. The main agent must also read the exact code it will modify.

## Route models

Use the compact rule: **Luna gathers, Sol solves, Astra judges.** Risk outranks apparent difficulty; reasoning effort does not substitute for a stronger model.

- Use Luna Medium for delegated searches, extraction, classification, broad low-risk read-only exploration, large inputs, and evidence compression.
- Use Sol for implementation, debugging, tests, module analysis, and ordinary formal review.
- Use Astra for architecture decisions, high-risk review, conflicting evidence, or final judgment on critical changes.

Read [model-routing.md](references/model-routing.md) only when model choice is consequential or ambiguous.

## Route optional detail

- For broad exploration, multiple independent questions, delegation boundaries, evidence format, or timeouts, read [subagents.md](references/subagents.md).
- For a requested formal code review or risk-focused audit, read [review-policy.md](references/review-policy.md).
- Do not preload every reference. Read only the reference needed for the current task.

## Preserve decision ownership

Treat subagent output as compressed evidence, not authority. Check cited locations or symbols selectively, resolve conflicts, perform edits in the main agent, and run the final verification there. Do not re-read all delegated material unless the evidence is incomplete or inconsistent.
