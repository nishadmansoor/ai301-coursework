# Evidence guide: where evidence lives in a plan package

## Diagnosis and grounding

**Where it lives:** In an eval package, read the issue context and the
repro-evidence block first, then the candidate plan's diagnosis and quoted
reproduction evidence. In live mode, use the Path Review issue thread, the
student's posted reproduction comment, and the diagnosis in the draft
plan.

**What good looks like:** The plan's stated cause or failure mechanism is
consistent with the behavior demonstrated by the reproduction. A diagnosis
may remain a hypothesis when the evidence does not prove the exact cause,
provided the plan makes that uncertainty clear and gives a bounded way to
investigate it. The diagnosis must not contradict the observed result.

## Scope

**Where it lives:** In an eval package, read the candidate plan's scope
statement, not-in-scope statement, and files-to-touch list, then compare
them with the issue context, repro evidence, and repo-facts block. In live
mode, compare the draft plan with the issue and the repository's stated
conventions.

**What good looks like:** The proposed work is limited to the reproduced
issue and identifies both what will change and what will not. Files or areas
outside the problem are not added without a reason supported by the issue or
repository evidence.

## Executability

**Where it lives:** In an eval package, read the candidate plan's approach,
files-to-touch list, and implementation steps, together with the repo-facts
block. In live mode, read the corresponding sections of the draft plan and
inspect the relevant repository documentation or files named by the plan.

**What good looks like:** Another developer could begin the proposed work
without inventing the overall direction. Small implementation details may
remain open when the plan identifies the investigation needed to resolve
them and explains how the result will guide the implementation.

## Test plan

**Where it lives:** In an eval package, read the candidate plan's test plan
and compare its commands, inputs, expected results, and regression checks
with the repro-evidence block. In live mode, compare the draft test plan
with the student's posted reproduction steps and the repository's available
test commands.

**What good looks like:** The plan exercises the reproduced behavior through
the real code and states an observable result that distinguishes the fixed
behavior from the original failure. Relevant controls or regression behavior
should be included when applicable. The plan does not need to resolve every
implementation question before testing begins.

## Honesty

**Where it lives:** In an eval package, read the candidate plan's risks and
unknowns and its Deviations section when present, then compare them with
claims in the diagnosis, scope, approach, and test plan. In live mode, use
the draft plan and, after implementation, the filled Deviations section.

**What good looks like:** Material uncertainty is explicitly identified
instead of being presented as fact. An acknowledged open question is
acceptable when the plan gives a reasonable path to resolve it. If
implementation differs from the posted plan, the deviation records what
changed and why; if nothing changed, the plan records that in the author's
own words.

## Comms

**Where it lives:** In an eval package, read the candidate plan comment and
compare it with the issue context, thread highlights, and repo-facts block.
In live mode, compare the draft or posted plan comment with the actual Path
Review issue thread and the repository's stated contribution and AI-use
conventions.

**What good looks like:** The comment describes the student's own diagnosis,
scope, approach, and test plan rather than piggybacking on another student's
plan. It responds to relevant maintainer or thread requirements and follows
the repository's stated contribution and AI-use conventions.
