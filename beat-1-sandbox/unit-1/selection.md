# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/69

**Verdict output**
┌──────────────────┬───────────────────────────────────────────────────────────────────────────┬──────────────────────────────────────────────────────────────────────────────────────────────────────────────┐
│ Check            │ #69                                                                       │ #68                                                                                                          │
├──────────────────┼───────────────────────────────────────────────────────────────────────────┼──────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│ maintainer-alive │ pass — Aburke225 [COLLABORATOR] commented 2026-09-16                      │ pass — same                                                                                                  │
├──────────────────┼───────────────────────────────────────────────────────────────────────────┼──────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│ repo-in-use      │ pass — commits to main on 2026-09-16                                      │ pass — same                                                                                                  │
├──────────────────┼───────────────────────────────────────────────────────────────────────────┼──────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│ newcomer-scoped  │ pass — one bug, expected-vs-actual, two named files, xfail H-02 to remove │ pass — one bug, expected-vs-actual, two named files, xfail H-01 to remove                                    │
├──────────────────┼───────────────────────────────────────────────────────────────────────────┼──────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│ unclaimed        │ pass — no assignee, no linked PR, no comments                             │ pass — no assignee, no linked PR; one classmate claim comment, non-blocking under the Path Review house rule │
└──────────────────┴───────────────────────────────────────────────────────────────────────────┴──────────────────────────────────────────────────────────────────────────────────────────────────────────────┘

One tension worth naming: #68's only difference from #69 is a classmate's claim from 2026-09-19. Outside this classroom that would sink the check; the scope's house rule says to ignore student claim comments, so it passes as written. If you take #68, claim it anyway.

```json
[
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/69",
    "checks": [
      {"name": "maintainer-alive", "grade": "pass", "evidence": "Aburke225 [COLLABORATOR] commented 2026-09-16, within 30 days of the 2026-09-20 capture date"},
      {"name": "repo-in-use", "grade": "pass", "evidence": "Three commits to default branch main on 2026-09-16, e.g. 'chore: track five more manifest entries against the tracker'"},
      {"name": "newcomer-scoped", "grade": "pass", "evidence": "One bug with expected-vs-actual ('calls .items() on the parsed value and raises AttributeError'), two named files, and xfail H-02 to remove"},
      {"name": "unclaimed", "grade": "pass", "evidence": "assignees: [], no linked or cross-referenced PRs in the timeline, comment thread empty"}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/68",
    "checks": [
      {"name": "maintainer-alive", "grade": "pass", "evidence": "Aburke225 [COLLABORATOR] commented 2026-09-16, within 30 days of the 2026-09-20 capture date"},
      {"name": "repo-in-use", "grade": "pass", "evidence": "Three commits to default branch main on 2026-09-16, e.g. 'chore: track five more manifest entries against the tracker'"},
      {"name": "newcomer-scoped", "grade": "pass", "evidence": "One bug with expected-vs-actual ('index([]) raises ZeroDivisionError ... index() shouldn't raise on an empty corpus'), two named files, and xfail H-01 to remove"},
      {"name": "unclaimed", "grade": "pass", "evidence": "assignees: [], no linked PRs; sole claim comment is from classmate acordero4852 [NONE] on 2026-09-19, non-blocking under the Path Review house rule"}
    ],
    "verdict": "accept"
  }
]
```

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

Agreement scores in run order, quoted verbatim from each run's output:

1. Smoke test (`--limit 3`): `agreement: 2/3 scored items`
2. Full run: `agreement: 13/20 scored items  (bar: 18/20: below the bar)`
3. Targeted rerun (`--only issue-04,issue-06,issue-09,issue-14,issue-16,issue-19`): `agreement: 5/6 scored items`
4. Full run: `agreement: 18/20 scored items  (bar: 18/20: below the bar; category floor unmet: no match in policy)`
5. Final run (`--save-run eval-run.txt`): `agreement: 19/20 scored items  (bar: 18/20: PASS)`


**Issue analysis**

I picked issue-04 — the one disagreement that survived the targeted rerun (5/6) and motivated the rubric fix that took the full run from 13/20 to 18/20.

- Gold label: `accept`. From its eval bundle: `gold-label: {"id": "issue-04", "source": "zxcalc/zxlive#555", "category": "clear-accept", "calibration": false, "verdict": "accept", "note": "small active repo, maintainer-filed bounded bug, unclaimed"}`. Final run table row: `issue-04  accept  accept   yes`.
- The issue, quoted from its eval bundle:

> ### Missing several basic rule previews (#555)
>
> opened by RazinShaikh (COLLABORATOR) on 2026-08-04, state open, labels: Type: bug, good first issue, Category: Proof mode, Priority: Medium
>
> Including remove identity, fuse spiders, remove self loops, etc.

- The rubric check that decides it, quoted verbatim from the current rubric.md:

