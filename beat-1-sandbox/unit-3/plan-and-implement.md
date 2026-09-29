# Unit 3 — Plan and Build

Path: `beat-1-sandbox/unit-3/plan-and-implement.md`

Record of your plan, the branch you built it on, and the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in the
repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Posted upstream

**GitHub username**

miaaoyama

**Plan comment**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/71#issuecomment-5898530931

I reproduced the failing-test condition for #71 and confirmed that the indented Markdown fixture produces no extracted headings.

My plan is to update the fixture in `tests/unit/test_readme_parser.py` so the `#`, `##`, and `###` lines are interpreted as headings, then remove the issue #71 `@pytest.mark.xfail` marker. I do not plan to change `_extract_heading_hierarchy()` because the reproduction points to the fixture rather than the parser behavior.

I’ll re-run the issue-specific test from my reproduction and verify that it changes from XFAIL to PASS with the expected heading hierarchy, then run the full `tests/unit/test_readme_parser.py` test file to check for regressions.

---

## Your branch

**Branch**

fix/71-heading-fixture

**Evidence**

### Before

Command:

`.venv/bin/python -m pytest tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy -v -rx`

Output:

```text
tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy XFAIL [100%]

XFAIL tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy - issue #71 (manifest H-04): heading hierarchy fixture is indented, so it has no headings

1 xfailed in 0.10s
```

Direct reproduction using the same indented fixture:

```text
Extracted headings: []
Heading count: 0
```

### After

Command:

`.venv/bin/python -m pytest tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy -v -rx`

Output:

```text
tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy PASSED [100%]

1 passed in 0.28s
```

Full relevant test file:

`.venv/bin/python -m pytest tests/unit/test_readme_parser.py -v`

Output summary:

```text
14 passed, 1 xfailed in 0.11s
```

The remaining xfail was `test_parse_standard_readme`; `test_extract_heading_hierarchy` passed after the issue #71 change.


## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

1. Smoke run (`--limit 3`): 3/3 scored packages agreed with the gold labels.
2. First full diagnostic run: 19/20 scored packages agreed with the gold labels. `pkg-14` was the only disagreement.
3. Second full diagnostic run saved to `results.json`: 19/20 scored packages agreed with the gold labels. `pkg-14` was the only disagreement.
4. Final full run saved to `eval-run.txt`: 19/20 scored packages agreed with the gold labels. `pkg-14` was the only disagreement. The run passed the 18/20 bar and all category floors were met.

**Package analysis**

I analyzed `pkg-14`. My rubric decided `reject`, while the gold label was `accept`. In my final run, the package failed my `Honest uncertainty` check. The candidate plan gives a specific explanation for the OSC response leak on reattach and presents that diagnosis confidently, while the reproduction evidence establishes the reattach behavior, regression window, and cache behavior but does not directly prove every part of that mechanism. My rubric therefore treated the diagnosis as containing more certainty than the reproduction evidence alone established. The gold label accepted the package because the diagnosis was sufficiently grounded in the reproduced behavior and the plan also identified a concrete risk and bounded mitigation.

**Check rationale**

My rubric currently says:

> `Honest uncertainty | The plan's claims about cause, assumptions, risks, unknowns, and any deviations read against the issue and repro evidence, using Honesty in the evidence guide. | Pass if verified facts are distinguished from assumptions or unknowns, and unresolved questions that could affect the implementation are stated rather than presented as certainty. If a deviation has occurred, the plan records what changed and why. | required`

I kept this check required because a plan should not present an unsupported assumption as an established fact before implementation begins. It also requires deviations to be recorded honestly when implementation changes the original plan. The trade-off became visible in `pkg-14`: my check interpreted part of its diagnosis as more certain than the reproduction evidence established, causing my rubric to reject a package whose gold label was `accept`.

**Trade-offs**

Making `Honest uncertainty` a required check creates a stricter standard for causal claims: it can reject a plan when the proposed diagnosis is plausible and consistent with the reproduction evidence but is stated more confidently than the evidence directly proves. `pkg-14` demonstrates that trade-off. My rubric rejected it on `Honest uncertainty`, while the gold label accepted it. I chose not to loosen the check before the final run because the rubric still agreed on 19/20 scored packages, exceeded the 18/20 bar, and matched every category, including both thread-and-convention packages.

---

Related paths: `plan.md` and `eval-run.txt` in this directory; your skill's files in
`tools/plan-check/`.
