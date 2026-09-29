# Unit 3 Plan — Issue #71

## Diagnosis

The `test_extract_heading_hierarchy` fixture contains Markdown headings indented by eight spaces. Markdown treats those indented lines as a code block rather than headings, so `_extract_heading_hierarchy()` returns an empty list. My Unit 2 reproduction confirmed that passing the current indented fixture to `_extract_heading_hierarchy()` returns `[]` with a heading count of 0.

## Scope

This change is limited to correcting the heading hierarchy test fixture in `tests/unit/test_readme_parser.py` and removing the issue #71 `@pytest.mark.xfail` marker.

I do not plan to change `_extract_heading_hierarchy()` or other production parser behavior because the reproduction evidence shows that the current fixture, rather than the parser, is the source of the failing-test condition. If the corrected fixture reveals a separate parser problem during implementation, I will record that as a deviation before expanding the change.

## Implementation

1. Update the Markdown fixture used by `test_extract_heading_hierarchy` so the `#`, `##`, and `###` lines are interpreted as Markdown headings rather than indented code.
2. Remove the issue #71 `@pytest.mark.xfail` marker from the test.
3. Keep the production parser unchanged unless testing the corrected fixture provides evidence of a separate parser defect.

## Test plan

First, re-run the same issue-specific test used during my Unit 2 reproduction:

`.venv/bin/python -m pytest tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy -v -rx`

Before the change, this test reports `XFAIL`, and directly testing the fixture returns an empty heading list. After the change, the issue-specific test should report `PASS` and verify the expected heading hierarchy containing levels 1, 2, and 3.

Then run the complete relevant test file:

`.venv/bin/python -m pytest tests/unit/test_readme_parser.py -v`

This checks that correcting the fixture and removing the xfail marker do not introduce regressions in the surrounding README parser tests.

## Risks and unknowns

The main risk is that another assertion or test in the same file could depend on the existing fixture structure. If implementation reveals additional work is necessary, I will keep it limited to issue #71 where possible and record any change from this plan in the Deviations section.

## Deviations

No implementation deviations occurred. The change matched the posted plan: I removed the issue #71 xfail marker and corrected the indentation in the test fixture without changing the production parser. The issue-specific test passed after the change, and the full README parser test file completed with 14 passed and 1 unrelated existing xfail.
