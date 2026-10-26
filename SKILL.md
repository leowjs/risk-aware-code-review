---
name: risk-aware-code-review
description: Review code changes with executable evidence, verified findings, risk-based depth, and bounded repair rounds. Use for a diff, pull request, or pre-PR quality check, including Python and data pipelines.
---

# Risk-aware Code Review

Produce an actionable review of the requested change. Adapt the Claude Code team's published practices to the actual repository; their internal merge policy and reported results are not defaults for this user.

## Establish the review target

Read applicable AGENTS.md, relevant owner guidance such as REVIEW.md, the requested diff, and affected callers. Establish the base and head revision, intended behavior, and what failure would look like. For uncommitted changes, identify the worktree state. Do not silently widen a PR review into a whole-repository audit.

Choose depth from consequences and reversibility. Inspect permissions, secrets, billing, destructive writes, CI/release logic, and shared contracts more deeply when the change touches them. A docs correction usually needs a source check; a behavioral change may need a regression example and execution. Follow existing owner and approval requirements; never infer permission to weaken them.

## Gather evidence

Choose the smallest checks that can demonstrate the requested behavior and expose plausible regressions. Use existing project commands and inspect their results. Tests, type checks, builds, representative input/output, and visual comparisons serve different purposes; run those relevant to this change. Add a regression test when it materially proves a bug or guards meaningful behavior, rather than mechanically adding tests to every edit.

For data transformations, consider schema and grain, joins and duplicate keys, nulls, row counts, and reconciliation only as relevant. Use a fixture, dry run, or read-only sample before commands that modify remote data. Report when the real service or representative input was unavailable.

A model review reads and reasons about code; it does not establish that a program ran. Record commands, outcomes, revision, and checks that could not run. Do not turn an unexecuted command into a passing result.

## Verify findings

Try to disprove each suspected issue using the surrounding implementation, caller contracts, and existing checks. Report actionable defects with severity, file/line, triggering conditions, expected versus actual behavior, impact, and supporting evidence. Separate introduced regressions from relevant pre-existing issues. Keep uncertain concerns explicitly uncertain and keep cosmetic preferences out of defect counts.

A focused second pass can challenge the first analysis. Use an independent agent only when delegation is authorized in the current environment; otherwise perform the check directly and describe that limitation. Multiple model votes do not prove correctness.

For a review-only request, report findings without modifying the code. When fixes are authorized, fix the cause, verify affected behavior, then inspect the resulting diff for regressions. Look for other instances of the same defect within scope. Track each finding as fixed, rejected with evidence, or unresolved; do not re-report resolved findings without new evidence. After three substantive repair/review rounds without convergence, stop that loop, reassess the approach and explain the unresolved issue. Re-review changed behavior and affected interactions; repeat broader checks only when new evidence justifies it.

## Deliver the review

Lead with the count and severity of verified issues, or say no actionable issues were found within the reviewed scope. Include checks and actual results, material gaps, remaining risk, and a practical rollback option when relevant. An empty findings list is not proof of safety.

Do not post comments, approve, merge, deploy, change repository protections, or upload code to a review service merely because this skill was invoked. Those actions require authorization from the task. Preserve required human decisions and re-evaluate evidence when the reviewed revision changes.

## Improve a recurring review process

When the task includes improving a reviewer, use confirmed historical regressions plus known-good examples to evaluate missed defects and harmful false alarms. Compare reviewer changes on the same cases. Measure review effort together with repair effort, review rounds, reverts and incidents; more comments alone is not improvement. Move repeated, demonstrated failure patterns into a targeted check or concise owner guidance when that edit is authorized.

For release-process work, inspect the existing integration checks, rollout controls, detection signals and rollback procedure. Do not assume that a flag reverses a data migration. Keep a named human accountable and preserve repository-specific approval rules. When understanding is missing, explain the affected module from current code before asking someone to judge it.

Read [references/source-check.md](references/source-check.md) for provenance and claim limits, and [references/original-article.md](references/original-article.md) for the original reading link and the adaptation map. Recheck current product documentation before recommending vendor-specific setup.
