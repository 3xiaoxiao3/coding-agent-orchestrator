# Code review policy

Read this reference when the user requests a formal review, audit, regression assessment, or merge-readiness judgment.

## Review standard

Prioritize findings that could cause incorrect behavior, security exposure, data loss, outages, or meaningful maintenance risk. Do not inflate the report with style preferences unless they violate an explicit project rule or hide a defect.

For each finding, provide:

- severity and concise title;
- exact file and narrow line range;
- concrete failure mode;
- triggering condition or counterexample;
- why existing tests or guards do not prevent it, when relevant.

Order findings by severity. Keep summaries secondary to findings. If no actionable findings remain, say so and identify material untested or unchecked areas.

## Model and agent use

- Luna may perform exact searches, inventories, bounded extraction, and scan relationships across call sites, tests, configuration, logs, and historical patterns, then return evidence.
- Sol performs ordinary formal review and integrates module-level conclusions.
- Astra handles high-risk, security-critical, architecture-level, or conflicting review judgments.
- The main agent verifies decisive evidence and owns the final review result.

Use independent subagents only when review surfaces are separable, such as implementation, tests, schema, configuration, and security boundaries. Avoid multiple agents reviewing the same diff without a specific independent-validation reason.

## Risk escalation

Escalate review depth for authentication, authorization, payments, refunds, concurrency, locks, transactions, migrations, database writes, data consistency, destructive operations, and deployment-critical behavior. Check failure paths, retries, idempotency, rollback behavior, privilege boundaries, and partial-success states as applicable.

Do not approve solely because tests pass. Confirm that tests exercise the relevant failure mode and that the change preserves caller-visible contracts.
