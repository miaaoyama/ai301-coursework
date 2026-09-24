# Unit 2 — Claim and Reproduce

Path: `beat-1-sandbox/unit-2/reproduction.md`

## Your identity upstream

**GitHub username**

miaaoyama

---

## Posted upstream

**Claim comment**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/71#issuecomment-5820157903

Hi! I'd like to work on issue #71. I plan to reproduce the indentation problem in the test fixture and verify the behavior associated with the current xfail marker. I'll document the environment, steps, and results from my reproduction attempt and report back here before moving forward.

**Reproduction comment**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/71#issuecomment-5820527274

## Reproduction report

I reproduced the current failing-test condition associated with issue #71.

### Environment

- macOS (Darwin)
- Python 3.14.5
- pytest 9.1.1
- Repository development dependencies installed in `.venv` with `pip install -e ".[dev]"`

### Steps

From the repository root, I created the virtual environment and installed the development dependencies:

```bash
python3 -m venv .venv
.venv/bin/python -m pip install --upgrade pip setuptools wheel
.venv/bin/pip install -e ".[dev]"
```

I then ran the test associated with issue #71:

```bash
.venv/bin/python -m pytest tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy -v -rx
```

### Observed behavior

Pytest reported the test as XFAIL:

```text
tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy XFAIL [100%]

XFAIL tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy - issue #71 (manifest H-04): heading hierarchy fixture is indented, so it has no headings

1 xfailed in 0.10s
```

The test fixture contains indented Markdown headings and expects `_extract_heading_hierarchy()` to return a non-empty list containing heading levels 1, 2, and 3.

To verify the behavior directly rather than relying only on the existing xfail marker, I passed the same indented Markdown fixture to `_extract_heading_hierarchy()`:

```python
from ingestion.parsers.readme_parser import ReadmeParser

markdown = """
        # Main Title

        Some content

        ## Subsection

        More content

        ### Sub-subsection

        Even more content

        ## Another Section

        Final content
        """

parser = ReadmeParser()
headings = parser._extract_heading_hierarchy(markdown)

print("Extracted headings:", headings)
print("Heading count:", len(headings))
```

Output:

```text
Extracted headings: []
Heading count: 0
```

This confirms that the indented fixture produces no extracted headings.

### Result

I reproduced the behavior associated with issue #71. The issue-specific pytest test reports XFAIL, and directly passing the same indented Markdown fixture to `_extract_heading_hierarchy()` returned an empty list with a heading count of 0. I did not modify the fixture or remove the xfail marker during this reproduction.

## Eval iterations

**Run history**

1. Full run: 19/20 scored packages agreed with the gold labels. `pkg-09` was the only disagreement.
2. Full run: 18/20 agreed. `pkg-09` and `pkg-20` disagreed, and the disclosure category floor was unmet.
3. Targeted run on `pkg-09,pkg-20`: 1/2 agreed. `pkg-09` matched the gold label, while `pkg-20` was still incorrectly accepted.
4. Targeted run on `pkg-20`: 1/1 agreed after revising the conventions/disclosure handling.
5. Final full run: 20/20 scored packages agreed with the gold labels. All category floors were met and the run passed.

**Package analysis**

I analyzed `pkg-20`. The gold label was `reject`. During an intermediate run, my rubric decided `accept`. The reproduction evidence itself was strong: the environment was recorded, the steps were followable, and the observed Ghostty behavior matched the issue. However, the repository facts stated that Ghostty has a strict AI policy requiring all AI usage to be disclosed, including AI-assisted issues and comments. The candidate comments did not include the required disclosure. My earlier judgment focused too heavily on the technical reproduction evidence and did not reliably make the repository communication policy outcome-determinative. After revising the conventions/disclosure handling, I re-ran `pkg-20` and my rubric correctly returned `reject`, matching the gold label.

**Check rationale**

My rubric currently says:

> `Repo conventions respected | Claim comment and repro report read against repository-specific contribution instructions, issue or PR templates, and communication requirements identified in the package or evidence guide. | Pass if the claim and repro report follow every applicable explicit repository communication requirement shown in the evidence. Fail if either violates an applicable explicit requirement. If the evidence establishes a relevant requirement but does not establish whether it was satisfied, mark unclear. | required`

I revised this check so that repository communication requirements are evaluated explicitly rather than being treated as a general technical-conventions check. This mattered for `pkg-20`: its reproduction evidence was technically strong, but the repository required disclosure of AI assistance and the candidate comments did not include that disclosure. Making explicit communication requirements part of the pass condition allowed the rubric to reject that package for the specific repository-policy violation rather than relying only on the technical reproduction evidence.

**Trade-offs**

Making repository conventions a required check can reject a technically correct reproduction for a communication-policy violation. I accepted that trade-off because this rubric judges whether a package is ready to post upstream, not only whether the technical experiment is valid. `pkg-20` was my canary for this behavior: before the revision it was incorrectly accepted, and after the revision I re-ran it with `--only pkg-20` and received `reject`, matching the gold label. I then confirmed the change with a full run, which reached 20/20 with every category matched.

---

Related paths: `eval-run.txt` in this directory; your skill's files in `tools/repro-check/`.








