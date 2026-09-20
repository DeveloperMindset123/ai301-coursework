# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/6

**Verdict output**

[Your skill's live-mode output for this issue, pasted verbatim and ending with the
fenced JSON verdict block. A summary does not satisfy this field.]

**The verdict must record `accept` for this issue.** Choose an issue your own skill
accepts. If your skill rejects every candidate you try, that is a signal about your
rubric rather than about the issues: revise it and re-run — retries are unlimited and a
partial re-run costs about $0.20 — or run the skill on different candidates. Output
recording `reject` for the issue you chose earns no credit for this field.

````
I have all the evidence I need. Let me compile the grades.

---

**Check-by-check summary for https://github.com/codepath/pathreview-ai301-fa26-s1/issues/6**

| Check | Grade | Evidence |
|---|---|---|
| **not-archived** | PASS | `isArchived: false` from repo API |
| **repo-active** | PASS | Newest default-branch commit is 2026-09-16 (4 days ago, well within 90-day window) |
| **unclaimed** | PASS | Assignees: none; PRs: zero open in the entire repo; comments on issue: none |
| **bounded-scope** | PASS | Single reported bug in one file (`rag/retriever/hybrid.py`), no umbrella structure, no unresolved prerequisites, 0 comments, 0 prior PRs |
| **policy-allows-ai** | PASS | `docs/CONTRIBUTING.md` states only process requirements (CI green, PR template, conventional commits) — no AI-contribution ban or restriction |
| **maintainer-responds** *(preferred)* | UNCLEAR | All issues in the repo were opened 2026-09-10 or later (< 14 days before today 2026-09-20); no eligible samples exist yet |
| **clean-history** *(preferred)* | PASS | Issue is 10 days old, no linked PRs at all, zero abandoned attempts |
| **labeled-friendly** *(preferred)* | FAIL | Labels are `docs`, `rag`, `tier-2` — no `good first issue` or newcomer equivalent |

**Verdict: ACCEPT.** All five required checks pass. The two preferred misses (`maintainer-responds` unclear due to repo youth, `labeled-friendly` absent) don't change the verdict.

**Fit note:** This issue is a strong match for your profile. The bug lives in the numerical/algorithmic heart of a RAG system — BM25 score normalization is exactly the kind of correctness-argued, math-grounded problem you ranked highest. It's a single bounded Python file, verifiable locally without GPU hardware, and the 4–6 hour estimate keeps the PR small and well-scoped — ideal for getting reps on the contribution loop itself.

```json
{
  "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/6",
  "checks": [
    {"name": "not-archived", "grade": "pass", "evidence": "isArchived: false from gh repo view"},
    {"name": "repo-active", "grade": "pass", "evidence": "Newest default-branch commit: 2026-09-16, 4 days before today 2026-09-20"},
    {"name": "unclaimed", "grade": "pass", "evidence": "Assignees: [], linked PRs: none (repo has 0 PRs total), issue comments: []"},
    {"name": "bounded-scope", "grade": "pass", "evidence": "Single defect in rag/retriever/hybrid.py, no umbrella structure, 0 comments, 0 prior PRs"},
    {"name": "policy-allows-ai", "grade": "pass", "evidence": "docs/CONTRIBUTING.md imposes only process requirements (CI, PR template); no AI-contribution ban"},
    {"name": "maintainer-responds", "grade": "unclear", "evidence": "All repo issues opened 2026-09-10 or later — none are 14 days old; no eligible response samples exist"},
    {"name": "clean-history", "grade": "pass", "evidence": "Issue opened 2026-09-10 (10 days old), no linked PRs, zero abandoned attempts"},
    {"name": "labeled-friendly", "grade": "fail", "evidence": "Labels are docs, rag, tier-2 — no good-first-issue or newcomer equivalent"}
  ],
  "verdict": "accept"
}
```
````

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

1. 2/3, smoke test (`--limit 3`, partial)
2. 14/20, full run
3. 9/9, targeted re-run (`--only`, 9 items, partial)
4. 19/20, full run
5. 8/9, targeted re-run (`--only`, 9 items, partial)
6. 1/1, targeted re-run (`--only issue-15`, partial)
7. **20/20, full run, saved to `eval-run.txt`**

**Issue analysis**

`issue-15`, zulip/zulip#19589, "Separate `command` and `text` field for
slack-compatible outgoing webhook".

**My rubric's decision: `reject`. Gold label: `reject`.** These agree on my
final run, but they did not agree on the run before it, and that disagreement
is the more useful thing to report.

At 19/20 this was my single miss. My rubric graded it `accept` against a gold
label of `reject`, and the categories line read `scope 3/4` while every other
category was full. The cause was a regression I introduced myself. When I
rewrote `bounded-scope` to stop over-rejecting, I dropped a disqualifier my
first draft had carried, "not a design still being debated with no maintainer
decision", which is listed explicitly in `references/evidence-guide.md`: "when
the thread shows the design is still being debated and no maintainer has
settled it". Nothing in my rewritten check looked at thread length or at
failed prior attempts, so an issue open since 2021-08-18 with 97 comments
passed as bounded.

