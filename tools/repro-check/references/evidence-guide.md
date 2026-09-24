# Evidence guide: where proof lives in a reproduction package

<!--
THIS IS THE PART YOU WRITE (new this week: Unit 1 handed you this file
finished; the scaffolding fades). The skill uses this guide as its map:
for every kind of proof a rubric check names, this file says WHERE to
find it in a package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repo-facts block, the
  claim comment, the repro report and its parts). In live mode (where
  on GitHub or in the draft: the issue thread, the repo's docs, the
  student's draft comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the versions named match what the
  issue targets, or the difference is called out") over adjectives
  ("environment is thorough").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute; the rubric swap showed you what that feels
like. Write the map you wish your grader had.
-->

## Environment

**Where it lives:** In an eval package, look at the issue context for the environment the issue targets and the repro report's environment record for the environment actually used. Also use relevant setup, dependency, configuration, or version information included with the reproduction artifacts. In live mode, compare the GitHub issue and repository documentation with the environment stated in the draft repro comment.

**What good looks like:** The environment record identifies the operating system or platform, relevant runtime or tool version, dependency or package version when relevant, and configuration or setup details that could materially affect the reported behavior. If the reproduction environment differs from a target named by the issue, the difference is explicitly identified so the result is not presented as though the environments were identical.

## Steps

**Where it lives:** In an eval package, look at the repro report's setup and reproduction steps together with commands, inputs, files, configuration changes, and starting-state information referenced by those steps. In live mode, read the draft repro comment and any repository setup instructions needed before performing the described actions.

**What good looks like:** The evidence establishes a starting state and a sequence of actions that another contributor could follow through the attempted trigger without guessing an issue-relevant command, input, prerequisite, or configuration change. Repository setup instructions may be referenced rather than unnecessarily repeated when the reference clearly identifies what must be followed.

## Behavior shown

**Where it lives:** In an eval package, compare the issue's described expected and problematic behavior with the repro report's output excerpts, logs, screenshots, error messages, or other artifacts. In live mode, compare the issue description and relevant issue-thread clarification directly with the evidence included in the draft repro comment.

**What good looks like:** For a reproduced issue, the artifact demonstrates the behavior the issue actually describes rather than a nearby error or different failure. For a cannot-reproduce result, the evidence shows that the relevant trigger was attempted under the recorded conditions and that the described behavior did not occur. Evidence of a different behavior does not establish reproduction of the target issue.

## Honesty

**Where it lives:** Compare the repro report's stated result and explanatory claims with its commands, outputs, logs, screenshots, and other reproduction artifacts. Also compare those claims with the issue's target behavior so that a technically real but unrelated failure is not reported as successful reproduction.

**What good looks like:** The stated outcome does not claim more than the evidence demonstrates. A successful reproduction is backed by evidence of the target behavior. A cannot-reproduce result is acceptable when the evidence shows a valid attempt and the report states that result without converting uncertainty into a stronger conclusion.

## Comms

**Where it lives:** In an eval package, read the claim comment and repro report against the issue context, repo-facts block, contribution policy, applicable issue or pull-request templates, and any stated AI-assistance or disclosure policy. In live mode, inspect the repository's contributor documentation and templates and compare them with the student's draft before posting.

**What good looks like:** The claim identifies the specific issue and promises the investigation and report without promising a fix, outcome, or completion date. The repro report describes the observed result specifically and in the student's own words rather than piggybacking on another contributor's report. Both follow explicit repository communication requirements. If the repository requires disclosure of AI assistance, the applicable posted comment includes that disclosure; omitting a required disclosure does not satisfy repository conventions.
