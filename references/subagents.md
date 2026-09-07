# Subagent orchestration

Read this reference for broad repository exploration, multiple independent questions, or substantial context compression.

## Dispatch threshold

Delegate when at least one benefit clearly exceeds dispatch and verification cost:

- broad cross-file or cross-directory reading;
- large logs, generated output, or search results;
- two or more independent checks that can run concurrently;
- a large input that should collapse into a small evidence set;
- an independent risk check that materially improves confidence.

Keep work in the main agent when it concerns a known small file, a single fact, the exact code about to be edited, a blocking call that immediately determines the next action, or foundational project documents.

## Task contract

Give each subagent one bounded, self-contained question. Include:

1. exact search or reading scope;
2. the question to answer;
3. evidence required;
4. desired output format;
5. excluded work, especially writes.

Default to minimal context (`fork_turns="none"` when supported). Supply only facts the subtask cannot recover safely. Prefer one round per agent and avoid overlapping assignments.

Request a compact response:

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

