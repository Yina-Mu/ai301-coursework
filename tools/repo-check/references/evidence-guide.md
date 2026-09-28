# Evidence guide: where proof lives in a reproduction package

## Environment

- **Where it lives:** the repro report's environment record (a dedicated block or section, usually near the top of the report); the issue context for the version the bug was reported against. In live mode: the draft's environment section, plus the repo's own docs (README / setup guide) for the canonical version.
- **What good looks like:** the record names the exact project version (release version, commit, or tag) and the OS — each specific enough that someone else could rebuild the same setup. "Latest", or either of the two missing, is not sufficient. Language and toolchain versions are expected when the reproduction builds from source or the behavior could depend on them. If the environment differs from what the issue targets, the difference is called out explicitly.


## Steps

- **Where it lives:** the repro report's steps section. The starting state is the state before step one (fresh clone, clean checkout). In live mode: the draft report's steps.
- **What good looks like:** the steps run in order from the stated starting state to the observed behavior with no missing command and no unexplained jump — a stranger could follow them and land on the same output. Each step shows both the trigger (what you do) and the observation point (what you look at).

## Behavior shown

- **Where it lives:** the package's artifacts — output excerpts, terminal logs, screenshots — read against the issue's description of the failure (the issue context, or the issue thread in live mode).
- **What good looks like:** the artifact shows the same failure the issue reports: the same error type and message, produced by the same trigger. An excerpt showing a different error does not count, and prose describing the behavior with no artifact behind it does not count. At least one concrete, legible artifact is present.

## Honesty

- **Where it lives:** the report's stated conclusion (reproduced / could not reproduce / partially reproduced) read against the artifacts in Behavior shown.
- **What good looks like:** the conclusion says exactly what the artifact shows — no more. A cannot-reproduce backed by a complete environment record, full steps, and the actual output is honest and passes. A "reproduced" claim whose artifact shows a different behavior, or any conclusion with no artifact behind it, fails.

## Comms

- **Where it lives:** the claim comment read against the issue (does it name this issue's specifics?); the claim and repro comments read against the repo's stated templates and contribution policy, including AI-use disclosure requirements. In live mode: the repo's CONTRIBUTING / docs and the issue thread. In eval: the repo-facts block.
- **What good looks like:** the comment is specific to this issue — names the version, the behavior, and what will be / was done — rather than boilerplate that could fit any issue. Where the repo's policy requires disclosing AI assistance, the disclosure is present and explicit. Promises stay within investigation: no promised fix, no promised date.
- **Course rule for AI disclosure (mechanical test):** treat the package's comments as AI-assisted work. First read the repo-facts contribution policy: only a stated requirement that AI usage *be disclosed* (e.g. ghostty's AI_POLICY.md: "All AI usage in any form must be disclosed, stating the tool used and the extent of the assistance") triggers the disclosure check. An AI policy about something else — e.g. ripgrep's "comments to maintainers must be written by humans in their own words" — is an authorship rule, not a disclosure requirement: a missing disclosure is not a fail there. Where a disclosure requirement is stated, the comments must contain an explicit disclosure naming the tool used and the extent of assistance; its absence fails `conventions-respected`.
