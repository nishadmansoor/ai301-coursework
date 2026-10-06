# Rubric: is this reproduction package ready to post?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Environment | The repro report's environment record and the `repo-facts` block, compared with the issue's stated target. | The evidence identifies the relevant environment conditions and either matches the issue's target or explicitly identifies a meaningful difference that affects interpretation of the result. | required |
| Steps | The reproduction procedure in the repro report, including its starting state and trigger actions. | The stated procedure is sufficient for another person to follow from the given starting state to the reported test or trigger without relying on an unstated result-changing step. | required |
| Behavior shown | The repro report's output excerpts, logs, screenshots, or other artifacts, read against the issue description in the issue context. | The artifacts either demonstrate the issue's described behavior, or demonstrate a genuine reproduction attempt whose observed result supports the report's stated cannot-reproduce conclusion. A different or adjacent behavior that does not establish either outcome does not pass. | required |
| Honesty | The claim comment and repro report conclusion compared with the issue context and the supporting artifacts. | The comments accurately state what the evidence establishes. A supported cannot-reproduce conclusion passes even when the attempted test did not trigger the issue, provided the report clearly identifies that limitation and does not claim the issue is absent. A stronger claim than the evidence supports fails. | required |
| Comms | The claim/repro comments together with repository policy or conventions included in the package, including any AI-use disclosure requirement. | The comments make specific claims about the student's own work and respect applicable repository communication rules. If the repository policy requires disclosure of AI use for issues or comments, the candidate comments must contain an explicit disclosure identifying the AI tool used and the extent of its assistance. If the repository policy does not require AI disclosure for the communication being graded, lack of disclosure does not fail this check. | required |
## Verdict rule

Accept if every required check passes. Reject if any required check fails
or is unclear. Preferred checks, if added later, never change the verdict.
For a full package, all five checks are considered. In claim-only live mode,
checks that require the repro report are not applicable and are excluded from
the verdict as specified by the skill.
