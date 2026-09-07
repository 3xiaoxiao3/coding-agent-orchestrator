# Subagent orchestration

Read this reference for broad repository exploration, multiple independent questions, or substantial context compression.

## Dispatch threshold

Delegate only when a concrete benefit clearly exceeds dispatch and verification cost. Good triggers are:

- two or more independent checks that can run concurrently;
- broad cross-file reading, large logs, generated output, or search results that should collapse into a small evidence set;
- an independent risk check that materially improves confidence.

Do not delegate merely because a task is long. Keep work in the main agent when it concerns a known small file, a single fact, the exact code about to be edited, a blocking call that immediately determines the next action, or foundational project documents.

## Task contract

Give each subagent one bounded, self-contained question. Include:

1. exact search or reading scope;
2. the question to answer;
3. evidence required;
4. desired output format;
5. excluded work, especially writes.

Default to minimal context (`fork_turns="none"` when supported). Supply only facts the subtask cannot recover safely. Prefer one round per agent and avoid overlapping assignments. Start with at most two workers; add another only for a distinct, independently useful surface. Do not fill the platform concurrency limit by default.

Request a compact response, normally no more than 1–2k tokens unless the required evidence cannot fit:

```text
Conclusion:
<one concise conclusion>

Evidence:
- path:line — Symbol — why it matters

Uncertainty / unchecked scope:
<only if applicable>
```

## Execution and verification

- Run independent tasks concurrently, within the platform's concurrency limit.
- Do not duplicate a subagent's active search in the main agent.
- Continue unrelated main-agent work while agents run.
- Wait before edits or decisions that depend on their results.
- Validate by checking cited locations and symbols, not by repeating the full exploration.
- If results conflict, inspect the disputed evidence directly; escalate the judgment when risk warrants it.

Treat an agent running for roughly ten minutes without useful progress as abnormal. Use any valid partial evidence, stop the stalled work, then narrow, split, or handle the remainder directly. Never wait indefinitely.

Subagents default to read-only exploration. Keep code or file modification, destructive actions, production changes, permission changes, database writes, final decisions, and final acceptance in the main agent unless the user or governing instructions explicitly assign otherwise.

## Evaluate the routing

Do not infer an optimization from agent count alone. For repeated workflows, compare representative routed and single-agent runs using total tokens or credits, elapsed time, retries or rework, and missed issues found during verification. If delegation repeatedly increases cost or latency without improving quality, narrow the dispatch threshold, reduce concurrency, or use a cheaper worker for more tightly bounded tasks.
