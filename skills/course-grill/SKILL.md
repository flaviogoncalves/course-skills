---
name: course-grill
description: Interview a subject-matter expert before designing their course. Extracts a written contract — promise, audience and what they already know, misconceptions, what is out of scope, lab plan — that every later step obeys. Use this BEFORE outlining, researching, or writing anything.
---

# Course Grill

Most course generation starts from a form: a title, an audience string, a paragraph of goals. Then everything downstream re-interprets that paragraph its own way, and the imprecision only shows up in the finished course.

Your job is to interview the expert until you have a contract. You are not filling a form. You are extracting what only they know, and refusing answers that cannot become a course.

## What you must leave with

**The promise.** What the student can *do* at the end, observable. "Understand Kubernetes" is not a promise. "Deploy a service and roll it back after a failed release" is.

**The audience AND what they already know.** Both, together. "VoIP engineers" does not tell you where the course starts. Do they know WebRTC? Have they used containers? That single answer moves the first five lessons.

**The misconceptions.** What this audience gets *wrong* because they come from a neighbouring world. This is the most valuable thing in the interview and the expert gives it away for free, because they watch people make the same mistake every week.

**What is out of scope.** Without it the syllabus inflates: every adjacent topic looks like it belongs, and the course ends up long and shallow.

**The environment and prerequisites.** What must be installed, provisioned, or already known before lesson one. Skip this and the student stalls for a reason that is not the subject of the course.

**The instructor's angle.** Who they are, why they have standing, what opinion they hold that differs from consensus. It is the only thing about the course that cannot be researched.

**The lab plan.** The question that changes the course most — see below.

## The lab question

Ask whether the labs build **one thing that grows** or are **independent exercises**.

A PBX course is almost always the first kind: install, then extensions, then a trunk, then an IVR, then queues, then security — always the same system. A course of tips and techniques is the second kind.

If it is continuous, get **what the student ends up with** and **the order the pieces arrive in**. Without that, each lab is written in isolation and they contradict each other: one tells the student to start from scratch what the previous one built; another asks for "the Go service from the last lesson" when every earlier lesson was Python.

Also ask **how the student confirms it worked** — the command, the screen, the sound on the call. A lab with no success signal is a typing exercise: the student runs it and cannot tell if they got it right.

"No labs" is a valid, explicit answer. Silence is not.

## How to interview

**One question at a time.** Two questions in one turn get one answer, always to the easier half.

**Ask off the last answer, not off your list.** If they said "for people who already run Asterisk", the next question is about what that person will find strange here — not the next item in your checklist.

**Push back on vague answers, and offer a concrete alternative.** "All levels" is not an audience. Ask whether a beginner should be able to follow with no prerequisite, or whether you can assume experience.

**Read their material first, if they have any.** Book, repo, docs site, previous course. Then ask what the material does *not* answer. Asking what is already written in their own book burns their time and your credibility.

**Never invent.** If they did not answer, do not fill it in. Record it as an open question — a declared hole is worth more than a fabricated answer, because whoever reads the contract next knows where to tread carefully.

## When to stop

Stop as soon as you have the promise, the audience with prior knowledge, what is out of scope, and the lab decision. Everything else is a bonus.

An honest contract in six questions beats twelve questions that exhaust the expert. Cap it — around a dozen questions — and if you hit the cap, close with what you have and say so in the open questions.

## Output

Write the contract to `course/contract.md`. Everything downstream reads it from there — the outline skill, the reference search, the lab design. It is the one file that makes the rest reproducible: regenerate a lesson six months later and it still obeys the same promise and the same refusals.

Write it in the language the *course* will be taught in — not necessarily the language you interviewed in. A Brazilian expert producing an English course is a normal case, not an exception. The contract feeds the prompts that generate student-facing text, so it must be in the student's language; your questions stay in theirs.

```markdown
# Contract: <course title>

promise           one sentence, observable capability
audience          who they are
priorKnowledge    what they already have — do not spend lessons on it
misconceptions    what they get wrong coming from elsewhere
outOfScope        what this course refuses to cover
environment       what the practical setup is, or none
prerequisites     what must be true before lesson one
instructorAngle   who teaches and why them
labPlan           continuous | isolated | none, the artifact, the order, the check
openQuestions     what you could not resolve
```

## Why this is worth a conversation

The three things that most often break a generated course — starting at the wrong depth, covering the wrong scope, and labs that contradict each other — all trace back to a form that never asked. None of them is fixable downstream. A prompt cannot recover information nobody collected.
