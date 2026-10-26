# Original reading and adaptation map

Primary reading: [How the Claude Code team does code review](https://claude.dev/blog/solving-code-review-at-anthropic/).

Authors: Addy Osmani, Morgan Westlee Lunt and Qing Wang. Published 15 October 2026; fetched and compared with the selected X rewrite on 26 October 2026. The page estimates 14 minutes of reading time. The rewrite follows the same core process and claims; it is not independent corroboration. The publisher's link is the full reading; this file contains implementation notes rather than a reproduction.

Use these prompts when adapting the article to a repository:

- What executable evidence establishes the changed behavior?
- Which suspected findings survive inspection of actual callers and contracts?
- What existing policy governs this revision and its risks?
- How will fixes converge without resurfacing rejected comments?
- What integration, detection and recovery controls actually exist?
- Which confirmed failures and clean cases can evaluate a reviewer change?
- Who owns the result, and what explanation would help them assess it?

The main skill now covers these questions. Workflow improvements are conditional on the task; an ordinary diff review does not authorize creating CI infrastructure, changing approval policy or running production experiments. Report unavailable controls as limitations rather than implying they were installed.

Read source-check.md before citing performance figures or equating Anthropic's internal workflow with its public product.
