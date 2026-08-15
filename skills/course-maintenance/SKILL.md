---
name: course-maintenance
description: Audit a published course for rot — what changed in the subject since you recorded, which lessons are now wrong, and what each fix costs. Use periodically, and whenever the tool you teach ships a major version.
---

# Course Maintenance

A course is not finished when it ships. The subject moves and the course does not, and the gap is invisible to you and obvious to the student.

This skill answers one question: **what changed since I recorded, and which lessons need redoing?**

Run the audit often. Fix in batches — the audit is cheap and the fix is not.

## The references are your tripwire

Every lesson has its own sources, recorded when it was written. That is what makes this mechanical rather than a memory exercise.

For each lesson: re-fetch its references and compare against what they said when the lesson was written.

- **Gone or moved** — a 404, or a redirect to something else. The page that grounded the lesson no longer exists.
- **Changed materially** — the section the lesson relied on now says something different.
- **Unchanged** — strong evidence the lesson is still true, and the cheapest possible answer.

This works only because references are per lesson. A course grounded in a shared pool cannot do it: nothing knows which source belonged to which lesson, so the whole course is either suspect or trusted, with no way to tell which lessons to look at.

Keep the *content* of what a reference said at writing time, not only its URL. A URL alone tells you the page still loads; it does not tell you the paragraph you taught from was rewritten.

## The other signals

**The version pins in the contract.** Prerequisites say "Docker 24 or newer". Check what the current version is, what is now the oldest supported, and whether anything in the labs behaves differently across that range.

**The vendor's changelog and deprecations.** Read for the interval since the course was recorded. Most entries do not matter; you are looking for renamed commands, changed defaults, and anything the course states as impossible that has since shipped.

**Student questions.** The best rot detector there is, and free. A cluster of questions on one lesson means that lesson rotted — students hit it before any audit does. If you have support threads or course comments, read them before running anything else here.

**Your own claims.** Search the course for absolute statements: "X is not supported", "this only works with Y", "there is no way to". Those age worst, because a vendor shipping the feature turns your confident sentence into a wrong one, and confident-and-wrong is what students quote back.

## Triage by what it does to the student

Not everything that changed matters. Sort by consequence, not by how recent it is.

**Broken** — the student cannot complete the step. Highest priority, and the easiest to find, because it fails loudly.

**Wrong** — the step completes and teaches something now false. Worse than broken in one way: nothing signals it. The student learns the outdated thing and carries it into their work.

**Stale** — it still works, but nobody would do it this way now. A judgment call, and the place where courses accumulate unnecessary re-recording.

**Cosmetic** — a button moved, a screen was restyled. Annoying, rarely worth the cascade.

A patch release almost never justifies touching a course. A major version usually does, and it usually justifies touching only a handful of lessons.

## What each fix costs

Same cascade as `course-review`, and it decides everything here:

- **Text edit** — a value, a flag, a sentence. Nothing downstream moves.
- **Regenerate the lesson** — slides and narration follow; recorded audio and video for that lesson are dead.
- **Re-record** — the expensive one, and it carries a hidden cost: a lesson re-recorded a year later sounds different. Different room, different microphone, different you. A course patched lesson by lesson over three years sounds patched.

That last point should change what you decide. Sometimes the honest answer is not "fix lesson 7" but "re-record the module", and sometimes it is "leave it and add a note".

**A dated note is a legitimate fix.** "As of version 21 this flag was renamed to `--foo`; the video shows the old one." It costs a text edit, it keeps the student unblocked, and it is far better than a lesson that is quietly wrong while you wait for time to re-record.

## Output

A table, one row per lesson, ordered by severity:

| Lesson | What changed | Severity | Evidence | Fix | Cost |
|---|---|---|---|---|---|

Evidence is a link and a quote — what the source says now versus what the lesson claims. A maintenance report without evidence turns into a re-recording list nobody trusts enough to act on.

Then two summaries: what you would do before the next student enrols, and what can wait for the next major version.

## It's working if

- Most lessons come back unchanged, with the reference check as the evidence
- Every finding quotes the source as it reads now, beside what the lesson says
- Severity is about what happens to the student, not about how new the change is
- Findings carry a cost, so a five-minute fix is not queued behind a re-record
- It sometimes recommends a dated note instead of re-recording
- A patch release produces no findings

## Known rough edges

**Silent behaviour change is undetectable here.** The documentation did not change, the tool did. Nothing in a reference diff catches a default that quietly moved — only running the labs does. Treat a hands-on course as something that must be re-run periodically, not just re-read.

**Student signals are the strongest input and this skill does not have them** unless you bring them. If you have support threads, feed them in; an audit without them is guessing at what actually hurts.

**Reference drift is a proxy, not proof.** A rewritten page may say the same thing in new words, and an unchanged page may sit beside a changed reality. It narrows where to look; it does not decide.

**Nothing tracks what you already decided to leave alone.** Re-running the audit surfaces the same accepted staleness every time, and the noise trains you to skim. Record the decisions you made, next to the course.
