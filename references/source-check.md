# Source check and scope

Sources checked 26 October 2026:

- Selected post: https://x.com/addyosmani/status/2114604912520921136
- Original team account: https://claude.dev/blog/solving-code-review-at-anthropic/
- Product capabilities: https://code.claude.com/docs/en/code-review
- Runnable verification: https://code.claude.com/docs/en/best-practices
- Repository enforcement: https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches

The selected X article was retrieved through the FxTwitter mirror after direct X access failed. Its embedded source points to the original Claude developer article. This corroborates provenance; the mirror is not an independent audit of the claims.

Anthropic reports that Claude writes about 90% of Claude Code, merged PR volume more than doubled from June to September, and the proportion reverted fell over 40%. Treat these as internal observations, not independently verified measurements or causal proof. A lower proportion does not necessarily mean fewer absolute reverts. The reported 2,500-to-30,000 daily changes concern Anthropic's monorepo, a separate scope: https://www.anthropic.com/engineering/redesigning-source-control

The claimed two-to-three-fold benefit from verification is an estimate, not a controlled benchmark. More PRs receiving substantive comments does not measure reviewer accuracy. Do not promise these gains for another repository.

Official Code Review documentation says the public service reads code without building or running it, and posts findings without approving or blocking a merge. Anthropic's internal blocking gates and lighter human-approval paths are additional process choices. GitHub can enforce required reviews, status checks, conversation resolution, and stale-approval handling when configured; merely writing these requirements in a skill does not enforce them.

The installed skill is an adaptation: runnable evidence, explicit uncertainty, targeted defect review and bounded repair are practical choices. It does not install Anthropic products, configure CI, implement automated risk classification, create monitoring, or grant automatic merge authority. Its three-round reassessment is a local default, not a proven optimum. Company rules, repository policy and the user's current authorization govern actual execution.
