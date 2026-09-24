cat > beat-1-sandbox/unit-1/selection.md <<'EOF'
# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/69

**Verdict output**

Summary

Both issues are in scope (codepath/pathreview-ai301-fa26-s3), and the Path Review house rule applies: student claim comments never block an issue here.

Repo-level facts (same for both): Last 5 default-branch commits all authored by Andrew Burke (Aburke225, author_association COLLABORATOR), most recent 2026-09-16 — 7 days before today (2026-09-23). Repo is not archived, last push 2026-09-16. No AI_POLICY.md/AGENTS.md found; CONTRIBUTING.md and the PR template require test/lint/CI compliance and a completed template but say nothing about AI-assisted work.

#69 — Output parser crashes on a top-level JSON array fallback → accept

┌────────────────────┬───────┬────────────────────────────────────────────────────────────────────────────────────┐
│       Check        │ Grade │                                      Evidence                                      │
├────────────────────┼───────┼────────────────────────────────────────────────────────────────────────────────────┤
│ Maintainer         │ pass  │ All 5 recent commits by collaborator Aburke225, latest 7 days ago                  │
│ activity           │       │                                                                                    │
├────────────────────┼───────┼────────────────────────────────────────────────────────────────────────────────────┤
│ Repo activity      │ pass  │ Not archived; last push 7 days ago                                                 │
├────────────────────┼───────┼────────────────────────────────────────────────────────────────────────────────────┤
│ Bounded newcomer   │ pass  │ One specific bug (.items() on a list crashes), named files, named fix target, 2–4h │
│ scope              │       │  estimate                                                                          │
├────────────────────┼───────┼────────────────────────────────────────────────────────────────────────────────────┤
│ Issue availability │ pass  │ No assignees, no linked/mentioned PRs; 3 student "I'd like to work on this"        │
│                    │       │ comments don't block per house rule                                                │
├────────────────────┼───────┼────────────────────────────────────────────────────────────────────────────────────┤
│ Contribution       │ pass  │ No AI restriction anywhere in repo                                                 │
│ policy             │       │                                                                                    │
└────────────────────┴───────┴────────────────────────────────────────────────────────────────────────────────────┘

Ranking by fit

Both accepted, but they suit the stated profile (strong Python/ML background, wants to grow software engineering and AI/ML skills) very differently:

1. #69 — a real bug in the RAG pipeline's output_parser.py (handling LLM output shapes), paired with removing a strict=True xfail marker once fixed. This is actual code-reading/debugging in an AI/ML-adjacent module — better matches the stated goal of leveling up engineering skill inside an LLM system.
2. #73 — a pure two-file text/config sync with zero code logic. Safe and fast, but it won't build the engineering muscle the profile calls out.

[
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/69",
    "checks": [
      {"name": "Maintainer activity", "grade": "pass", "evidence": "Last 5 commits all by collaborator Aburke225, most recent 2026-09-16 (7 days before capture date 2026-09-23)"},
      {"name": "Repo activity", "grade": "pass", "evidence": "isArchived: false, pushedAt: 2026-09-16 (7 days ago)"},
      {"name": "Bounded newcomer scope", "grade": "pass", "evidence": "Body names one bug ('.items() on list raises AttributeError'), the fix target (fallback path), files, and effort estimate"},
      {"name": "Issue availability", "grade": "pass", "evidence": "assignees: [], no cross-referenced/connected PRs in timeline; 3 student claim comments only, no maintainer claim, house rule ignores student claims"},
      {"name": "Contribution policy", "grade": "pass", "evidence": "CONTRIBUTING.md and PR template require passing CI/tests/template but state no AI restriction; no AI_POLICY.md/AGENTS.md found in repo tree"}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/73",
    "checks": [
      {"name": "Maintainer activity", "grade": "pass", "evidence": "Last 5 default-branch commits all by collaborator Aburke225, most recent 2026-09-16 (7 days before capture date 2026-09-23)"},
      {"name": "Repo activity", "grade": "pass", "evidence": "isArchived: false, pushedAt: 2026-09-16 (7 days ago)"},
      {"name": "Bounded newcomer scope", "grade": "pass", "evidence": "Body identifies exact mismatch between README.md and .env.example and states the desired outcome: 'Make the two files agree'"},
      {"name": "Issue availability", "grade": "pass", "evidence": "assignees: [], comments: [], no cross-referenced/connected PRs in timeline"},
      {"name": "Contribution policy", "grade": "pass", "evidence": "Same repo-wide policy as #69: no AI restriction found"}
    ],
    "verdict": "accept"
  }
]

## Eval iterations

**Run history**
agreement: 17/20 scored items  (bar: 18/20: below the bar)
agreement: 17/20 scored items  (bar: 18/20: below the bar)
agreement: 18/20 scored items  (bar: 18/20: PASS)
agreement: 18/20 scored items  (bar: 18/20: PASS)

**Issue analysis**

issue-19: accept. The gold label was accept, and the final evaluation returned accept.

The issue states: “There are two potential causes which should be fixed:
1. The matchers are slow for certain rewrites (quadratic instead of linear)
2. UI update is waiting for the matching thread to finish”

My rubric returned accept because the issue was not explicitly identified as an umbrella/tracking issue, pure usage question, or an issue requiring core-internal changes. The issue also had no availability blockers in the final evaluation.

**Check rationale**

“Passes only if the issue is not explicitly an umbrella/tracking issue, not a pure usage question, has no unresolved design debate in the thread, and has no maintainer statement that the fix requires core-internal changes”

I kept this check focused on whether an issue is concrete enough for a first contribution rather than trying to judge subjective difficulty. The goal is to reject issues where the scope is explicitly broad, where there is unresolved design work, or where the issue requires internal changes beyond what a newcomer could reasonably address.

**Trade-offs**
This check can be conservative when an issue is concrete but the available evidence does not make its scope completely clear. I accepted that trade-off because the rubric treats unclear required checks as failures.

I also re-ran individual canaries with `--only`. For issue-19, the later canary produced:

`issue-19  accept  accept   yes`

The final full evaluation also returned 18/20, so I kept the current check rather than broadening it further.

**Selection rationale**

1. Issue #69 fits my interests in Python, AI/ML, and software engineering, and the issue estimates about 2–4 hours of work. It involves debugging an output parser in a RAG pipeline, so it is relevant to the skills I want to develop without being an excessively large project.

2. The verdict correctly identified that #69 is a specific, available bug with a clear fix target and no contribution-policy restriction. The rubric could not fully weigh that #69 is more relevant to my AI/ML and software-engineering interests than #73, which is mainly a documentation/configuration consistency change.

3. The main anticipated difficulty is understanding the existing RAG output-parsing code and the different LLM output shapes. I expect some codebase exploration and testing will be needed, but the issue's stated scope and estimate make it reasonable for a first contribution.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
EOF