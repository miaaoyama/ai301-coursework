---
name: pr-precheck
description: Grade a PR package (a candidate pull request read against the plan it claims to implement and the issue that plan belongs to) and decide whether it is ready to submit. Use when checking your own branch, draft PR title, and description before opening the pull request, or when grading an eval package bundle.
---

# pr-precheck: rubric-driven PR grading

## The question

You are grading one PR package to answer a single question: is this
ready to submit? A PR package includes the candidate PR title and
description, commits, diff, and test evidence, read against the plan it
claims to implement and the issue that plan belongs to. Do not answer
from gut feel. Grade the package by executing `procedure.md`, applying
the checks and verdict rule in `rubric.md`, and gathering evidence as
defined in `references/evidence-guide.md`.

## Inputs and modes

One of:

- **Live mode**: grade the student's own submission before the pull
  request is opened. Read the issue, the student's `plan.md` including
  any recorded deviation notes, the complete branch diff relative to
  the repository's default branch, the draft PR title and description,
  and the test evidence. From the working copy, use
  `git diff main...HEAD` to read everything the branch changes relative
  to `main`. Gather issue-side evidence from the real repository,
  including the issue thread, PR template, and stated contribution or
  disclosure policies. A house-chain student uses the house plan and
  house repro pack instead; apply the same checks to that evidence.

- **Eval mode**: grade one provided package bundle. The bundle is the
  whole world. Use only evidence contained in the bundle and do not
  fetch or read anything outside it. Run every rubric check and apply
  the complete verdict rule.

## The scope seam (live mode only)

In live mode, read `scope.md` before gathering any other evidence. Use
it to determine the repository where the student's PR is allowed to
live and any house rules that apply there. Refuse to grade work outside
the scoped repository. If the repository line in `scope.md` still
contains an unfilled placeholder, stop without grading and tell the
student to get the cohort's scope file from the instructor. Never guess
the scope.

In eval mode, ignore `scope.md` entirely.

## The voice seam (live mode only)

In live mode, read `voice-guide.md` and check the draft PR title and
description against the student's writing rules. Report any broken
voice rule in the readable summary and identify the rule that was
broken.

The voice guide does not change the final verdict on its own unless a
check in `rubric.md` explicitly reads it.

In eval mode, ignore `voice-guide.md` entirely.

## Component reads

Read `rubric.md` for the checks, their pass conditions, their weights,
and the rule that combines check grades into the final verdict.

Read `references/evidence-guide.md` to determine where each evidence
family lives in the PR package and what evidence can support each
check.

Execute `procedure.md` exactly as written. It determines the read
order, how evidence is gathered, how the rubric checks are applied,
and how the verdict is assembled. If the procedure is silent about a
necessary step, report the gap rather than inventing a step.

If `rubric.md` contains no completed checks or `procedure.md` contains
no completed steps, stop and refuse to grade. The tool requires both a
rubric and a procedure.

## Verdict and output

The verdict space is binary: `accept` means the PR is ready to submit
and `reject` means hold the PR. There is no third verdict.

A short readable summary may appear before the machine-readable output.
End every completed grading run with the following fenced JSON block.
It must be valid, it must be the final fenced JSON block, and nothing
may appear after it.

```json
{
  "item": "<PR URL or bundle id>",
  "checks": [
    {"name": "<check name>", "grade": "pass|fail|unclear",
     "evidence": "<one line: the fact or quote that decided it>"}
  ],
  "verdict": "accept|reject"
}
```

## Grading discipline

- Evidence first. Never grade a check without identifying the fact or
  quote that decided it. "Looks fine" is not evidence.
- Grade the PR itself, not how polished or confident it sounds. Compare
  the actual diff, description, evidence, plan, and issue.
- Let the rubric decide. If the evidence satisfies a check's written
  pass condition, grade it according to that condition even if the
  result feels wrong. Fix the rubric rather than changing a grade by
  instinct.
- Let the procedure decide how the grading is performed. Follow
  `procedure.md` exactly and report gaps instead of silently creating
  new steps.
- Treat `unclear` according to the verdict rule in `rubric.md`. If the
  verdict rule does not specify how to handle it, treat `unclear` as a
  failure because an unverifiable claim is not ready to submit.
