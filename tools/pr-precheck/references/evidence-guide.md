# Evidence guide: where evidence lives in a PR package

## Plan fidelity (harness category: silent-drift)

Where it lives: In eval mode, read the plan-context block's stated
scope, implementation steps, boundary, and any recorded deviation
notes. Compare them with the candidate PR's complete diff, changed
files, commits, title, and description. In live mode, read `plan.md`
including its deviation notes and compare it with the complete branch
diff from `git diff main...HEAD` and the draft PR title and description.

What good looks like: Every change in the diff falls within the work
promised by the plan or is accounted for by a recorded deviation that
states what changed and why. Planned work presented as completed is
visible in the diff. The PR title and description describe the work
the diff actually contains without claiming unsupported scope,
behavior, testing, or completeness. An honestly recorded limitation,
deferred edge, or deviation does not by itself make the PR unready.

## Test evidence (harness category: not-tested)

Where it lives: In eval mode, read the candidate PR's test-evidence
section against the plan-context block's test plan and original
reproduction evidence. Also read the repo-facts block for stated test,
lint, build, or validation requirements. In live mode, compare the
captured test output with the test plan in `plan.md`, the original
reproduction behavior, and the repository's stated checks.

What good looks like: The evidence shows that the behavior affected by
the change was actually exercised and records an observable result that
can be compared with the expected result. When before-and-after
evidence is applicable, the original behavior and changed behavior are
both visible or otherwise concretely demonstrated. Applicable
repository checks are shown with their outcomes. A statement such as
"tests pass" or a command name without its observable outcome is not
enough. If a check could not be run, the limitation and its effect on
confidence are explicitly disclosed rather than silently omitted.

## Diff quality (harness category: unreviewable)

Where it lives: In eval mode, inspect the candidate PR's complete
unified diff, changed files, and commit list. Compare the changed hunks
with the implementation described by the plan. In live mode, inspect
the complete branch diff from `git diff main...HEAD` and the branch's
commits against `plan.md`.

What good looks like: The intended implementation is visible and can
be isolated by a reviewer without unrelated changes obscuring it.
Supporting changes are directly connected to the planned work. The
diff does not contain unrelated cleanup, accidental files, debugging
output, dead code, commented-out blocks, unnecessary formatting churn,
or other drive-by edits that bury the intended change.

## Standards and comms (harness category: standards-wall)

Where it lives: In eval mode, read the repo-facts block for the
repository's PR-template asks, contribution instructions, stated
policies, and any AI-use disclosure requirement. Compare those
requirements with the candidate PR's title and description and with
relevant maintainer direction included in the issue or thread
highlights. In live mode, read the repository's PR template,
`CONTRIBUTING.md` or equivalent contribution guidance, stated
disclosure policy, and relevant issue-thread instructions, then compare
them with the draft PR title and description.

What good looks like: Every applicable repository requirement is
addressed with actual information rather than untouched boilerplate or
an empty section. Required disclosures, including AI-use disclosure
when the repository requires it, are present. Relevant explicit
maintainer instructions are followed or honestly addressed. A
requirement that clearly does not apply does not need invented content.
Whether the description accurately represents the diff is graded under
Plan fidelity rather than under this family.
