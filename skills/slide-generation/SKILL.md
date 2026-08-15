---
name: slide-generation
description: Turn one lesson into slides plus spoken narration. Enforces the split that makes slides work — the slide carries the skeleton, the narration carries the detail — and a height budget so nothing renders cut off. Use after the lesson content exists.
---

# Slide Generation

Slides for one lesson. Two outputs per slide: what is **seen**, and what is **said**.

Read `course/glossary.md` and `course/design.md` first. The glossary settles which word appears on the slide and in the narration; a slide that says one word while the narration says another reads as two courses.

From `design.md` you need — colour roles, type scale, the scrim rule, and the list of things this brand never does. If it does not exist, run `build-design` before this. Slides that each invent their own colours read as a pile of screens, not a course.

## The split that makes slides work

A slide is not a document. It is visual support for speech.

The student looks at the slide for five seconds and returns to listening. A wall of text forces them to choose between reading and listening, and they lose both.

**The slide shows the skeleton. The narration teaches.** Every time you are tempted to add a sentence to the slide, ask whether it belongs in the narration instead. It almost always does.

**The five-second test:** if the student glanced at this slide for five seconds and looked away, would they have got the main idea? If they must *read* each line to understand it, the slide has failed. Every element exists to be caught at a glance.

## Hard limits

Calibrate the exact numbers to your renderer, but keep the shape of these — they exist because each one has a matching failure.

| Item | Limit | The failure it prevents |
|---|---|---|
| Bullet | ~80 chars ideal, 140 hard cap | A full sentence with qualifiers |
| Bullets per slide | 3–4 (5 only for a genuine taxonomy) | Dumping everything into six |
| Blocks per slide | ≤ 4 | Bullets + code + callout + diagram all at once |
| Diagram nodes | ≤ 6 | An architecture chart nobody can read |
| Code | ≤ 8 lines, ≤ 60 chars per line | Pasting a whole file |
| Callout | one sentence | A paragraph in a box |
| Slides per lesson | proportional to objectives, not a fixed number | "About ten" regardless of content |

Bullets are noun phrases or verb-led and punchy — never a complete sentence with subject, verb, object and qualifier. One concept per bullet, never three joined by commas.

> Wrong: "Use a distributed cache to reduce latency on frequent queries that hit the database, especially on endpoints that read far more often than they write"
>
> Right: "Cache the hot reads" · "Latency: 50ms → 2ms" · "Only for data that rarely changes"

## The height budget

This is the rule that prevents the most visible defect: a slide that renders cut off at the bottom.

Give each element an approximate height, sum them, and check the total fits the usable area before adding one more. Rough costs for a 16:9 slide with roughly 540px under the header:

```
header (title + subtitle)      ~90px
short bullet                   ~32px
bullet that wraps to 2 lines   ~64px
code block, 6 lines           ~180px
one-sentence callout           ~80px
image                         ~280px
diagram                       ~300px
```

Stay under ~480px. The combinations that overflow almost every time: four or more wrapping bullets; bullets plus code plus callout together; an image alongside dense bullets; a diagram plus anything beyond the title.

**If the content does not fit, split it into two slides.** Two clear slides beat one crowded slide that gets cut. Splitting is not a failure — cramming is.

## Composition

Most slides are a vertical stack, and that is correct for sequential content. Reach for a different composition only when the relationship between the parts is **spatial**.

**Two columns.** The height of a two-column slide is the height of the *taller column*, not the sum — so this is real space, not decoration. Content that overflowed stacked will fit side by side.

Use it when the halves are genuine pairs: before and after, option A and option B, code on one side and the explanation on the other, a list beside a diagram.

Do not use it to cram more into a slide that was already full. If the two columns have nothing to do with each other, they are two slides.

**Full-bleed image.** One image fills the stage; a little text sits over it. The background image costs no vertical budget — it *is* the stage.

Good for an opening, a module transition, or a single strong statement. With more than a short line or two over it, it becomes an unreadable poster.

**Always apply the scrim** from `design.md` when text sits over an image. Light text on a light photograph disappears, and it disappears only on the projector, after you have shipped. Erring too dark is recoverable; erring illegible is not.

## Diagrams

Use one to show a *relationship* between three to six concepts: a flow with a decision, a protocol between actors, a state lifecycle, a type hierarchy.

A diagram is a concept map, not an architecture drawing. If it needs ten nodes and nested groups, it is the wrong tool — split it into two smaller diagrams or fall back to bullets.

When the lesson's concept has any relationship between two or more elements — order, dependency, choice, transformation — a diagram is probably better than bullets. The cost of a diagram that does not land is small; the cost of never drawing one that would have helped is silent and large.

## Narration is spoken, not written

The narration becomes audio. Write what you would **say**, not what you would write in a technical document.

One criterion: it must sound like a person explaining, not a file read aloud.

**Read it aloud in your head. If you stumbled, or pronounced a symbol, rewrite it.**

Avoid only what genuinely breaks audio:

- **Markdown formatting** — no bold asterisks, no backticks, no `[link](url)`. For emphasis use words: "this is the part that breaks", "pay attention here".
- **Inline lists or JSON** inside a sentence — a speech engine reads separators literally. Rewrite as prose.
- **Long code** pasted into the narration. Code lives on the slide, not in the speech.

Everything else — a command name, a file name, a flag, an acronym — can appear directly when it is natural in an instructor's sentence. Do not defensively rewrite `package.json` as "package dot json"; it sounds robotic, and the student is *looking at the slide* while listening.

## Do not repeat the slide in the narration

Reading the bullets aloud wastes both channels. The slide already said it.

The narration adds: why it matters, what happens if you get it wrong, the number behind the claim, the transition to the next idea. If your narration is the bullets in full sentences, you have written one channel twice and taught with neither.

## Before you finish each slide

- [ ] Would a five-second glance deliver the main idea?
- [ ] Bullets punchy, one concept each, within the cap?
- [ ] Blocks summed against the height budget — does it fit?
- [ ] Any diagram at six nodes or fewer?
- [ ] Narration free of markdown, inline lists, and pasted code?
- [ ] Narration adds something rather than reading the slide aloud?
- [ ] Did you split instead of cramming?