The bundle's own facts are what a working check should have caught. The
repo-facts block records `this issue: assignees: none; linked PRs:
zulip/zulip#20840 (closed); zulip/zulip#23123 (closed)`, and the thread is
stamped `## Comments (97 total, first 40 shown)`. Two closed pull requests
against an issue that is still open are two abandoned attempts.

After I restored the disqualifier as clause (e), the check graded the issue
`fail` on this evidence: "Two closed linked PRs (#20840 and #23123) with issue
still open indicates both were unmerged, more than one closed unmerged prior
attempt". A second required check also moved against it. `unclaimed` graded
`unclear`: "Bundle shows only first 40 of 97 comments; 57 unshown comments
(likely more recent) cannot be checked for a claim comment within the 60-day
window ending 2026-08-05". My verdict rule counts `unclear` as `fail` on every
required check except `policy-allows-ai`, so either one alone produces the
reject.

What I take from it is that the issue looks healthy on every surface signal.
It carries `good first issue`, `help wanted` and `area: integrations`, the
repo is active, and nobody is assigned. It is still a bad first issue, because
two people have already tried and the approach was never settled. My first
draft knew that and my rewrite forgot it.

**Check rationale**

The check I am writing about is `bounded-scope`, quoted from
`tools/issue-select/rubric.md` as currently uploaded:

```
| bounded-scope | The issue body, its `labels:` line, and the Comments section | The issue is one bounded piece of work. It fails only on: (a) an explicit umbrella or tracking issue, i.e. one whose body is a list of separate issue references or sub-items meant to be split into separate work; (b) a new feature or new first-class UI element that no maintainer has endorsed, where endorsement means a maintainer-applied triage label or a maintainer comment agreeing it should be built, or that names a prerequisite still unresolved in the body ("asset TBD", spec undecided); (c) a usage or support question rather than a change request; (d) a maintainer statement in the thread that the fix requires changes to core internals; (e) an approach still unsettled, shown by an extended thread (20 or more comments) in which no maintainer has decided how it should be implemented, or by more than one closed unmerged PR that already attempted it. Two or more closed linked PRs on an issue that is still open count as abandoned attempts, whether or not the bundle states their merge status: had one landed, the issue would not still be open. A single reported defect stays bounded even when the body enumerates several contributing causes or lists optional follow-up suggestions | required |
```

It is written as a closed list of named failure conditions, signalled by the
phrase "fails only on". My first draft did the opposite. It described in
general terms what a good issue looks like, and an open-ended description
grades however the reader is feeling that run. That draft said the issue must
ask for "one bounded change: not an umbrella or tracking issue listing
sub-items". On `issue-19` the grader applied it like this: "Issue enumerates
two explicit root causes 'which should be fixed' plus three additional feature
suggestions across separate subsystems (parallelism, selective matching,
threaded apply)". That is a defensible reading of my words and the wrong
answer. `issue-19` is one reported bug, a UI freeze when selecting large
subgraphs, filed by a COLLABORATOR, carrying maintainer triage labels
`Type: bug, Category: Proof mode, Priority: High`, with zero comments. The
author diagnosed two causes and volunteered three optional ideas. Enumerating
causes inside one defect is a well-written bug report, not an umbrella. That
is why the check now ends with a sentence protecting exactly that case.

Each clause is there because a specific bundle demanded it. Clause (a) is
`issue-10`, tldr-pages' "Documentation request megaissue", whose body is a
bare list of 37 issue references. Clause (b) is `issue-20`, an excalidraw
feature request opened by `cursor[bot]` with `labels: none` and zero comments,
asking for a new first-class toolbar shape while the body itself says the logo
asset is TBD, a prerequisite that does not exist yet. Clause (e) is `issue-15`
above. Clauses (c) and (d) come straight from `references/evidence-guide.md`.

The final sentence about closed linked PRs exists for a different reason:
reliability rather than correctness. Clause (e) was already right, but it
required the grader to infer that two closed PRs on a still-open issue must
have been unmerged. On that inference the same bundle graded `accept` in one
run and `reject` in the next, with no change to my rubric in between. Stating
the inference in the rubric removed the judgment step instead of adding
strictness.

Clause (b) also does real work on the accept side. `issue-09` is
`type::feature` and gold-accept, so a feature request is not automatically out
of scope. It passes because it is triaged: `good first issue`,
`source::community`, `backlog`, opened by a MEMBER. `issue-20` fails because
nobody has touched it. The distinction the check draws is endorsement, not
whether the work is a feature.

**Trade-offs**

`bounded-scope` gives up issues whose real scope is invisible in the bundle,
and it gives up untriaged good ideas.

The clean miss I accept is clause (b). It will reject a genuinely small,
genuinely good feature request that simply has not been triaged yet, the sort
of one-function addition filed by a careful outsider on a project whose
maintainers are slow to label. My check cannot distinguish that from
`issue-20`, and it rejects both. I am taking that trade deliberately. As a
first contributor, the cost of building something nobody agreed to is a wasted
PR, while the cost of skipping a good untriaged issue is that I pick a
different one from the same tracker.

