# Scope: where to look, and who is looking

<!--
This file is the skill's field of view. The rubric (rubric.md) decides
whether an issue is GOOD; the scope decides which issues are candidates
at all, and whose hands the issue would land in. It applies in live mode
only: in eval mode the bundle is the whole world and this file is
ignored.

Two parts. Staff wrote the first; you write the second.
-->

## Where candidates come from

Only issues in the course's Path Review repository are candidates:

- Repo: `codepath/pathreview-ai301-fa26-s1` <!-- paste your section's repo from the Unit 1 Check-In page -->

Do not search, fetch, or grade issues from any other repository, however
promising. The wider GitHub comes later in the course; for now the field
is Path Review.

**Path Review house rule.** Path Review is a classroom, and your
classmates are not strangers. Ignore the usual claim signals here: other
students' claim comments (and there may be several on one issue) do not
block an issue, and finding some on the issue you want is normal. Claim
anyway: course credit attaches to the pull request you open, not to
whether it merges, so a shared issue costs nobody anything. Everything
else in the rubric applies as written.

## Your fit profile

<!-- YOU write this part: a few sentences about you. What languages and
tools you have actually used, what you want to get better at, anything
you want to avoid. The skill uses this only to RANK the issues your
rubric accepts, never to change a verdict: fit cannot rescue an issue
your rubric rejects, and cannot sink one it accepts. -->

I work primarily in Python: NumPy-heavy numerical and computer-vision code
written from scratch rather than leaning on high-level libraries, plus ML
pipelines, model evaluation, and agent/MCP tooling. I also read and write C++
and Rust, and I prefer systems-level and numerical code to application glue. I
am comfortable dropping into an unfamiliar codebase, reading its tests, and
reasoning about data flow. What I want more reps at is the contribution loop
itself on an established project: its test conventions, its review culture, and
the discipline of keeping a PR small and well-scoped. On the technical side, I
want work with real mathematical content, meaning numerical methods, statistics
and probability, or anything where correctness is argued rather than eyeballed.
I would rather not take issues that are mostly front-end or CSS work, or ones
whose fix cannot be verified without hardware or a heavyweight GPU environment I
cannot reproduce locally. A docs-only issue is acceptable, but I would rank a
small bug fix that comes with a test higher, and a bug in numerical or
algorithmic code highest of all.
