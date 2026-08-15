# Course Skills

Agent skills for building a real course — the craft, as markdown files you can read in 90 seconds and edit yourself.

Thirteen skills that take you from "I want to teach this" to a course with an outline, sources, lessons, slides, labs and questions. Each is one `SKILL.md`. No DSL, no orchestrator, nothing to install.

## Install

These follow the [Agent Skills standard](https://agentskills.io/specification) — `name` and `description` in the frontmatter, nothing else required — so the same files work in Claude Code, OpenCode and Pi. Only the folder and the invocation differ.

```bash
git clone https://github.com/flaviogoncalves/course-skills ~/course-skills
```

Then copy them where your agent looks:

**Claude Code**

```bash
mkdir -p ~/.claude/skills && cp -r ~/course-skills/skills/* ~/.claude/skills/
```

Invoke by name: `/course-grill`.

**OpenCode**

Already done, if you ran the Claude Code line — OpenCode reads `~/.claude/skills/` too. Otherwise pick either of its own:

```bash
mkdir -p ~/.config/opencode/skills && cp -r ~/course-skills/skills/* ~/.config/opencode/skills/
```

OpenCode has no slash form for skills; the agent calls its `skill` tool when a task matches. Ask for one by name — *"use course-grill to interview me"* — and it will. Skills are on by default.

**Pi**

```bash
mkdir -p ~/.agents/skills && cp -r ~/course-skills/skills/* ~/.agents/skills/
```

Invoke with `/skill:course-grill`. `~/.pi/agent/skills/` works too.

**All three at once.** `~/.agents/skills/` is read by OpenCode *and* Pi, and `~/.claude/skills/` by Claude Code *and* OpenCode, so two copies cover everything:

```bash
mkdir -p ~/.agents/skills ~/.claude/skills
cp -r ~/course-skills/skills/* ~/.agents/skills/
cp -r ~/course-skills/skills/* ~/.claude/skills/
```

To update, `git pull` and re-copy. Or use `ln -s` instead of `cp -r`, and a pull updates every harness at once — Claude Code's loader takes a symlink where it takes a directory, and the other two resolve the file through it. Edit skills at the clone, not through the link: Claude Code refuses to write through a symlink, by design.

**A newly installed skill appears in the next session, not the current one.** The list is built at startup. If you just installed and the name is not recognised, restart before assuming the path is wrong.

### Per project instead of globally

Same files, inside the course repo. Useful when you have edited a rule for one specific course.

| Harness | Project folder | Invoke |
|---|---|---|
| Claude Code | `.claude/skills/` | `/course-grill` |
| OpenCode | `.opencode/skills/`, `.claude/skills/` or `.agents/skills/` | by name, in prose |
| Pi | `.agents/skills/` or `.pi/skills/` | `/skill:course-grill` |

`.agents/skills/` is the one folder OpenCode and Pi both read. Pi also walks up from the working directory to the git root, so a skill at the repo root reaches every subfolder.

### Any other agent, or none

They are plain markdown with a two-field header. Paste the file into whatever you use, or read it yourself — every skill ends in a checklist, and nothing here needs an agent to be useful.

## One repo per course

That is the default, and the skills assume it: they write to `course/` at a fixed path, so two courses in one repository collide on the same `glossary.md` and `outline.md`. The collision is silent, and glossary ownership is per course, so it corrupts rather than errors.

It also makes the git history mean something — you can see when the outline changed and read why.

```bash
mkdir my-course && cd my-course && git init
```

**The exception is a course line.** If you publish several courses under one brand, the visual system is shared and the vocabulary often overlaps. Copying `design.md` into five repositories is five places to drift. For that case:

```
courses/
  brand/design.md          built once, by build-design
  livekit-for-voip/course/ contract, glossary, outline, lessons
  asterisk-basics/course/  its own everything
```

Keep `course/` per course even here. Share the design; never share the glossary — two courses teaching adjacent subjects will define the same word differently, and that is correct.

## Start here

Inside the course repo, in order:

```
course-grill          interview yourself, or the expert, until there is a contract
course-outline        turn the contract into a lesson sequence
build-design          settle colour, type and contrast before any slide exists
lesson-references     per lesson — find sources, reject the ones without authority
lesson-content        per lesson — write it, grounded in those sources
slide-generation      per lesson — slides plus the spoken narration
lab-generator         per practical lesson — one milestone, every step checkable
question-generation   per lesson — questions whose wrong answers are real mistakes
narration-audio       per lesson — the written narration becomes audio, last of all
course-review         the whole course at once, before you record anything
```

Later, and repeatedly:

```
course-maintenance    what changed since you recorded, and which lessons rotted
```

`course-domain-model` and `course-eval` are not steps — the first is the vocabulary discipline the others follow, the second judges any artifact against the checklist of the skill that made it.

## The model

A course lives in a folder, and each skill writes a file the next one reads:

```
course/
  contract.md      course-grill      promise, audience, scope, prerequisites, labs
  glossary.md      course-grill      the course's words, beside the audience's
  decisions/       course-grill      the few choices worth a record
  outline.md       course-outline    the lesson sequence
  design.md        build-design      the visual system
  narration.md     narration-audio   voice, speed, format — settings, never keys
  lessons/…                          references, content, slides, labs, questions
```

These files are written **during** the interview, term by term, not produced at the end. That is what makes the rest reproducible: regenerate a lesson six months later and it still obeys the same promise, the same words and the same refusals.

Nothing here is a framework. If a skill's rule is wrong for your course, edit the markdown — that is the intended way to use it.

## The glossary is the piece people underestimate

It is not a definitions list. It holds **the audience's word beside the course's word**, and that mismatch is how you find the lesson a generated outline always skips.

When several of the audience's words collapse into one of yours — *channel*, *conference* → *room* — you have found a concept the course must teach explicitly, before first use. That is the missing lesson, every time.

It also carries something a codebase glossary has no reason to: **which lesson introduces each term**. Code has no reading order, so a definition suffices. A course is consumed front to back, so a term is owned by a lesson, and no lesson may assume a term owned by a later one.

That turns vocabulary into a dependency you can check — and it catches the defect nobody ever reports. A student who meets a word in lesson 3 that gets explained in lesson 7 does not write in to complain. They conclude the course is above them, and leave.

## Skills

| Skill | Reach for it when |
|---|---|
| `course-grill` | Starting anything. Interviews until there is a contract: promise, audience and what they already know, misconceptions, scope, prerequisites, lab plan. |
| `course-domain-model` | Deciding what earns a glossary entry and which lesson owns it. Drives the glossary the rest read. |
| `course-outline` | You have a contract and need a lesson sequence — a progression of capability, with the opening generated outlines skip: welcome, problem, mental model, environment. |
| `build-design` | Before any slide exists. Colour roles, type scale, shape and contrast rules, written so a generator can obey them literally. |
| `lesson-references` | Per lesson. Sources found from *that lesson's* title and objectives, each passing an authority test. Never a course-wide pool. |
| `lesson-content` | Per lesson, once it has sources. Concrete claims, counter-examples, no packaging — and it refuses to write a lesson with nothing to stand on. |
| `slide-generation` | Per lesson, after the content. Slides plus narration: the slide carries the skeleton, the narration teaches. |
| `lab-generator` | Per practical lesson. One milestone, starting from the state the last lab left, every step with a check. |
| `question-generation` | Per lesson. Questions tied to objectives, with distractors drawn from mistakes this audience actually makes. |
| `narration-audio` | The narration text is settled and you want audio. One voice for the course, pronunciation from the glossary, resumable per chunk. |
| `course-eval` | Judging one artifact. Compliance fails; quality scores. Reads the checklist of whichever skill produced it. |
| `course-review` | The lessons exist and you are about to record. Judges the course, not the artifacts. |
| `course-maintenance` | The course is published and the subject moved. Audits for rot using each lesson's own references as the tripwire. |

## Why these exist

Each prevents a failure that is invisible until someone reads the finished course.

**The outline opens in the wrong place.** No welcome, no basics, straight into the subject — often because a rule like "deliver a win by lesson 3" gets applied to a 27-lesson course, leaving one slot for everything foundational.

**The references are almost right.** A course-level pool of eight links spread across twenty-five lessons is set-partitioning under pressure to fill slots. Every lesson ends up with a plausible, mis-assigned source — and if references feed content generation, that becomes the material the lesson is written from.

**A lesson gets written with no sources at all.** Indistinguishable, on the page, from one written from documentation. That is what quietly halves a course: some lessons anchored in real material, the rest fluent invention, nothing marking which is which.

**The slides are walls of text.** Written as a document rather than visual support, so the student chooses between reading and listening and loses both — and the last block renders cut off, because nothing summed the heights before adding it.

**The labs contradict each other.** Written in isolation, one tells the student to rebuild from scratch what the previous one made. Patching that afterwards by reading the earlier labs is archaeology; deciding the build order up front is not.

**The questions test whether you read the page.** Answerable by pattern-matching the lesson's wording, with three obviously wrong options. It grades cleanly and measures nothing.

**Every lesson passes and the course still fails.** The promise is never delivered, one concept is taught twice, another is used but never introduced. None of it is visible while reading a single lesson.

**The course was right when you recorded it.** Then the tool shipped a major version, a flag was renamed, and a sentence you were confident about became false. Nothing tells you — students hit it and quietly conclude the course is out of date.

Each skill states the failure it prevents, because a rule whose reason is forgotten is the first one dropped.

## Status

The rules here come from generating real courses and watching them break. The **skill format is new**, though: these were distilled from a production pipeline, not yet hardened as standalone skills in a clean terminal. Expect to find places where something obvious to the author was left implicit.

Each skill ends with a *Known rough edges* section naming what it does not solve. Those are honest, not modest — reordering lessons quietly breaks both glossary ownership and lab inheritance, and nothing in here checks it for you.

## What is not here

**Course-level topic research.** Deliberately absent. A general research pass produces a pool of references, and a pool becomes a distribution — the exact failure `lesson-references` exists to prevent.

## Contributing

A skill earns its place by preventing a failure you can name. If a rule here cost you a bad course to learn, say so in the text — the reason is the part that makes it stick, and the first thing dropped when it goes missing.

Issues and pull requests welcome, especially reports of a rule that did not survive contact with a real course.

## License

MIT.
