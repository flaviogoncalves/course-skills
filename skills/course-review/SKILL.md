---
name: course-review
description: Review the whole course at once — does the arc deliver the promise, do the lessons connect, is anything taught twice or never. Catches what per-artifact evaluation structurally cannot. Use when the lessons exist, before recording or publishing.
---

# Course Review

`course-eval` judges one artifact at a time. Everything below is invisible at that granularity: twelve lessons can each pass and the course still fail.

This is the pass that catches "it reads like a collection of articles, not a course."

## What only shows at course level

**The promise is not delivered.** Walk the contract's promise and find the lesson where the student can actually do it. Often it is nowhere — the course covers every component and never assembles them. Each lesson was fine; the course does not keep its word.

**The same thing is taught twice.** Two lessons explaining one concept in different words, usually written weeks apart. Neither author knew. The student notices immediately and concludes nobody read the whole thing.

**Something is used but never taught.** The glossary's ownership rule catches terms; this catches the rest — a technique, a file, a habit that appears in lesson 8 as if settled and was never introduced.

**An objective has no lesson.** Walk the contract's promise and objectives against the outline. A course objective nothing serves is a promise quietly dropped.

**A lesson serves nothing.** The inverse, and more common: a lesson that exists because the topic came up. If you cannot name which course objective it serves, it is padding, however good it is.

**The weight is wrong.** Six lessons on setup and two on the thing people came for. Or one module with nine lessons beside one with two. Per lesson, each was reasonable.

**The difficulty spikes.** Not a ramp but a cliff — lessons 1 to 5 gentle, lesson 6 assuming three things at once. That is where students stop, and it is only visible in sequence.

**The example does not thread.** The running example changes between lessons, or the lab artifact does not actually grow monotonically — lesson 7 builds something lesson 9 does not use.

**The voice drifts.** Lesson 1 and lesson 12 read as different people, because they were written by the same model in different sessions. Register, sentence length, how much is assumed.

**It stops instead of ending.** The last lesson is just the last topic. A course ends by closing the arc it opened — a project, a synthesis, a decision framework, next steps. Not necessarily a capstone; something that says *finished*.

## How to read it

A whole course rarely fits in one context, so the method matters and you should say which passes you actually ran.

**Structural pass, from the contract and outline alone.** Coverage, orphans, weight, ordering, arc shape, ending. Cheap, and it finds the expensive defects — the ones that require a new lesson.

**Prose pass, in windows.** Redundancy, voice drift, threading of the example. Read titles, objectives and openings across everything; read a handful of lessons in full, chosen where the structural pass raised suspicion.

**Lab pass, in sequence.** Follow the artifact from milestone to milestone and check it grows without gaps or rebuilds.

If you could not hold enough to judge something, say so. A review that silently skipped the prose pass reads exactly like one that found no prose defects.

## Say what each finding costs

This is the part reviews usually miss, and it decides what gets fixed.

A course is a cascade. Change a lesson's content and its slides no longer match; regenerate the slides and the narration is stale; regenerate the narration and any recorded audio or video is worthless. **The narration is where real money burns.**

So mark every finding:

- **Text edit** — fix in place, nothing downstream moves
- **Regenerate the lesson** — slides, narration and video for that lesson follow
- **Change the outline** — a new or moved lesson, which shifts ownership of terms and the lab sequence, and can cascade across several lessons

Order findings by damage, but let the reader see cost beside it. A cheap fix for a real problem should be done today; an outline change three days before recording is a decision, not a chore.

## Do not re-review the parts

You will be tempted to note that a bullet is too long or a distractor is weak. That is `course-eval`'s job on a single artifact, and repeating it here buries the findings only this pass can produce.

If a per-artifact defect appears in *many* lessons, that is a course-level finding — report the pattern, not the instances.

## Output

The verdict first: does this course deliver the contract's promise, yes or no.

Then findings, each with where, what, why it matters at course level, and the cost band. Then what you did not check, and why.

## It's working if

- The first line answers whether the promise is delivered
- Every finding is one that could not be seen while reading a single lesson
- Findings carry a cost band, so the reader can decide what to fix before recording
- A pattern across many lessons is reported once, not twelve times
- The passes you could not run are named, rather than silently omitted
- You sometimes conclude the course is coherent, and say so plainly

## Known rough edges

**Context is the binding constraint.** The bigger the course, the more this becomes sampling rather than review — and sampling misses redundancy, which is precisely a pairwise property. Two lessons duplicate each other only if you happen to hold both.

**It runs too late to be cheap.** By the time the lessons exist, the expensive findings are outline findings, and fixing those wastes work already done. Running a structural pass right after the outline — before any lesson is written — catches most of them when they cost nothing.

**No student has seen it.** Coherence judged by reading is not coherence experienced by learning. A course that reviews well and loses people at lesson six is a case this cannot detect.
