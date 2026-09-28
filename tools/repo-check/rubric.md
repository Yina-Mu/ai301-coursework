# Rubric: is this reproduction package ready to post?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| env-pinned | The repro report's environment record | Pass if it names the exact project version (release version, commit, or tag) and the OS, each specific enough to rebuild the same setup. Language and toolchain versions are required only when the reproduction builds from source or the behavior could depend on them; for a released binary the exact version is sufficient. Fail if the version or OS is missing or vague (e.g. "latest"). | required |
| steps-replayable | The repro report's steps section | Pass if a stranger following the steps from a fresh clone would reach the same observed behavior, with no missing command and no unexplained jump. | required |
| behavior-matches | The output excerpt or artifact read against the error the issue describes | Pass if the observed failure is the same failure the issue reports: same error type and message, same trigger. A different error fails even if the run "failed". | required |
| outcome-honest | The report's stated conclusion read against its artifact | Pass if the claimed outcome is supported by the artifact. An evidenced cannot-reproduce passes; a confident "reproduced" claim about the wrong behavior fails. | required |
| artifact-attached | The package's artifacts (terminal output, logs, screenshots) | Pass if at least one concrete artifact shows the observed behavior or its direct verifiable consequences (e.g. an empty stash list proving nothing was stashed). Prose alone, with no artifact at all, fails. | required |
| conventions-respected | The words of the claim comment and repro report | Pass if the words respect the repo's stated conventions. AI disclosure (mechanical test): (1) Read the repo-facts contribution policy. Does it state, in so many words, that AI usage must be disclosed — e.g. "must be disclosed, stating the tool used and the extent of the assistance"? An AI policy about something else (e.g. "comments must be written by humans in their own words", "AI-assisted coding is welcome") is NOT a disclosure requirement: stop here, pass. (2) Only if a disclosure requirement is stated, treat the package's comments as AI-assisted work (course rule): the comments must then contain an explicit disclosure naming the tool used and the extent of assistance; a missing disclosure fails. | required |


## Verdict rule

ready if and only if every required check passes. unclear counts as fail. Preferred checks, if any, never change the verdict.