# Rubric: is this reproduction package ready to post?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here. It ships empty on purpose: the judgment is your
work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the claim comment, the repro report's environment
     record, the artifacts read against the issue's description, the
     repo-facts block) or a location from your
     references/evidence-guide.md. "The report" is not a source; "the
     output excerpt read against the error the issue describes" is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (does
     the artifact show the issue's behavior?), never the write-up's
     shape (how many steps it has, how long it is, whether it uses a
     template's headings). Structure-shaped checks are what make
     graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad packages posted. The lecture named the
proof families: the environment is recorded, the steps are complete
and followable, the behavior shown matches the issue (not an adjacent
one), the outcome is stated honestly (an evidenced cannot-reproduce is
a pass, a confident wrong-target is not), and the words respect the
repo's conventions. A rubric that ignores a family will fail eval
packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Environment recorded | Repro report's environment record, including the operating system or platform, relevant runtime/tool version, dependency or package version when relevant, and configuration or setup details that could affect the reported behavior. | Pass if the report records the issue-relevant environment facts needed to interpret and repeat the attempt. If an environment fact could materially affect whether the issue appears and that fact is not recorded or recoverable from the supplied evidence, mark unclear. | required |
| Steps followable | Repro report's reproduction steps, read together with any commands, inputs, setup instructions, and artifacts referenced by those steps. | Pass if another contributor could follow the described setup and actions in order without having to guess an issue-relevant action, input, or prerequisite. | required |
| Behavior matches issue | Reproduction artifacts and output excerpts read against the behavior described in the issue. | Pass if the observed artifact or output demonstrates the same behavior described by the issue, or if a cannot-reproduce result clearly shows that the relevant behavior was tested and did not occur. Fail if the evidence demonstrates only an adjacent or materially different behavior. | required |
| Outcome supported | Repro report's stated outcome read against the commands, outputs, logs, screenshots, or other artifacts produced by the reproduction attempt. | Pass if the stated outcome accurately reflects the evidence shown, including an evidenced cannot-reproduce result. Fail if the report claims reproduction or another result that the supplied evidence does not support. | required |
| Repo conventions respected | Claim comment and repro report read against repository-specific contribution instructions, issue or PR templates, and communication requirements identified in the package or evidence guide. | Pass if the claim and repro report follow every applicable explicit repository communication requirement shown in the evidence. Fail if either violates an applicable explicit requirement. If the evidence establishes a relevant requirement but does not establish whether it was satisfied, mark unclear. | required |
| Required AI disclosure present | Repo-facts block read against the candidate claim comment and candidate repro report. | If the repo-facts block states that AI assistance must be disclosed for the type of candidate communication being graded, pass only when the candidate communication contains the disclosure required by that policy, including any explicitly required details such as the tool used and extent of assistance. Fail when that required disclosure is absent or incomplete. If the repo-facts block explicitly states that disclosure is not required for the candidate communication, or contains no applicable disclosure requirement, pass. | required |

## Verdict rule

Accept only if every required check passes. Reject if any required check fails. For required checks, unclear counts as fail because a reproduction package should not be posted when the evidence is insufficient to determine whether a required condition is satisfied. An evidenced cannot-reproduce outcome may pass when the environment, steps, tested behavior, and supporting artifacts clearly show what was attempted and the stated outcome accurately reflects that evidence.
