---
name: course-grill
description: Interview a subject-matter expert about a course until you share one understanding of it, writing the vocabulary and the hard decisions into the repo as they resolve. Produces the contract every later step obeys. Use before outlining, researching, or writing anything.
---

# Course Grill

Interview the expert until there is a contract. You are not filling a form: you are extracting what only they know, and refusing answers that cannot become a course.

**This skill is stateful.** Other interviews leave the session in your head; this one leaves files on disk, and writes them *as things resolve* rather than batched at the end. That is the whole difference. An interview whose output only appears on the last turn loses everything if the session dies — and worse, the expert cannot see what you understood while correcting it is still cheap.

## The paper trail

Three things come out of a session, and they are not equal.

| What resolved | Where it lands |
| --- | --- |
| A term — what the course calls a thing, and what the audience calls it today | `course/glossary.md`, the moment it resolves |
| Promise, audience, scope, environment, labs | `course/contract.md`, updated as each part settles |
| A decision that is hard to reverse, surprising without context, and a real trade-off | `course/decisions/NNN-slug.md` |
| Everything else you agreed | The conversation, and nowhere else |

That last row catches people out. Most of what you discuss earns no file, deliberately. A session that produced only a sharper glossary worked.

## The glossary is the point

In a course, a glossary is not a definitions list. It is a **translation table**: the word the audience uses today beside the word this course will use.

```markdown
## room
The unit where a session happens.
The audience calls this a **channel** or a **conference** today. Not the same thing:
a room has no fixed capacity and no dial-in identity of its own.
```

The second half is what makes it worth writing, and it does two jobs.

**It finds the lesson that must exist.** When several of the audience's words collapse into one of the course's — or one splits into several — you have found a concept the course has to teach explicitly, before first use. That lesson is the one generated outlines skip, every time.

**It keeps every later step consistent.** The outline knows which lesson is required, the lesson content knows which word to use, the slides stop alternating between both. Without it, each step re-derives the vocabulary and they disagree.

Write a term the moment it resolves. Challenge the expert when they use a word the glossary already defines differently — a course that calls one thing by two names teaches the student to distrust it.

Keep it pure vocabulary: no procedure, no scope, no spec-like prose. Those belong in the contract.

## The contract

Update `course/contract.md` as each part settles, not at the end.

**The promise.** What the student can *do* at the end, observable. "Understand Kubernetes" is not a promise. "Deploy a service and roll it back after a failed release" is.

**The audience AND what they already know.** Both, together. "Backend engineers" does not tell you where the course starts — do they already deploy containers? "Small business owners" does not either — have they ever run a paid ad? That single answer moves the first five lessons.

**What is out of scope.** Without it the syllabus inflates: every adjacent topic looks like it belongs, and the course ends up long and shallow.

**The environment and prerequisites.** What must be installed, provisioned, or already known before lesson one. Skip it and the student stalls for a reason that is not the subject of the course.

**The instructor's angle.** Who they are, why they have standing, what opinion they hold that differs from consensus. The only thing about the course that cannot be researched.

**The lab plan.** Do the labs build **one thing that grows**, or are they **independent exercises**? Anything teaching a system is almost always the first: install it, add users, connect it outward, handle failure, secure it — the same instance, growing. A course of techniques is the second: each shot in a photography course stands alone.

If continuous, get what the student ends up with and the order the pieces arrive in. Without it, each lab is written in isolation and they contradict each other — one tells the student to rebuild from scratch what the last one made.

Also ask **how the student confirms it worked**. A lab with no success signal is a typing exercise: they run it and cannot tell if they got it right.

"No labs" is a valid, explicit answer. Silence is not.

## Decisions worth a file

A decision earns `course/decisions/` only if **all three** hold:

1. **Hard to reverse** — lessons will be built on it, and changing it later means rewriting several
2. **Surprising without context** — someone reading the outline cold would ask "why did they do it that way?"
3. **A real trade-off** — a competent instructor could have chosen otherwise, for good reasons

"The labs build one system across the whole course" qualifies: irreversible by lesson five, surprising to anyone expecting standalone exercises, and a genuine trade-off against letting students start anywhere.

"We teach the CLI before the GUI, against the vendor's own tutorial" qualifies too.

"We use British spelling" does not. Put it in the contract and move on.

Most sessions produce none. That is the design, not a failure.

## How to interview

**Read their material first.** Book, repo, docs site, previous course. Then ask what the material does *not* answer.

Anything the material can answer, answer by reading — do not ask. Asking what is written in their own book burns their time and your credibility, and it is the fastest way to lose an expert's patience.

**Ask in short rounds.** Two or three *related* questions, then stop and wait. Never mix unrelated topics in one round: the expert answers the easy one and the other silently disappears. Build the next round from what they just said, not from your checklist.

**Push back on vague answers, with a concrete alternative.** "All levels" is not an audience. Ask whether a beginner should follow with no prerequisite, or whether experience can be assumed.

**Never invent.** If they did not answer, record it as an open question in the contract. A declared hole is worth more than a fabricated answer, because whoever reads the contract next knows where to tread carefully.

## When to stop

Stop once you have the promise, the audience with prior knowledge, what is out of scope, and the lab decision. Everything else is a bonus.

An honest contract in six questions beats twelve that exhaust the expert. Cap it around a dozen; if you hit the cap, close with what you have and say so in the open questions.

## Language

Interview in the expert's language. Write the artifacts in the language the **course** will be taught in — they feed the prompts that generate student-facing text. An expert producing a course in a second language is a normal case, not an exception.

## It's working if

- `course/glossary.md` changes *during* the session, term by term, rather than appearing in one lump at the end
- The glossary carries the audience's word beside the course's word, not just definitions
- Questions the expert's own material can answer get answered by reading it
- You get few or no decision records, and the ones you get are ones you would hate to re-litigate at lesson twenty
- It challenges a word the expert used, because the glossary already defines it differently
- The expert tells you something you could not have researched

## Known rough edges

**Nothing re-checks the contract later.** No step verifies that the finished course still matches what was agreed. Scope creep in a lesson is invisible: nothing errors, the course just gets longer and shallower.

**A second session produces a second contract.** Nothing reconciles them. Re-running this on a course that already has one means you are editing, not interviewing — read the existing files first and say what changed.

**Large material eats the interview.** If the expert's book is long, reading it consumes the context the interview needs. Read selectively: the table of contents, and the chapters that overlap the course.

**Everything outside those three files is gone when the session ends.** If the conversation held decisions worth keeping, do not clear it — hand it straight to the next step in the same session.

## Where it fits

```
course-grill → course-outline → build-design → lesson-references → lesson-content → slide-generation
```

It comes before anything is planned. The contract and glossary are what let every later step stop guessing — and what let a lesson regenerated six months from now still obey the same promise and the same refusals.
