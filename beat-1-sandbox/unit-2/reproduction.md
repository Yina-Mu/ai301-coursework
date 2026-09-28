# Unit 2 — Claim and Reproduce

Path: `beat-1-sandbox/unit-2/reproduction.md`

Record of your claim and reproduction on the issue you chose in Unit 1, and of the
evaluation runs that produced `eval-run.txt`. This file is graded at the path above; a copy
kept anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your identity upstream

**GitHub username**

Yina-Mu

---

## Posted upstream

**Claim comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/69#issuecomment-5753636262

I'd like to work on this issue for my coursework.

**Reproduction comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/69#issuecomment-5864067126

Reproduction report for #69.

Environment: fork Yina-Mu/pathreview-ai301-fa26-s3 @ 2f4e82f (main), Python 3.13.9, pytest 9.1.1, macOS 14.6.1 (darwin).

Steps:
$ git clone https://github.com/Yina-Mu/pathreview-ai301-fa26-s3.git && cd pathreview-ai301-fa26-s3
$ make setup # installs .venv + deps; the Postgres migrate/seed step needs a local Postgres server, skipped — not needed for this unit test
$ .venv/bin/python -m pytest tests/unit/test_output_parser.py -k test_json_array_fallback -v
$ .venv/bin/python -m pytest tests/unit/test_output_parser.py -k test_json_array_fallback -v --runxfail

Expected: the parser handles a top-level JSON array gracefully (test passes).

Actual: the first run reports XFAIL — the test is marked xfail for issue #69 (manifest H-02) ("18 deselected, 1 xfailed in 0.69s"). The --runxfail run fails with:
E AttributeError: 'list' object has no attribute 'items'
rag/generator/output_parser.py:68: AttributeError
in \_parse_json_output, at `for key, value in data.items()` — data is the parsed list ['First feedback item', 'Second feedback item']. Matches the issue exactly.

Next: leaving the fix for Unit 3; keeping this thread to the reproduction.

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

agreement: 18/20 scored items (bar: 18/20: PASS)
(categories: clear-accept 6/8, disclosure 1/1, no-evidence 4/4, unfollowable-comms 3/3, wrong-target 4/4)

Earlier calibration runs were done while revising the rubric, but their scores were not recorded. The eval-run.txt committed in this directory is the record of the final run above.

**Package analysis**

pkg-10 (source: starship/starship#7648, "Prompt disappears when path is a symlink to a subdirectory inside a Git repository"). My rubric decided reject; the gold label said accept. The failing check was behavior-matches.

The candidate's repro report states its result up front: "Result: cannot reproduce on Linux + zsh with the report's exact layout and config." With the report's exact symlink layout and starship config (starship 1.26.0, matching the report's version), the directory module rendered on every attempt — the prompt showed `monorepo/packages/app-dir on  master` and `starship explain` listed the module instead of omitting it. The report documents exactly what differed from the issue's environment (Linux vs macOS, zsh vs fish 4.7.1) and offers a mechanism, concluding "a fish shell resolving `PWD` logically looks necessary to hit the `contract_repo_path` failure; I did not have one available for this attempt."

My rubric's behavior-matches reads: "Pass if the observed failure is the same failure the issue reports: same error type and message, same trigger. A different error fails even if the run 'failed'." The package observed no failure at all — the prompt rendered. "The same failure the issue reports" cannot be satisfied when there is no observed failure, so the check fails and the verdict is reject. The gold label accepts the package as an evidenced, honest cannot-reproduce — the kind my outcome-honest check explicitly allows ("An evidenced cannot-reproduce passes"). My rubric still rejects it because behavior-matches has no cannot-reproduce carve-out: as written, it only knows how to grade packages that show a failure, and it holds everything else, including honest cannot-reproduces. The disagreement was consistent across runs. (pkg-09, the other behavior-matches disagreement, agreed with gold in an earlier run, which reads as evaluator variation rather than a rubric defect — so pkg-10 is the stable signal.)

**Check rationale**

| artifact-attached | The package's artifacts (terminal output, logs, screenshots) | Pass if at least one concrete artifact shows the observed behavior or its direct verifiable consequences (e.g. an empty stash list proving nothing was stashed). Prose alone, with no artifact at all, fails. | required |

This check reads this way because of calib-01 (lazygit#5883, the stash-name prompt that silently does nothing on untracked-only selections). The candidate's decisive artifact was an empty `git stash list` — literally no output. A narrower wording, requiring the artifact to show the observed behavior itself, would have failed that package: empty output shows nothing, yet the package's entire point was that nothing happened. I revised the check to accept "the observed behavior or its direct verifiable consequences," with the empty stash list as the named example — the empty list is verifiable precisely because a completed stash would have made it non-empty. What I rejected was the narrower version: it would have punished negative evidence, which is the only kind of artifact a silent-failure or cannot-reproduce package can offer.

**Trade-offs**

behavior-matches gives up honest cannot-reproduce packages, and I accept the miss. pkg-10 is the receipt: an evidenced cannot-reproduce that names its environmental differences and a plausible mechanism, held by my rubric while the gold label accepts it. The check demands "the same failure the issue reports," which a cannot-reproduce can never supply. The alternative — a cannot-reproduce carve-out inside behavior-matches — would force the grader to judge whether the reporter "really tried," the exact kind of judgment call that produced whack-a-mole during calibration, where each loosening fixed one package and flipped another. For the same reason I froze the rubric at 18/20 instead of chasing 20/20: pkg-09 agreed with gold in an earlier run and flipped back, which reads as evaluator variation, not a defect the rubric should contort itself to fix.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/repro-check/`.
