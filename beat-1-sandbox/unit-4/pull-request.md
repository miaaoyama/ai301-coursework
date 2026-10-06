# Unit 4 — Test and Submit

Path: `beat-1-sandbox/unit-4/pull-request.md`

Record of the pull request you opened against the Path Review repo, and of the evaluation
runs that produced `eval-run.txt`. This file is graded at the path above; a copy kept
anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your pull request

**Pull request**

https://github.com/codepath/pathreview-ai301-fa26-s1/pull/94

**Branch**

fix/71-heading-fixture

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

I ran two small smoke tests first and got "agreement: 3/3" on both. I then ran a canary across all five categories and got "agreement: 5/5". After those passed, I ran the full evaluation and got "agreement: 18/20 scored items (bar: 18/20: PASS)". The full run is the one saved in eval-run.txt.

**Package analysis**

I looked at pkg-08. My rubric decided reject, while the gold label was accept. The eval result showed "pkg-08  clear-accept  accept  reject  NO  failed: Repository checks".

The package said, "Requirements: cheatsheets regenerated (no binding changes, no diff); code formatted; integration test added; new error text internationalised; no UserConfig changes." It also gave specific test evidence: "Integration test stash_untracked_only_errors passes; go test ./... passes; go generate ./... produces no cheatsheet diff."

My Repository checks rule is strict about having visible evidence that applicable checks were actually run. The package provides observable outcomes for several checks, including the integration test, `go test ./...`, and `go generate ./...`, while other requirements such as `"code formatted"` are stated without a separate observable outcome. Based on my rubric's requirement that applicable checks have visible outcomes, the tool rejected the package under Repository checks. The gold label considered the package ready, showing that my rule was more conservative about repository-check evidence than the gold standard.

**Check rationale**

One of my required checks is:

| **Repository checks** | The test evidence read against the repository's stated test, lint, build, or validation requirements in the repo-facts block and the plan's test plan, using Test evidence in the evidence guide. | Pass if the applicable repository checks were actually run and their outcomes are visible in the evidence. If a stated check cannot be run, pass only when the limitation and its effect on confidence are explicitly disclosed rather than silently omitted. | required |

I wrote it this way because I did not want a PR to pass just because it says something like “tests pass.” I wanted the tool to look for evidence of the checks the repository actually requires and their outcomes. I also added the exception for checks that cannot be run so an honest limitation does not automatically fail a PR, as long as the limitation and its effect are clearly disclosed.

**Trade-offs**

The full run showed the trade-off in making Repository checks strict: "not-tested 4/4" but "clear-accept 5/7". It correctly rejected every not-tested package, but it also rejected pkg-08 and pkg-16, which the gold labels considered clear accepts.

Before the full run, I also ran a canary with --only pkg-01,pkg-02,pkg-03,pkg-04,pkg-12, one package from each category, and got "agreement: 5/5". Because that canary passed every category and the final full run reached "18/20 scored items (bar: 18/20: PASS)", I chose not to loosen Repository checks just to chase 20/20. Relaxing it could reduce false rejects, but it could also allow unsupported testing claims to pass.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/pr-precheck/`.
