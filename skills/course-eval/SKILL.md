---
name: course-eval
description: Judge a course artifact — outline, lesson, slides, lab or questions — against the contract and against the checklist of the skill that produced it. Separates contract violations, which fail, from quality, which is scored. Use after generating, and before generating the next thing downstream.
---

# Course Eval

Judge one artifact. Say what to change.

Read `course/contract.md` and `course/glossary.md`, then read **the skill that produced the artifact** — its "It's working if" section and its final checklist are your rubric. Do not invent criteria that the generating skill does not ask for, and do not restate them here; if a rule changed, it changed there, and this skill follows.

## Two verdicts, not one

Most evaluation goes wrong by mixing these into a single number.

**Compliance is binary.** The contract's refusals, the glossary's ownership rule, the declared prerequisites, the milestone order, and grounding: a lesson written with no sources and no declared exit is a fail, not a low score. A violation is a fail, no matter how good the rest is — a beautiful lesson teaching something the course promised not to cover is worse than a mediocre one that stayed inside the lines, because the first breaks a promise the student was given.

**Quality is scored.** How well it does what it was supposed to do.

Report them separately. An artifact can be fully compliant and weak, or excellent and disqualified.

## Cite or it did not happen

Every deduction quotes the artifact. Every compliance failure quotes both the artifact and the line of the contract or glossary it breaks.

A score with no quote is an opinion, and it is the thing that makes people stop trusting evaluation. It also stops you from grading a vibe: forcing yourself to find the sentence often reveals there is no defect, only a preference.

## Grade inflation is the default failure

Untethered judges give almost everything a high score, cluster their answers in a narrow band, and reward fluent prose over correct prose. Assume you will do this and work against it:

- Before scoring, list what is **wrong**. Score afterwards, from that list.
- A high score requires the artifact to have no findings, not merely to read well.
- If you cannot name a specific improvement, say the artifact is good — do not invent a finding to look rigorous. Fabricated criticism is as corrosive as inflation, and harder to spot.

The honest distribution has weak artifacts scoring badly. If everything you review scores similarly, you are measuring your own fluency, not the work.

## Judge only your slice

When several criteria apply, each judges its own thing and stays out of the others. A lesson can have excellent prose and a bad example; that is high on one criterion and low on another, not a blended middling score on both.

Never penalise the same defect twice under different names. Double-counting is what turns a single flaw into a failing artifact and makes the scores unusable for deciding what to fix first.

## What matters per artifact

The generating skill carries the rubric. These are the things easiest to miss when judging each one:

**Outline.** Does the sequence hold, lesson by lesson, given only what came before? Is there a lesson that owns each concept the audience gets wrong? Did anything from the out-of-scope list become a lesson?

**Lesson content.** Is it grounded — could you trace each claim to a source, or is it fluent invention? Check the sources exist *before* judging the prose: an ungrounded lesson that reads beautifully is the single most dangerous artifact in a course, because every review mechanism except this check will pass it. Fluency is exactly what an LLM judge over-rewards, so read for *anchors*: numbers, commands, named failures.

**Slides.** Two checks that the design rubric will not catch. Does the deck still represent the lesson it came from, or did it drift into a different emphasis — text is written first, so slides can quietly become a different course. And does the narration add to the slide rather than reading it aloud?

**Labs.** Does it start from the state the previous lab leaves? Does every step have a check? Ignore how it reads and ask whether you could follow it on a clean machine.

**Questions.** Could someone who understood but did not memorise the wording pass? Is each distractor a mistake a real person makes?

## Output

For each finding: where it is, what is wrong, and what to do about it. Ordered by what to fix first.

An evaluation that reports a score and no action is a number nobody can use. The point is the next edit, not the grade.

## It's working if

- Compliance failures are reported separately from quality, and one violation is enough to fail
- Every finding quotes the artifact
- Weak artifacts get low scores, and the range across a course is wide
- The same defect is never counted under two criteria
- Someone reading your output knows what to change first without re-reading the artifact
- You sometimes report no findings, and do not manufacture one

## Known rough edges

**A judge sharing the generator's blind spots misses the same things.** If both work from the same instructions, what the instructions never mention is invisible to both. The defects most likely to survive are the ones nobody wrote a rule about.

**Scores are not comparable across models or across prompt versions.** Changing either resets the baseline, so a course scored before a rule changed cannot be compared with one scored after. Record what produced the score alongside it.

**No calibration against real students.** Everything here is judged by proxy. A lesson that scores well and confuses learners is a case this skill cannot detect, and the only fix is putting it in front of people.
