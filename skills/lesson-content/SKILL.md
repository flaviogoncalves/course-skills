---
name: lesson-content
description: Write the body of one lesson. Enforces concreteness, counter-examples, and grounding in real sources — and refuses the padding that makes generated lessons feel hollow. Use after the outline, once a lesson has a title and objectives.
---

# Lesson Content

Read `course/contract.md`, `course/glossary.md` and `course/outline.md` first. Write one lesson at a time.

Use the glossary's words exactly. If the audience calls the thing something else, say so once, the first time it appears — then use the course's word throughout. Alternating between the two teaches the student to distrust the course.

**You may only assume terms owned by earlier lessons.** If this lesson introduces a term, it spends the time to teach it; if it needs one owned by a later lesson, the outline is wrong — say so instead of quietly defining it here.

The lesson serves **its own objectives** — the one or two stated in the outline. Not the course's objectives, not the topic in general. If you find yourself writing something that serves neither objective, it belongs in another lesson or nowhere.

## Content only — no packaging

Generated lessons are recognisable by their packaging. Cut all of it:

- "In this lesson, we will see…" — the student already clicked; they know
- "As we saw earlier…" / "As we will see later…" — say the thing, not its position
- "It is important to note that…" — if it were not important you would not write it
- "In summary, we covered…" — a recap that adds nothing is a recap that costs attention
- Motivational filler about how powerful or revolutionary the topic is

Every sentence should carry information the student did not have before reading it. Packaging is the easiest thing for a model to produce and the first thing a reader skips.

## Concreteness: show, do not tell

**No abstract verb without an anchor.** "Optimises performance", "improves security", "facilitates integration" — each of those must arrive attached to a number, a command, a file, a before/after, or a named failure.

| Hollow | Anchored |
|---|---|
| "Caching improves performance" | "Cache the read: 50ms → 2ms" |
| "Configure security properly" | "Allow only your office IP range; everything else is refused at connect" |
| "Good lighting matters" | "Move the lamp to 45° and one metre back; the nose shadow disappears" |
| "Handle objections early" | "Ask about budget on the first call, before the demo, not after" |

If you cannot anchor a claim, you do not know it well enough to teach it — go back to the sources or mark it as a gap.

## Expand acronyms on first use

Every acronym gets its full form once, the first time it appears in the lesson. Even the ones that feel universal in the field: the student is here precisely because they are not yet fluent. After the first time, use the short form freely.

## Counter-examples are not optional

Boundaries teach as much as centres. A lesson that only shows the happy path leaves the student unable to recognise the wrong case.

For the main concept, include at least one of:

- **When NOT to use it** — the case where this technique is the wrong choice
- **What it is often confused with** — the neighbouring thing, and how to tell them apart
- **The failure it produces when misapplied** — the concrete symptom, not "it may cause problems"

The contract's `misconceptions` list is the best source for these. If the audience already believes something wrong, say it plainly and correct it — do not tiptoe.

## No references, no lesson

**Stop before writing if this lesson has no sources.** This is a gate, not advice.

A lesson written without sources is written from the model's memory, and it is indistinguishable — to you, to the reader, to any later review — from one written from documentation. That is the failure mode that quietly halves a course: some lessons anchored in real material, the rest fluent invention, and nothing anywhere marking which is which.

Zero references is sometimes the *correct* outcome of searching: the candidates were read and none had the authority to ground teaching. Correct, and still a stop. Three ways out, all deliberate:

1. **The expert supplies one.** Ask. They usually have it — the page they always send people to.
2. **Their own material is the source.** A book, a repo, a previous course is a reference. Cite it as one.
3. **The lesson is written from the instructor's own practice**, and *says so in the text*. An expert with twenty years of it is legitimate grounding, but it has to be declared: "in my experience, on this hardware" is honest, and it is a different claim from "the documentation states". Undeclared, the two are identical on the page and only one of them is true.

What you may not do is write it anyway and stay quiet.

## Grounded, or silent

Write from the lesson's references. Do not invent facts, numbers, version behaviour, command flags or names.

When the sources do not cover something the lesson needs, say so in the text — "the documentation does not specify X; verify against your version" — rather than filling the hole with something plausible. A declared gap is recoverable. A confident fabrication is not, and it is the failure that destroys trust in a generated course fastest.

## Respect the contract's refusals

Anything on the contract's out-of-scope list stays out, however naturally it comes up. If the course says "we do not teach the database — the student already runs one", then you connect to their database without teaching how to administer it, even when a paragraph about it would flow nicely.

Scope creep in a lesson is invisible: nothing errors, the lesson just gets longer and the course gets shallower.

## Continuity

The student has seen the earlier lessons. Do not re-explain what they already covered — reference it in one clause and move on. Re-teaching is the second most obvious tell of content written in isolation, after packaging.

Equally, do not depend on anything from a *later* lesson. If you need it, either the outline is wrong or you are writing the wrong lesson.

## Voice

Write like an experienced instructor talking to a competent adult. Not academic, not breathless, not a manual.

Second person for instructions ("you configure", not "one configures" or "the user must"). Present tense. Short sentences carrying one idea each. A technical term stays in the original language when a specialist in that field would say it that way in normal speech.

## Before you finish

- [ ] Every stated objective has a section that serves it
- [ ] No sentence is packaging
- [ ] No abstract claim without a number, command, example or named failure
- [ ] Every acronym expanded on first use
- [ ] At least one counter-example, boundary, or corrected misconception
- [ ] The lesson had sources before you started, or one of the three exits was taken deliberately
- [ ] Every fact traceable to a source; every gap declared instead of filled
- [ ] Nothing from the out-of-scope list crept in
- [ ] Nothing re-explains an earlier lesson or depends on a later one
