# Model routing

Read this reference when model choice affects cost, quality, or safety.

Route by the highest applicable risk, then choose reasoning effort within that model.

| Work | Default route | Typical effort |
| --- | --- | --- |
| Exact file lookup, inventory, field extraction, simple classification, bounded fact check | GPT-5.6 Luna | low–medium |
| Multi-file read-only exploration, large-file review, logs, test-failure triage, evidence compression | GPT-5.6 Terra | medium |
| Feature implementation, debugging, test repair, local refactor | GPT-5.6 Sol | medium |
| Complex bug, cross-module analysis, stateful or production-critical implementation | GPT-5.6 Sol | high |
| Ordinary formal code review | GPT-5.6 Sol | medium–high |
| Architecture, security-critical or high-risk review, conflicting analyses, final critical acceptance | GPT-6 Astra | high–xhigh |

Use at least Sol for authentication, authorization, payments, refunds, concurrency, locking, transactions, database writes, data consistency, migrations, or critical production paths. Use Astra when the task is a high-risk review or a system-level judgment in those areas.

Use Luna only when the question and output format are tightly bounded. Prefer Terra when the worker must understand relationships across files, interpret ambiguous logs, or decide which evidence matters. Luna and Terra may locate risks and collect evidence but must not own the final formal review conclusion. Sol normally owns implementation reasoning; Astra owns the hardest judgment calls. Keep the main agent responsible for the integrated result regardless of model.

Do not upgrade merely because a task is long. Broad low-risk reading often belongs on Terra; a tiny but irreversible or security-sensitive decision may require Astra. If the preferred model is unavailable, use the nearest available model capable of the work and preserve the same scope, evidence, and decision-ownership boundaries.