The check is also blind in the other direction. It reads thread length,
labels, and linked PRs, all of which are surface evidence. An issue with a
short thread, no prior attempts, and clean labels passes even if the fix
actually touches half the codebase, unless a maintainer happened to say so in
the thread. Clause (d) only fires when someone wrote it down.

On whether rewriting it broke anything else: it did not, and here is how I
know. After the rewrite I re-ran nine bundles with
`--only issue-01,issue-06,issue-09,issue-14,issue-16,issue-19,issue-10,issue-20,issue-05`
and got 9/9. Those nine were not arbitrary. Six were the issues my rubric had
been getting wrong. The other three were the gold-rejects that the rewrite had
left resting on `bounded-scope` alone (`issue-10`, `issue-20` and `issue-05`),
because I had just demoted `maintainer-responds` to `preferred` and relaxed
`repo-active`, which removed the second required failure those three had been
leaning on. All six flipped to agree and all three still rejected.

When I later added clause (e), I re-ran a different nine: `issue-15` plus all
eight accept-gold issues, and got 8/9. That set was chosen on the logic that
adding a disqualifier can only endanger accepts, since a new failure condition
cannot unmake a reject, so the eight accepts were the complete population at
risk. All eight were preserved. The full run after it came back 20/20 with
every category full.

---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**

**1. Fit to my interests and to the time available.**

I picked #6, "Hybrid retriever skips keyword indexing and normalizes BM25
scores per batch". The issue reports two related defects in
`rag/retriever/hybrid.py`: `HybridRetriever.retrieve` fetches the
collection's chunks but never passes them to `keyword_searcher.index()`, so
the keyword half of the blend contributes nothing, and each side is
normalized by its own batch's top score, so the best keyword match scales to
1.0 even when it is weak.

That second defect is the reason I chose it. Per-batch max normalization is a
scoring bug you cannot see by looking at output, because the numbers always
look reasonable; you have to reason about what the score is supposed to mean
before you can say the blend is wrong. That is the "correctness is argued
rather than eyeballed" work I said I wanted, and it is genuine information
retrieval mathematics rather than application glue. It is Python, it is one
named file, and it reproduces locally with no GPU or hardware.

The issue estimates 4 to 6 hours.
[AYAN: say what you actually have available before Unit 2.]

**2. What the verdict identified correctly, and what I weighed that the rubric
could not.**

All five required checks passed and each was right. The repo is live, with its
newest commit on 2026-09-16, four days before I ran the skill. Nobody is
assigned, there are no linked PRs, and in fact the repository has no open pull
requests at all. The contribution policy in `docs/CONTRIBUTING.md` sets
process requirements only, with no restriction on AI-assisted work.

Two preferred checks did not pass, and I went ahead anyway. `labeled-friendly`
failed outright: the labels are `docs`, `rag`, `tier-2`, with no `good first
issue` or newcomer equivalent. `maintainer-responds` graded `unclear`, because
every issue in the repository was opened on 2026-09-10 or later and my check
only counts samples opened at least 14 days before the grading date, so no
eligible sample exists yet. Neither can change a verdict by design, and this
is the case that design was written for: they told me the issue is less
newcomer-friendly than the alternatives without pretending that made it a bad
issue.

What the rubric could not weigh is why I chose this one over the other two it
also accepted. My rubric accepted #68, #6 and #64, so the verdict did not pick
for me. I first chose #68, the `ZeroDivisionError` in keyword search, and then
changed my mind after reading its thread: a classmate had already reproduced
the crash on `main`, posted the traceback and a control run, and published the
exact fix they intended to write, down to which test marker to remove. Under
the Path Review house rule that does not block me, and the credit attaches to
the pull request I open rather than to whether it merges. But the entire fix
is a five-line empty-corpus guard, and writing it behind someone who has
already published the plan is not the rep I am after. I turned #64 down for a
different reason: it is tier-1 and the fastest of the three, but the whole fix
is editing query terms in one test fixture, which teaches me the PR mechanics
and nothing else.

None of that reasoning belongs in the rubric. Fit is supposed to rank what the
rubric accepts, not decide it, and here it did exactly that: the rubric told me
all three were safe, and I chose among them on grounds the checks do not
measure.

**3. Anticipated difficulty claiming it.**

Claiming should be uncomplicated. The issue has no assignee, no linked PR, and
zero comments, so nobody is ahead of me and there is no thread to read into. I
have not commented on it; choosing is not claiming.

The difficulty I expect is in the work rather than the claim, and it is
specific. The first defect is clear, since the missing `keyword_searcher.index()`
call is a straightforward omission. The second is not fully specified: the
issue says normalizing each side by its own batch's top score is wrong, but it
does not say what the correct normalization should be, and that is a real
decision rather than a mechanical fix. I may need to ask the maintainer what
they intend before writing it, which is itself the contribution-loop practice I
wanted. It is also `tier-2` with no newcomer label, so I am accepting a larger
surface than either alternative offered.
[AYAN: add anything else you are genuinely unsure about, such as the review
turnaround or reproducing the blend behaviour locally.]

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
