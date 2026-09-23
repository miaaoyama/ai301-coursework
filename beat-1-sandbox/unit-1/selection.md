# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/71

[The individual Path Review issue page. A link to the repository or the issue list
does not satisfy this field.]

**Verdict output**

Repo is in scope (codepath/pathreview-ai301-fa26-s1). Graded live against the rubric; capture date 2026-09-22.
Repo is in scope (codepath/pathreview-ai301-fa26-s1). Graded live against the rubric; capture date 2026-09-22.
**The verdict must record `accept` for this issue.** Choose an issue your own skill
accepts. If your skill rejects every candidate you try, that is a signal about your
rubric rather than about the issues: revise it and re-run — retries are unlimited and a
partial re-run costs about $0.20 — or run the skill on different candidates. Output
recording `reject` for the issue you chose earns no credit for this field.

```
Repo is in scope (codepath/pathreview-ai301-fa26-s1). Graded live against the rubric; capture date 2026-09-22.
  "verdict": "accept"
}
```

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

[The agreement score of each run you did, in order. A single run is a complete answer if
only one run occurred. **The last score in your list must match the agreement line in the
`eval-run.txt` you committed** — that file is the record of your final run.]
Full run: agreement: 16/20 scored items (bar: 18/20: below the bar)

Targeted run on issue-01, issue-04, issue-15, and issue-19: agreement: 2/4 scored items

Targeted run on issue-01 and issue-19: agreement: 1/2 scored items

Full run: agreement: 18/20 scored items (bar: 18/20: PASS)

Full run: agreement: 18/20 scored items (bar: 18/20: PASS)

Final saved full run: agreement: 17/20 scored items (bar: 18/20: below the bar)

**Issue analysis**

issue-15: My initial rubric returned accept, while the gold label was reject. When I reviewed the issue, I saw that it had a long history of abandoned attempts and closed unmerged PRs. My original scope check treated closed PRs as abandoned rather than as evidence that an issue could be more difficult than it first appeared. I changed the scope check so that at least two abandoned implementation attempts or closed unmerged PRs indicate recurring difficulty. After that change, my targeted run returned reject for issue-15, matching the gold label.

[One scored issue, identified by id (`issue-01` through `issue-20`; the `calib-`
issues are not scored). State your rubric's decision, the gold label, and the
reasoning that produced your rubric's result.]

**Check rationale**

"Newcomer-sized scope | Issue body and Comments, including maintainer statements about implementation scope, issue labels, opener association, linked/mentioned PR history, and prior contribution attempts. | Pass when the issue requests one bounded outcome. Count scope by independent outcomes, not by the number of files, listed steps, suggested implementation approaches, or apparent technical complexity. Multiple related edits that all produce the same outcome still count as one bounded contribution. Multiple possible causes or suggested fixes for one reported bug also remain one bounded outcome unless the issue explicitly requires them as independent deliverables. A terse issue may pass, especially when opened by a maintainer/collaborator or labeled good-first-issue. Fail when the issue is explicitly an umbrella/tracking issue containing separate independent work items, is a pure usage/support question, has unresolved design debate with no maintainer-set direction, a maintainer states that it requires changes to core internals, or its history shows at least two abandoned implementation attempts or closed unmerged PRs indicating recurring difficulty. | required"

I changed this check because my first version was too likely to treat the number of files, steps, or technical complexity as evidence that an issue was too large. The revised version focuses on whether there is one bounded outcome. I also added prior abandoned attempts as evidence because issue-15 showed that an issue can appear bounded while its history indicates recurring difficulty.
[One check from the `rubric.md` uploaded to `tools/issue-select/`, quoted as it is
currently written, with the reasoning behind its current form.]

**Trade-offs**

The trade-off is that this check can still disagree on borderline scope cases. For example, issue-19 changed between accept and reject across runs even after I clarified that technical complexity alone should not cause a failure. The final saved run rejected issue-19 while its gold label was accept. I accepted that trade-off rather than continuing to loosen the scope rule and potentially allowing genuinely difficult or repeatedly abandoned issues through.

[What the quoted check gives up. Any one of these is a complete answer: an issue whose
result it changes, a canary you re-ran with `--only`, a case you accept it will miss, or a
stated reason nothing changed elsewhere. "Nothing changed, and here is how I know" earns
the point in full when the reason follows.]

---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**

[Answer all three:

1. The issue's fit to your interests and to the time available.
2. What the verdict identified correctly, and what you weighed that the rubric could
   not.

1. Issue #71 fits the time I have because the work is specific and bounded. It focuses on fixing the indentation in a test fixture and removing the related xfail marker, and the issue estimates the work at 1–2 hours. I also like that it involves debugging and tests rather than a large open-ended feature.

2. The verdict correctly identified that the issue has one bounded outcome, no assignee or linked PR, recent maintainer activity, and no contribution-policy restriction that would prevent me from working on it. What I weighed beyond the accept verdict was the tier-2 label. The rubric accepted the issue based on its required checks, but I still considered whether I was comfortable taking an intermediate issue without a good-first-issue label. The specific files, expected change, and estimated effort made me comfortable choosing it.

3. I expect the main difficulty in claiming it to be availability. The issue is currently unclaimed, but another student could choose it before I complete the Unit 2 claiming process. I will also need to follow the course's claiming instructions rather than assuming that selecting it in Unit 1 reserves it for me.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
