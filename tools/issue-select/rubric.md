# Rubric: is this a good first issue?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| maintainer-alive | repo-facts block: maintainer response sample (comment dates) and merged-PR dates | a maintainer comment, response, or merge dated within the 30 days before the capture date | required |
| repo-in-use | repo-facts block: default-branch commit dates and merged-PR dates | at least one commit or merged PR in the last 30 days | required |
| newcomer-scoped | issue body | the issue is bounded: one concrete task with named touch points — a bug with repro steps or expected-vs-actual behavior, a small feature, or a docs task with a stated home and scope (pages to create or update are named). A maintainer-filed issue with a concrete item list, or a maintainer diagnosis with named causes, counts as bounded — a trailing "etc." on an otherwise concrete list does not break boundedness. No open design decisions; explicitly optional "consider" items are fine | required |
| unclaimed | comment thread; repo-facts block: assignee and linked-PR state | no assignee, no linked open PR, and no claim comments in the thread; stale claims (no linked open PR and no follow-up activity) do not block, and a maintainer invitation for new takers overrides old claims | required |


## Verdict rule

Accept if all four required checks pass. Reject if any required check fails or is unclear. Unclear counts as fail: a first issue you cannot verify is not a first issue you should take.

