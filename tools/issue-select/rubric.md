# Rubric: is this a good first issue?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| not-archived | The `archived:` field on the repo line under Repo facts | Reads `no` | required |
| repo-active | The "last 5 default-branch commits" list and the "last push to any branch" line under Repo facts | Newest default-branch commit is within 90 days of the bundle's `captured:` date. A missing or stale `latest release` does not by itself fail this check: many healthy projects ship from the default branch and never cut releases, so commit recency is the signal and release recency is only corroboration | required |
| unclaimed | The "this issue: assignees:" and "linked PRs:" fields under Repo facts, plus the Comments section | Assignees is none, no linked PR is open, and no non-author claim comment ("I'll take this", "working on this") sits in the thread within 60 days of the capture date without a maintainer redirecting it | required |
| bounded-scope | The issue body, its `labels:` line, and the Comments section | The issue is one bounded piece of work. It fails only on: (a) an explicit umbrella or tracking issue, i.e. one whose body is a list of separate issue references or sub-items meant to be split into separate work; (b) a new feature or new first-class UI element that no maintainer has endorsed, where endorsement means a maintainer-applied triage label or a maintainer comment agreeing it should be built, or that names a prerequisite still unresolved in the body ("asset TBD", spec undecided); (c) a usage or support question rather than a change request; (d) a maintainer statement in the thread that the fix requires changes to core internals; (e) an approach still unsettled, shown by an extended thread (20 or more comments) in which no maintainer has decided how it should be implemented, or by more than one closed unmerged PR that already attempted it. Two or more closed linked PRs on an issue that is still open count as abandoned attempts, whether or not the bundle states their merge status: had one landed, the issue would not still be open. A single reported defect stays bounded even when the body enumerates several contributing causes or lists optional follow-up suggestions | required |
| policy-allows-ai | The "contribution policy" line under Repo facts, including any AI-policy files it names | The policy does not ban AI-generated or AI-assisted contributions outright. Disclosure, human-review, personal-understanding and testing requirements are conditions, not bans, and pass | required |
| maintainer-responds | The "maintainer first-response sample" list under Repo facts, counting only eligible samples: those not marked "opened by a maintainer" and opened at least 14 days before the capture date | Among eligible samples, at least one drew a maintainer comment within 30 days. Ranks only: a large project with a triage backlog is still worth contributing to, so this never rejects | preferred |
| clean-history | The issue's open date against the capture date, and any closed unmerged PRs named in linked PRs or the Comments section | Issue has been open under 24 months and shows no more than one abandoned prior attempt | preferred |
| labeled-friendly | The `labels:` line on the issue header | Carries `good first issue`, `good-first-issue`, `beginner`, or an equivalent maintainer-applied newcomer label | preferred |

## Verdict rule

Accept when every `required` check grades `pass`. A single `required` fail
rejects the issue. `preferred` checks never change the verdict; they rank the
accepted issues against each other.

`unclear` counts as `fail` on every required check except `policy-allows-ai`,
where an absent or unstated contribution policy grades `pass`. Silence is not a
restriction: most repos state nothing, and treating that as a ban would reject
the majority of healthy issues. Everywhere else, a first issue whose evidence I
cannot verify is not a first issue I should take.

All recency thresholds are measured against the bundle's `captured:` date in
eval mode, and against today's date in live mode.
