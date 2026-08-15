---
name: question-generation
description: Write the questions that check whether a lesson landed — each tied to an objective, with distractors drawn from the mistakes this audience actually makes. Use after the lesson content exists.
---

# Question Generation

Questions for one lesson. Read the lesson, its objectives, and `course/contract.md` — the misconceptions list there is the most valuable input you have, and it is explained below.

## Test the objective, not the text

The failure mode is a question answerable by pattern-matching the lesson's wording. It looks like a question, it grades cleanly, and it measures whether the student read attentively ten minutes ago. That is not what anyone wants to know.

> Weak: "According to the lesson, what does a room contain?"
> Strong: "A caller dials in and an agent joins. How many rooms exist?"

The second cannot be answered by remembering a sentence. It can only be answered by having the model.

Rule of thumb: **if the phrasing of the lesson changed, would the answer still be findable?** If not, you tested recall of prose.

## Every question serves a stated objective

Each objective in the lesson gets at least one question. Every question maps to one. A question serving no objective is either testing something the lesson did not teach — unfair — or revealing that the lesson taught something not in its objectives, which is a finding worth reporting rather than papering over.

Match the level, too. An objective at *apply* deserves a question that makes the student apply something; asking them to recall the definition of the thing they were supposed to apply grades the wrong skill and reports a false pass.

## Distractors come from the contract

This is where the chain pays off. **The misconceptions in the contract are the wrong answers.**

They were collected from an expert who watches this audience make the same mistakes every week. A distractor built from a real misconception does two things a made-up one cannot: it catches the student who holds that belief, and it makes the question diagnostic — you learn *which* wrong model they have, not just that they were wrong.

Good distractors are:

- the mistake this audience actually makes, coming from their neighbouring field
- a confusion with the adjacent concept — the glossary's "confused with" field, directly
- a rule applied correctly but out of its context, which is the most instructive miss of all

Bad distractors, all of which teach nothing:

- "None of the above" / "All of the above" — lazy, and rewards test technique over knowledge
- Obviously absurd options — they narrow four choices to two and flatter the student
- Options that differ from the correct one by something trivial, like a word order
- Options that give the answer away by *shape*: the longest one, the only one with a qualifier, the only grammatically matching one

Keep all options similar in length and form. The single most common giveaway in generated questions is a correct answer that is noticeably longer, because it carries the full explanation while the distractors are stubs.

## Explain the wrong answer, not just the right one

Feedback that only confirms the correct answer teaches the students who did not need it.

Where the learning happens is: *why the thing you picked is the mistake* — the belief behind it, named, and where it breaks. One or two sentences. Do not restate the question.

## Vary the position of the correct answer

Deliberately. Generators drift toward one slot, and a student who notices stops reading the options.

## How many, and how hard

Proportional to the lesson's objectives, not a fixed count. One or two per objective is usually right; a five-minute lesson with two objectives does not need eight questions.

Spread the difficulty. Every question at recall level tells you nothing beyond attendance; every question at diagnosis level fails students who did learn the lesson but have not practised yet.

## What not to ask

**Anything from the out-of-scope list.** The contract's refusals apply here too — testing something the course deliberately did not teach is the cruellest way to break trust.

**Anything using a term owned by a later lesson.** Same ownership rule as everywhere else: a question may only assume vocabulary introduced at or before its own lesson.

**Trick questions.** A question whose difficulty is in parsing the sentence rather than the subject measures reading speed. If the student who knows the material can get it wrong by reading normally, rewrite it.

## It's working if

- Every objective is probed, and every question maps to one
- Someone who understood the lesson but did not memorise its wording passes
- Each distractor is a mistake you could name a real person making
- The wrong-answer feedback names the belief behind the mistake
- Correct answers are not the longest option, and not always in the same place
- Nothing tests material the course said it would not cover

## Known rough edges

**No calibration.** Difficulty here is asserted, not measured — a question labelled hard is hard because it looked hard when written. Real difficulty only appears once many people have answered, and nothing in this skill closes that loop.

**Distractor reuse.** Draw all distractors from the same misconception list across many lessons and they start repeating. When that happens, the questions are still fair but they stop being diagnostic; vary by pulling from the glossary's confusions as well.
