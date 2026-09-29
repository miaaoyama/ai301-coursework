# Evidence guide: where evidence lives in a plan package

<!--
THIS IS THE PART YOU WRITE (second week running: the judgment files
stay in your hands). The skill uses this guide as its map: for every
kind of evidence a rubric check names, this file says WHERE to find it
in a plan package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repro-evidence block,
  the candidate plan's scope statement or test plan, the plan comment,
  the repo-facts block). In live mode (where on GitHub or in the
  draft: the issue thread, the student's posted repro comment, the
  repo's docs, the draft plan and comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the stated cause cites behavior the
  repro evidence actually shows") over adjectives ("diagnosis is
  solid").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute, and this week that cuts twice: your
procedure.md tells the skill WHEN to gather each family, and this
guide tells it WHERE. Write the map you wish your executor had.
-->

## Diagnosis and grounding

Where it lives: In eval mode, compare the cause stated in the candidate plan with the behavior, steps, and observed result in the repro-evidence block. In live mode, compare the cause stated in the draft plan with the student's posted reproduction evidence on the issue.

What good looks like: The plan's diagnosis must explain the behavior actually shown by the reproduction evidence without contradicting it. If the evidence does not establish a root cause, the plan must present the cause as a hypothesis or unknown rather than as a confirmed fact.

## Scope

Where it lives: In eval mode, read the candidate plan's scope statement, including what it says is in scope, not in scope, and the files or areas it proposes changing. Compare that scope with the issue context and reproduction evidence. In live mode, read the same parts of the draft plan against the issue and posted reproduction evidence.

What good looks like: The plan proposes one bounded change that addresses the reproduced problem. The files and areas named should be relevant to that change, and unrelated cleanup, rewrites, or additional features should remain outside the scope.

## Executability

Where it lives: In eval mode, read the candidate plan's implementation steps, including the files or areas it identifies, the proposed approach, and the order of work. Compare those steps with the issue context and reproduction evidence. In live mode, read the implementation steps in the draft plan against the issue, repository context, and posted reproduction evidence.

What good looks like: The plan gives enough concrete direction for another contributor to begin the change without needing the author to explain the intended approach. The proposed work identifies the relevant code or area, describes what will change, and connects those actions to the reproduced problem.

## Test plan

Where it lives: In eval mode, read the candidate plan's test plan and compare it with the original steps and observed result in the repro-evidence block. In live mode, read the draft plan's test plan against the student's posted reproduction steps and evidence on the issue.

What good looks like: The test plan identifies an observable result that would show whether the proposed change fixed the reproduced problem. It should exercise the relevant code path and connect back to the original reproduction behavior so that success or failure can be determined from the result.

## Honesty

Where it lives: In eval mode, read the candidate plan's claims about the cause, risks, unknowns, assumptions, and any recorded deviations, and compare them with the issue context and reproduction evidence. In live mode, read those same claims in the draft plan against the issue thread, posted reproduction evidence, and any deviation notes added during implementation.

What good looks like: The plan distinguishes verified facts from assumptions or unknowns and does not present unsupported conclusions as certain. Risks or unresolved questions that could affect the implementation are stated clearly, and if the implementation has deviated from the original plan, the plan records what changed and why.

## Comms

Where it lives: In eval mode, read the candidate plan comment against the issue context and thread highlights, then compare it with the repo-facts block for contribution instructions, templates, and disclosure requirements. In live mode, read the draft plan comment against the current issue thread and the repository's stated contribution rules and templates.

What good looks like: The plan comment responds to relevant maintainer guidance or constraints in the thread and follows applicable repository contribution requirements, including required templates or AI-use disclosures. It should not ignore a stated request, restriction, or convention that applies to the proposed work.
