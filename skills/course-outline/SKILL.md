---
name: course-outline
description: Turn a course contract into a lesson sequence — a progression of capability, not a numbered syllabus. Enforces the opening (welcome, problem, mental model, environment) that generated outlines almost always skip. Use after course-grill, before writing any lesson.
---

# Course Outline

Read `course/contract.md` and `course/glossary.md` first. They outrank anything you find by searching: they came from the person who knows the audience. Where they disagree with research, the contract wins.

The glossary tells you which lesson must exist. When several of the audience's words collapse into one of the course's — or one splits into several — that mismatch is the mental-model lesson, and it goes before first use.

Write the result to `course/outline.md`.

## A syllabus is not an outline

A bad outline is a numbered list of subjects, in the order the subjects occurred to someone. The student crosses all of it and can do nothing.

A good one is a progression of capability: each lesson leaves the student able to do something new, and that ability is the input to the next.

## The order that works

**Welcome → Problem → Mental model → Environment → First win → Build → Choices → Diagnose → Operate**

**Lesson 1 is the welcome, and it teaches no content.** Who is teaching and why them, what the course delivers in concrete terms, who it is for and what they need first, and how the course is organised. Skipping this is the most visible failure to whoever is watching: the student lands in the middle of a subject not knowing where they are, how much is left, or whether the course is for them.

This is a genre convention, not a preference. People who buy an online course expect to be received before they are taught.

**Lesson 2 anchors on a real problem** the audience recognises: what this solves, and why what they already know is not enough.

**The mental model is a required lesson, before first use.** An inventory of components ("the seven parts of the system") is decorative and earns no lesson. But the central primitive — the unit where everything happens, the actor that replaces what the audience used to call something else — without it nothing later reads.

How to detect it: **when several misconceptions in the contract share a conceptual root, that root is the missing lesson.** Items of the form "assumes X works like the world they came from" are all the same item.

**If there is a practical environment, setting it up is a lesson, and it comes early.** Install, provision, create the account, and *verify it works* before moving on. Otherwise the student reaches the first hands-on lesson and stalls for a reason that is not the subject of the course.

Its content is already decided: the contract's **must have before lesson one** list, item by item, each with the check that proves it. Do not re-invent it, and do not soften the versions — "Docker 24+" stays "Docker 24+".

**The contract's milestone order is the order of the practical lessons.** It is a sequence because the artifact grows; reordering it silently breaks every lab after the point you moved. If the pedagogy demands a different order, that is a finding to take back to the expert, not a decision to make here.

**The first win is proportional to course length.** By lesson 3 in a 5–8 lesson course; within roughly the first 15% in a course of 20+. In a 27-lesson course, spending three lessons on foundation and delivering the win in the fourth is *correct*, not slow. A fixed "win by lesson 3" rule is what produces courses with no introduction and no basics.

**Comparison, cost, architecture and migration presuppose having built.** They never belong at the start, however high they appear on the expert's list.

**Test, lesson by lesson:** can the student follow this having seen only the ones before? If not, it is too early.

**And check it against the vocabulary.** Every glossary term names the lesson that introduces it; no lesson may assume a term owned by a later one. This is the mechanical half of the same test — see `course-domain-model`. When you find a term with no lesson to own it, you have found a missing lesson, not a missing definition.

## What earns a lesson

- **Core** — without it the rest does not stand. Its own lesson.
- **Important** — a fact or procedure needed to execute. Lives inside the lesson of the core it serves.
- **Worth knowing** — the student only needs to recognise it if they meet it. A mention. **Never a lesson.**

Watch for one misclassification: **a founding concept is not "worth knowing"**. What seems obvious to someone who has mastered the tool is exactly what the student lacks. If the audience makes practical mistakes for want of a concept, it is core.

## The expert's list is scope, not sequence

They will paste a list of objectives — in the order they thought of them, or copied from a syllabus. That tells you *what* to cover. **The order is yours to decide**, by dependency.

## Size

Each lesson is a 3–10 minute video (3–6 is the sweet spot). That forces **one or two objectives per lesson**. With three or more, either the video overruns or each objective becomes a mention instead of teaching. A topic too big for ten minutes is two lessons, not one dense one.

## Objectives

What the student will be able to *do*, measurable, Bloom verb first. Never "learn", "understand" or "know X" as an objective.

At least one objective at Apply or above per lesson — **except** the welcome and the mental-model lessons, where Remember/Understand is the right level. Forcing Apply there produces a fake-practical lesson: "deploy your first room" as the objective of a welcome video.

## Modules

Group consecutive lessons under a module with a title and a short explanatory text. **Never number the lessons or modules in their titles** — numbering is denormalised state: the moment you reorder, "3.2" lies and someone has to renumber by hand. Numbering is computed at render time, never stored.

## It's working if

- A stranger reading only the outline can say what the student will be able to do at the end
- Lesson 1 receives the student; lesson 2 gives them a reason; nothing teaches before either
- There is a lesson that owns each concept the audience currently gets wrong
- You can walk any lesson and name what earlier lesson supplied each thing it assumes
- Nothing from the contract's out-of-scope list appears, however naturally it fits
- Removing any lesson would break a later one — if one can go without consequence, it was padding

## Known rough edges

**It is tuned for self-paced courses people choose to buy.** The welcome lesson is a genre convention there. Mandatory compliance training, university modules and internal onboarding have different conventions, and applying this one to them will feel wrong to their audience.

**Lesson count arrives as a given.** Nothing here decides how many lessons a subject deserves; it distributes what it was told to. A target set badly upstream produces a well-shaped outline of the wrong size.

**Duration estimates are guesses.** How long a topic takes to teach depends on the audience's real starting point, which nobody knows until people take it. Treat the minutes as intent, not measurement.

## Before you write the file

- [ ] Lesson 1 is a welcome: instructor, delivery, audience, map — no content
- [ ] A practical course has an early set-up-and-verify lesson, and prerequisites are stated
- [ ] There is a mental-model lesson before first use — if several misconceptions share a root, that root is required
- [ ] A beginner knows, after the first lessons, what the thing **is** and how it is organised
- [ ] The first win arrives in proportion to course length
- [ ] Every lesson is followable having seen only the earlier ones
- [ ] Nothing from the contract's out-of-scope list became a lesson
- [ ] No lesson exists only because the topic appeared on the expert's list
- [ ] No lesson carries 3+ objectives, and no objective is generic
- [ ] Every glossary term has an owning lesson, and no lesson uses a term owned by a later one