> the issue is bounded: one concrete task with named touch points — a bug with repro steps or expected-vs-actual behavior, a small feature, or a docs task with a stated home and scope (pages to create or update are named). A maintainer-filed issue with a concrete item list, or a maintainer diagnosis with named causes, counts as bounded — a trailing "etc." on an otherwise concrete list does not break boundedness. No open design decisions; explicitly optional "consider" items are fine

- My reasoning: the issue is maintainer-filed (RazinShaikh, COLLABORATOR) with a concrete item list — three named rule previews: remove identity, fuse spiders, remove self loops — so a newcomer can see exactly what "done" looks like. The trailing "etc." adds no new unknown work; it only hedges minor follow-ups of the same kind. Before the fix, the rubric read any "etc." as unbounded scope and rejected the issue. That was the wrong call: boundedness should be judged on whether the listed items are concrete, not on a trailing hedge word. Stating the exception explicitly flipped issue-04 to accept, matching gold.


**Check rationale**

I quote the newcomer-scoped check, verbatim from the current rubric.md:

> the issue is bounded: one concrete task with named touch points — a bug with repro steps or expected-vs-actual behavior, a small feature, or a docs task with a stated home and scope (pages to create or update are named). A maintainer-filed issue with a concrete item list, or a maintainer diagnosis with named causes, counts as bounded — a trailing "etc." on an otherwise concrete list does not break boundedness. No open design decisions; explicitly optional "consider" items are fine

Why it has this form:

- The core test is "named touch points," not task size. A newcomer can't judge scope from vibes; they need to see exactly what "done" looks like — a file to change, a behavior to reproduce, pages to write. Naming the touch points makes the scope checkable before any work starts.
- The maintainer-filed clause exists because a maintainer's item list is itself a scoping act. If the person who owns the repo names the items, the newcomer isn't guessing at boundaries — they're executing a list someone authoritative already drew.
- The trailing-"etc." exception was added during calibration (issue-04). The first rubric draft treated any "etc." as unbounded scope and rejected a maintainer-filed issue with three concrete items — a gold-`accept` the skill got wrong. The exception keeps the check's intent (concrete list = bounded) while tolerating the hedging word people naturally append to lists. That single fix moved the full run from 13/20 to 18/20.
- "No open design decisions" draws the line the check is really about: a newcomer can implement, but shouldn't have to invent the solution's shape. Explicitly optional "consider" items are fine because they don't expand what "done" requires.


**Trade-offs**

Every exception in the newcomer-scoped check buys fewer false rejects at the price of occasional false accepts:

- The trailing-"etc." exception can hide a long tail. "Fix login, fix logout, etc." looks concrete, but the "etc." may conceal five more items nobody named. The check now bets that a concrete-looking list means a bounded task — usually true, wrong sometimes. Calibration chose this direction deliberately: for a first-issue picker, wrongly rejecting a good issue (a newcomer loses a chance) is worse than wrongly accepting a slightly loose one (the newcomer can still ask or walk away).
- "Maintainer-filed counts as bounded" trusts authority over evidence. Maintainers can file vague issues too, and the check gives their lists a presumption of good scoping. That presumption is right most of the time — the maintainer knows the codebase — but it's a shortcut around actually verifying each item is concrete.
- The check judges the issue text, not the real work. An issue can read bounded and hide deep complexity (the two named files turn out to need a refactor), or read vague and be trivial. The check is a triage heuristic over prose, not a guarantee about the work — it can only lower the odds of a tar pit, never eliminate them.
- "No open design decisions" categorically excludes issues with any design component, even small ones a mentored newcomer could handle well. The check optimizes for "never send a newcomer into a swamp" over "surface every doable issue" — coverage is the price of safety.


---

**Selection rationale**

- **Fit to my interests and time:** I'm an MSCS student and I work as a full-stack developer, with Python as my primary language. I'm taking this AI course to level up my agent and LLM-app skills, so a bug in a RAG output parser is directly on track — it's exactly the kind of LLM-app plumbing I want to get good at. The issue estimates 2–4 hours, which fits my week, and the scope is one crash with two named files, so it won't eat my weekend.
- **What the verdict got right, and what I weighed beyond the rubric:** The verdict got the important things right — the maintainer is active, the repo is alive, the scope is bounded and newcomer-sized, and nobody has claimed it. Beyond the rubric, the tie-breaker between #68 and #69 was the comment thread: #68 already had a classmate's claim comment (non-blocking under our house rule, but still), while #69's thread was completely empty. An empty thread means a cleaner claim and no chance of stepping on anyone. I also weighed personal fit: #69 is a small Python crash fix, which plays to what I'm good at, over anything needing domain knowledge I'd have to ramp up on.
- **How difficult it will be to claim:** Not difficult at all. No assignee, no linked or cross-referenced PRs, no comments — there's nothing to untangle. Claiming it is just posting a comment saying I'm taking it.


---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
