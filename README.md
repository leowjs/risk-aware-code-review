# Risk-aware Code Review

A reusable agent skill for reviewing code with executable evidence, verified findings, proportionate review depth, and bounded repair rounds.

This is an independent adaptation of published engineering practices. It is not an official Anthropic or OpenAI skill, and it does not install a review service or change repository permissions.

## Source and attribution

The primary inspiration is **[How the Claude Code team does code review](https://claude.dev/blog/solving-code-review-at-anthropic/)** by **Addy Osmani, Morgan Westlee Lunt, and Qing Wang**, published **15 October 2026** on the Claude developer blog.

The article was discovered through [Addy Osmani's X rewrite](https://x.com/addyosmani/status/2114604912520921136). The original and rewrite describe the same core process; the rewrite is not independent confirmation of the original's claims.

This repository contains adapted instructions and source notes, rather than a reproduction of the article. Read the publisher's version for the complete account and diagrams. Attribution does not imply endorsement.

Supporting documentation:

- [Claude Code review capabilities](https://code.claude.com/docs/en/code-review)
- [Claude Code verification practices](https://code.claude.com/docs/en/best-practices)
- [GitHub protected-branch controls](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches)

## What the skill does

- Establishes the intended behavior, reviewed revision, affected callers, and relevant repository guidance.
- Chooses runnable checks appropriate to the change, including data reconciliation when relevant.
- Requires concrete triggering conditions, impact, and file/line evidence for actionable findings.
- Distinguishes introduced defects, pre-existing issues, uncertain concerns, and cosmetic preferences.
- Tracks finding outcomes and reassesses after three substantive repair/review rounds without convergence.
- Covers historical-bug and clean-case evaluation when improving a recurring reviewer.
- Preserves human accountability, authorization boundaries, and existing approval policies.

The skill is a set of instructions. It does not itself execute checks, enforce branch protections, configure monitoring, or grant merge authority. A review-only request remains read-only.

## Use it

Clone or download this repository and install the folder in your coding agent's supported skills location. For a local Codex setup using the default skills directory:

```sh
git clone https://github.com/leowjs/risk-aware-code-review.git ~/.codex/skills/risk-aware-code-review
```

If you use a custom skills directory, choose that location instead. Then invoke:

```text
Use $risk-aware-code-review to review this diff.
Report verified findings, checks actually run, and remaining uncertainty.
```

For a data transformation:

```text
Use $risk-aware-code-review to review this Python transformation.
Check join cardinality, null handling, and output reconciliation where relevant.
Use fixtures or read-only samples; report findings without changing production data.
```

## Files

| File | Purpose |
| --- | --- |
| [SKILL.md](SKILL.md) | Reusable review instructions |
| [agents/openai.yaml](agents/openai.yaml) | Codex display metadata and example prompt |
| [references/source-check.md](references/source-check.md) | Provenance, evidence limits, and product distinctions |
| [references/original-article.md](references/original-article.md) | Original article and adaptation questions |

## Evidence limits

Sources were checked on 26 October 2026. The article's figures about AI-written code, PR throughput, and revert proportions are company-reported observations, not independently audited results or promised improvements for another team. More review comments do not establish better accuracy.

The public Claude Code Review service reads code without building or running it, and posts findings without itself approving or blocking a merge. Anthropic's internal approval and blocking arrangements are additional process choices. Check current vendor documentation before configuring a service.

The three-round reassessment threshold is an adopted workflow default, not a universal optimum. No findings does not prove that code is safe.

## License

The original material in this repository is available under the [MIT License](LICENSE). Linked articles, documentation, trademarks, and other third-party material remain subject to their respective owners' rights; this repository's license does not relicense them.
