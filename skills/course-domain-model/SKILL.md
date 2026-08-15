---
name: course-domain-model
description: Build and maintain the course's vocabulary as a real artifact — each term, the word the audience uses for it today, and the lesson that owns its introduction. Drives course-grill's glossary writing; read by the outline, the lessons and the slides.
---

# Course Domain Model

A course teaches a vocabulary before it teaches anything else. Every later confusion is downstream of a word the student did not have, or had with a different meaning.

This skill is the discipline of writing that vocabulary down. `course-grill` runs the interview; this decides what gets recorded and how.

## Two things a course glossary must carry that a codebase glossary does not

**The audience's word for the same thing.** Your student is not empty — they arrive with a working vocabulary from a neighbouring field, and the overlap is where they get hurt. They already have a word for the thing; it means almost the same, and the "almost" is the whole lesson.

**The lesson that owns the term.** Code has no reading order — anyone can open any file. A course is consumed front to back, so a term is not merely defined, it is *introduced somewhere*, and everything before that point must not assume it.

That second one is what makes this a model rather than a list. It turns vocabulary into a dependency graph you can check.

## The term record

```markdown
## room
The unit where a session happens. Participants join a room; media flows inside it.

- **They call it**: channel, conference
- **Not the same because**: a room has no fixed capacity and no dial-in identity of its own
- **Introduced in**: lesson 3 — The mental model
- **Confused with**: session (a room can outlive one)
- **Said**: only when a speech engine gets it wrong — see `narration-audio`
```

Four fields earn their place always; the fifth appears only when needed.

**They call it** is the translation. When several of their words collapse into one of yours — or one of theirs splits into several of yours — you have found a concept the course must teach *explicitly*, not in passing. That mismatch is the mental-model lesson, and it is the lesson generated outlines skip every single time.

**Introduced in** is ownership. Exactly one lesson introduces a term. That lesson is allowed to spend time on it; every later lesson may use it bare; every earlier lesson must not use it at all, or must define it inline and accept that it is doing the owner's job badly.

**Confused with** catches the neighbour inside your own vocabulary — the pair the student will mix up. If you cannot name what a term is confused with, you may not need the record.

## Not every noun is a term

A glossary that records everything is a dictionary, and nobody reads it. A term earns a record if **any** of these hold:

- the audience already has a different word for it, and the difference matters
- it is used in more than one lesson, so its meaning has to hold still
- getting it wrong causes a practical mistake, not just an awkward sentence

If none holds, define it in the sentence where it appears and move on.

## The rule that makes it checkable

**A lesson may only assume terms owned by earlier lessons.**

This is mechanical, so check it mechanically rather than by reading. Scan each lesson for glossary terms; for each hit, compare the owner's position with the lesson's. Any term used before its owner is either a forward dependency — the outline is wrong — or a missing record.

Two legitimate exceptions, and both should be deliberate:

- The welcome lesson may name things it will not explain, as a map. "We will build a voice agent" before *agent* is defined is fine; the student is being shown the destination.
- A term may be *mentioned* to be deferred: "this is what people call X — we come back to it in the module on scaling."

Everything else is a defect, and it is the kind nobody reports. Students do not write in to say "you used a word I did not know"; they just conclude the course is above them.

## Write during, not after

Add a term the moment it resolves, not in a pass at the end. A glossary produced in one lump is a glossary nobody corrected while correcting was cheap — and if the session dies, it never existed.

## Challenge the drift

When someone uses a word the glossary already defines differently, say so. Do not silently accept a second meaning.

A course that calls one thing by two names, or one name for two things, teaches the student to distrust its precision — and they are right to.

The same applies across sessions. When you return to a course that already has a glossary, read it before adding to it. A term redefined in the second session, with lessons already built on the first meaning, is the most expensive kind of drift here.

## It's working if

- The glossary carries the audience's word beside the course's word, not just definitions
- Every term names exactly one owning lesson
- No lesson uses a term owned by a later lesson
- The glossary is short — it holds the words that matter, not every noun in the subject
- Adding a term sometimes changes the outline, because you found a concept with no lesson to own it
- It pushes back on a word you used, because the glossary already had it meaning something else

## Known rough edges

**Nothing enforces ownership unless you check it.** The rule is mechanical but the check is not automatic. Without it, forward references creep in exactly where they hurt most — early lessons written after the later ones.

**Reordering lessons invalidates ownership.** Move a lesson earlier and it may now use terms it no longer owns the right to. Re-run the check after any reorder; this is the most common way a good glossary goes quietly wrong.

**One curator.** Two people adding terms in parallel produce two meanings for the same word, and the conflict surfaces in a lesson, not in the file.
