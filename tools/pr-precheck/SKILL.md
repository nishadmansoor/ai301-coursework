---
name: pr-precheck
description: Grade a PR package (a candidate pull request read against the plan it claims to implement and the issue that plan belongs to) and decide whether it is ready to submit. Use when checking your own branch, draft PR title, and description before opening the pull request, or when grading an eval package bundle.
---

# pr-precheck: rubric-driven PR grading

## The question

Answer one question: is this pull request ready to submit?

A PR package consists of the candidate plan, including any deviation notes, the branch diff, the draft PR title and description, and test evidence, read against the issue and the repository's contribution standards. Judge whether the implementation follows the plan, the evidence supports the claims, the changes are reviewable, and the submission meets the applicable requirements.

Do not substitute a general code review for this task. Grade the complete package against the student-authored rubric and procedure.

## Inputs and modes

Use one of two modes.

**Live mode:** Read the student's package from the working repository. The inputs are:

- `plan.md`, including any `## Deviations` section explaining changes from the original plan.
- The branch diff against the default branch, produced by running `git diff main...HEAD` from the working copy.
- `pr_draft.md`, containing the proposed PR title and description.
- `test_evidence.md`, containing before-and-after reproduction results and relevant test, lint, and type-check output.
- The issue thread associated with the change.
- The repository's `.github/PULL_REQUEST_TEMPLATE.md` and `docs/CONTRIBUTING.md`, when present.

Use the procedure and evidence guide to determine how to gather and compare these inputs. For a house-chain assignment, use the house plan and reproduction package specified by the course workflow in place of the student's own issue evidence.

Read the actual package contents. Do not assume a claim is true merely because the draft PR says it is. Compare the description with the diff and the test evidence. Do not treat files in the working directory as part of the proposed PR description unless the draft explicitly includes their content.

**Eval mode:** Grade the package bundle supplied in `eval/packages/`. The bundle is the entire evidence source. Do not fetch additional files, browse GitHub, or infer facts that are not in the bundle. Run every rubric check and apply the complete verdict rule.

## The scope seam (live mode only)

In live mode, read `scope.md` before gathering or grading any package evidence. Confirm that the issue belongs to the repository named in the scope file and follow the applicable repository rules.

If the repository is outside the defined scope, refuse to grade the package and explain that it is out of scope. If the repository line still contains an unfilled placeholder, stop and ask the student to fill in the correct repository rather than guessing.

In eval mode, ignore `scope.md` entirely.

## The voice seam (live mode only)

In live mode, read `voice-guide.md` and evaluate the proposed PR title and description against its writing rules. When a rule is broken, identify the rule and quote or describe the relevant wording in the readable summary.

The voice guide does not independently determine the verdict. It can affect the verdict only when a rubric check explicitly evaluates the voice guide.

In eval mode, ignore `voice-guide.md` entirely.

## Component reads

Read `rubric.md` for the checks, their evidence requirements, their pass conditions, their weights, and the verdict rule.

Read `references/evidence-guide.md` to determine where each type of evidence lives, how to locate it, and what good evidence looks like.

Execute `procedure.md` as written. Follow its read order, evidence-gathering instructions, check-execution instructions, and verdict-assembly rules. Do not silently invent missing steps. If the procedure is silent or ambiguous about a step, report the gap in the readable summary rather than improvising.

If `rubric.md` contains no completed checks, stop and explain that the skill cannot grade without a rubric. If `procedure.md` contains no completed steps, stop and explain that the skill cannot grade without a procedure. Do not produce a normal grading verdict when either required component is missing.

## Verdict and output

Use exactly one of the two verdicts:

- `accept`: the package is ready to submit.
- `reject`: the package should be held until the required issues are addressed.

Apply the verdict rule in `rubric.md`. Do not invent additional verdict conditions or override the rubric.

You may provide a short readable summary before the final JSON block. Report each check, its grade, and the evidence that determined the grade. Include any relevant procedure gaps and live-mode voice-guide violations.

End your response with the fenced JSON block below. Preserve its schema and field order exactly. The JSON must be valid, the final fenced block in the response, and nothing may follow it.

```json
{
  "item": "<PR URL or bundle id>",
  "checks": [
    {"name": "<check name>", "grade": "pass|fail|unclear",
     "evidence": "<one line: the fact or quote that decided it>"}
  ],
  "verdict": "accept|reject"
}
```
## Grading discipline

* Evidence first: Every grade must be supported by a specific fact, observation, or quote from the package. Record the deciding evidence for each check.
* Grade the package, not the polish: Evaluate whether the implementation and submission are complete, accurate, testable, and reviewable. Do not reward confident wording or penalize concise writing without a rubric-based reason.
* The rubric decides: Apply each check’s stated evidence requirements and pass condition. Do not change a grade because of personal preference.
* The procedure decides how: Follow the written procedure. Report gaps instead of filling them with invented steps.
* Be careful with claims: A test claim must be supported by test evidence. A description claim must agree with the diff. A change from the plan must be explained in the plan’s deviation notes.
* Handle uncertainty consistently: Use unclear when the available evidence does not establish pass or fail. If the rubric’s verdict rule does not specify how unclear affects the verdict, treat it as fail.
* Do not invent evidence: In eval mode, use only the package bundle. In live mode, distinguish observed results from assumptions and do not claim that a test, check, or review passed unless the evidence supports that claim.


