---
name: narration-audio
description: Turn a lesson's written narration into audio with a text-to-speech service such as Fish Audio — one voice for the whole course, pronunciation decided once, resumable per chunk. Use last, after the slides and narration text are settled.
---

# Narration Audio

This is production, not writing. The rules for *writing* narration live in `slide-generation`: sounds like a person explaining, no markdown, no inline lists, does not read the slide aloud. If the text is not settled, stop and settle it — synthesising unsettled text is how you pay twice.

**Run this last.** Audio is the most expensive artifact in a course and the most brittle: change a lesson and its slides move, change the slides and this is dead. Everything upstream should be final.

## One voice, one setting, for the whole course

Pick once and record the choice next to the course, alongside the design:

```
voice        the id, and why — sample it against your own subject, not a demo script
speed        one value, course-wide
format       and sample rate, matching what your player expects
```

Consistency matters more here than the choice itself. A course where lesson 3 is slightly faster or noticeably brighter reads as careless, and the student cannot say why — they just trust it less. Sampling voices on a vendor's demo sentence tells you little; run a paragraph of *your* narration, with your technical terms in it.

If you clone a voice, the same rule applies harder: clone once, from clean audio, and reuse it. A second clone from a different session is a second voice.

## Pronunciation is decided once, in the glossary

Every course has terms a speech engine mangles: product names, acronyms that should be spelled out and acronyms that should not, foreign words, anything with a number in it.

Decide each one **once**, and keep it with the term in `course/glossary.md`. It belongs there for the same reason the audience's word does: the term already has a home, and a pronunciation list living somewhere else drifts from it.

```markdown
## SIP
Session Initiation Protocol.
- **Said**: "sip", as a word — not S-I-P
```

Two things worth checking before a full run: acronyms your audience says as a word rather than letter by letter, and product names that sound wrong in the course's language.

Do not defensively rewrite the narration text to force pronunciation. Turning `package.json` into "package dot jason" corrupts the written narration for every other use — captions, transcripts, the chapter — to fix one channel. Fix it where it is a pronunciation problem.

## Chunk by slide, never mid-sentence

One slide's narration is one request. That is the natural unit: it matches how the player uses the audio, it keeps each request small, and it makes failure cheap.

Never split inside a sentence. A speech engine handed half a sentence gives it a falling, final intonation, and the join sounds like two takes.

If a single slide's narration is too long for one request, split at a paragraph or a full stop — and listen to the join, because that is where seams are audible.

## Resume, never restart

A twenty-slide deck where call fourteen fails must continue from fourteen. Rerunning the whole deck costs the thirteen you already paid for, and does it every time the network hiccups.

So: write each chunk to disk as it succeeds, name files by slide, and skip what already exists unless explicitly asked to redo. Treat a run as resumable by default.

Report what failed and why. Silent partial output is the worst outcome — a lesson that is missing slide fourteen's audio and does not say so surfaces in front of a student.

## Listen before you ship

No automated check hears a mispronounced product name, a wrong emphasis, or a sentence that reads fine and sounds robotic.

Listen to the first lesson end to end before generating the rest. That one pass catches voice, speed, and the pronunciation misses that would otherwise repeat across every lesson in the course — which is exactly the error you do not want to find after paying for all of them.

After that, spot-check: the first and last slide of each lesson, plus any slide dense with technical terms.

## Cost and limits

Charged by the character, so a course is a real bill and a regenerated course is that bill again. A generous free tier makes experimenting cheap and misleads about the full run — sample on a free tier, budget for the real one.

Rate limits bite at course scale, not lesson scale. Generating twenty lessons back to back is where you meet them, so pace requests and treat a rate-limit error as retryable rather than fatal — unlike a rejected input, which will fail identically forever.

## It's working if

- One voice and one speed across every lesson, recorded somewhere, not chosen per run
- Pronunciations live beside their terms in the glossary, decided once
- A failed run resumes and does not re-pay for what succeeded
- Nothing partial ships silently
- You listened to a full lesson before generating the rest
- The narration text was not distorted to fix pronunciation

## Known rough edges

**Voice models change under you.** A provider updating a voice means audio generated next year does not match audio generated today. Regenerating one lesson into an old course can be audible. Record the voice id and the date, and prefer regenerating a whole module over a single lesson.

**Nothing here checks that the audio matches the slide it belongs to.** An off-by-one in chunking produces a deck where every narration is one slide ahead, and it is perfectly fluent audio — only listening catches it.

**Cloned voices carry consent and likeness questions** that are not technical. Clone your own voice, or someone who agreed in writing to this specific use.
