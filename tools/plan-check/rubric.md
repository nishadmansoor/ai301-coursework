# Rubric: is this plan ready to post and build from?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Diagnosis | The plan's diagnosis and quoted repro evidence, read against the reproduction evidence's observed result and identified failure location. | The diagnosis is consistent with the reproduced behavior and identifies a plausible cause or failure mechanism supported by the evidence. A cause may remain a hypothesis when the plan makes that uncertainty clear and gives a reasonable way to investigate it. The diagnosis must not contradict the reproduced evidence. | required |
| Scope | The plan's scope statement and files-to-touch list, read against the issue/repro target and the repo-facts block. | The proposed change is bounded to the reproduced issue, identifies what will and will not change, and does not introduce unrelated work or scope creep. | required |
| Cause-targeting | The plan's approach and files-to-touch list, read against the reproduction evidence's failure path and the plan's diagnosis. | The proposed implementation targets the diagnosed cause or a clearly justified point in the relevant failure path. The plan may include a bounded investigation step when the exact implementation site is not yet established, as long as it does not merely hide or bypass the observed symptom. | required |
| Executability | The plan's approach and ordered implementation steps, read against the files-to-touch list and repo-facts block. | A developer with access to the repository could begin implementing or investigating the proposed change without inventing a major missing direction. Small implementation details may remain open when the plan names how they will be resolved. | required |
| Test plan | The plan's test plan, read against the reproduction evidence's original commands, inputs, and observed failure. | The planned verification exercises the reproduced behavior through the real code and states an observable expected result that would distinguish the fixed behavior from the original failure. Relevant controls or regression behavior should be included when applicable. | required |
| Unknowns and risks | The plan's risks and unknowns, read against the diagnosis, scope, approach, and test plan. | Material uncertainty is either resolved by the evidence or explicitly acknowledged. An open question does not fail the check when the plan gives a bounded way to resolve it and the uncertainty does not make the overall plan directionless. Risks must not be presented as settled facts when they are only assumptions. | required |
| Thread and conventions | The plan comment, read against the issue thread highlights and the repo-facts block. | The comment accurately represents the plan, addresses relevant issue/thread requirements, and follows the repository's stated conventions for the plan, branch, coordination, and AI-use process when those conventions are provided. | required |

## Verdict rule

Accept if every required check passes.

Reject if any required check fails.

An `unclear` result counts as a fail. Preferred checks, if added later, never change the verdict.

For every rejected package, the output should identify at least one failed or
unclear required check as the deciding reason. Do not accept a package merely
because its plan is well formatted or detailed; the checks judge whether the
planned change is supported, bounded, executable, and testable.
