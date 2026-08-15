# Course Skills

Agent skills for building a real course — the craft, as markdown files you can read in 90 seconds and edit yourself.

Each skill is one `SKILL.md`. No DSL, no orchestrator, no package to install. Drop them in `.claude/skills/` and invoke them, or read them as a checklist and do the work by hand.

## The model

A course lives in a folder, and each skill writes a file the next one reads:

```
course/
  contract.md      course-grill      promise, audience, scope, labs
  glossary.md      course-grill      the course's words, beside the audience's
  decisions/       course-grill      the few choices worth a record
  outline.md       course-outline    the lesson sequence
  design.md        build-design      the visual system
  lessons/…                          content, labs, references
```

These files are written **during** the interview, term by term, not produced at the end. That is what makes the rest reproducible: regenerate a lesson six months later and it still obeys the same promise, the same words and the same refusals.

The glossary is the one people underestimate. It is not a definitions list — it holds the audience's word beside the course's word, and that mismatch is how you find the lesson a generated outline always skips.

It also carries something a codebase glossary has no reason to: **which lesson introduces each term**. Code has no reading order, so a definition is enough. A course is consumed front to back, so a term is owned by a lesson, and no lesson may assume a term owned by a later one. That turns vocabulary into a dependency you can check — and catches the defect nobody reports, where lesson 3 uses a word explained in lesson 7.

## Skills

| Skill | What it does |
|---|---|
| `course-domain-model` | The vocabulary discipline: each term, the word the audience uses for it today, and the lesson that owns its introduction. Drives the glossary the others read. |
| `course-grill` | Interviews the expert until there is a contract: promise, audience and what they already know, misconceptions, what is out of scope, the lab plan. Run this first. |
| `course-outline` | Turns the contract into a progression of capability — and enforces the opening that generated outlines skip: welcome, problem, mental model, environment. |
| `lesson-references` | Finds sources for **one** lesson, from that lesson's own title and objectives, and rejects anything that fails an authority test. |
| `lesson-content` | Writes the lesson body: concrete claims, counter-examples, grounded in real sources, no packaging. |
| `build-design` | Builds the visual system — colour roles, type scale, shape, contrast rules — as a `design.md` in Material Design's token vocabulary. Run before slides. |
| `slide-generation` | Turns a lesson into slides plus spoken narration — the slide carries the skeleton, the narration carries the detail. |
| `lab-generator` | Writes the hands-on lab for one milestone, starting where the previous lab ended, every step verifiable. |
| `question-generation` | Writes the questions that check whether the lesson landed, with distractors drawn from the mistakes this audience really makes. |

## Why these exist

They are the parts that generators get wrong in ways that are invisible until someone reads the finished course.

**The outline opens in the wrong place.** No welcome, no basics, straight into the subject. Usually because a rule like "deliver a concrete win by lesson 3" is applied to a 27-lesson course, leaving one slot for everything foundational.

**The references are almost right.** A course-level pool of eight links distributed across twenty-five lessons produces a plausible, mis-assigned source on every lesson — and if references feed content generation, that becomes the material the lesson is written from.

**The slides are walls of text.** Written as a document instead of visual support, so the student has to choose between reading and listening and loses both — and the last block renders cut off, because nothing summed the heights before adding it.

**The labs contradict each other.** Written in isolation, one tells the student to rebuild from scratch what the previous one made. Patching this afterwards by reading the earlier labs is archaeology; deciding the build order up front is not.

**The questions test whether you read the page.** Answerable by pattern-matching the lesson's wording, with three obviously wrong options — it grades cleanly and measures nothing.

Each skill states the failure it prevents, because a rule whose reason is forgotten is the first one dropped.

## Contributing

A skill earns its place by surviving real use. If a rule here cost you a bad course to learn, say so in the text — the reason is the part that makes it stick.

## License

MIT.
