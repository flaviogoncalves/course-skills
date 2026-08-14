# Course Skills

Agent skills for building a real course — the craft, as markdown files you can read in 90 seconds and edit yourself.

Each skill is one `SKILL.md`. No DSL, no orchestrator, no package to install. Drop them in `.claude/skills/` and invoke them, or read them as a checklist and do the work by hand.

## The model

A course lives in a folder, and each skill writes a file the next one reads:

```
course/
  contract.md      course-grill      the interview with the expert
  outline.md       course-outline    the lesson sequence
  lessons/…                          content, labs, references
```

The contract is the file that makes the rest reproducible. Regenerate a lesson six months later and it still obeys the same promise and the same refusals.

## Skills

| Skill | What it does |
|---|---|
| `course-grill` | Interviews the expert until there is a contract: promise, audience and what they already know, misconceptions, what is out of scope, the lab plan. Run this first. |
| `course-outline` | Turns the contract into a progression of capability — and enforces the opening that generated outlines skip: welcome, problem, mental model, environment. |
| `lesson-references` | Finds sources for **one** lesson, from that lesson's own title and objectives, and rejects anything that fails an authority test. |

## Why these exist

They are the parts that generators get wrong in ways that are invisible until someone reads the finished course.

**The outline opens in the wrong place.** No welcome, no basics, straight into the subject. Usually because a rule like "deliver a concrete win by lesson 3" is applied to a 27-lesson course, leaving one slot for everything foundational.

**The references are almost right.** A course-level pool of eight links distributed across twenty-five lessons produces a plausible, mis-assigned source on every lesson — and if references feed content generation, that becomes the material the lesson is written from.

**The labs contradict each other.** Written in isolation, one tells the student to rebuild from scratch what the previous one made. Patching this afterwards by reading the earlier labs is archaeology; deciding the build order up front is not.

Each skill states the failure it prevents, because a rule whose reason is forgotten is the first one dropped.

## Contributing

A skill earns its place by surviving real use. If a rule here cost you a bad course to learn, say so in the text — the reason is the part that makes it stick.

## License

MIT.
