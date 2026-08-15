---
name: build-design
description: Build the visual system for a course before any slide exists — colour roles, type scale, shape and the contrast rules — as a design.md following Material Design's token vocabulary. Run before slide-generation; the slide skill reads its output.
---

# Build Design

Run this **before** any slide is made. Write the result to `course/design.md`.

Without it, every slide invents its own colours and sizes, and the deck reads as a pile of screens rather than one course. Worse, the decisions that matter most — is this text readable on that image, does this accent survive a projector — get made implicitly, one slide at a time, by whoever is generating.

Use Material Design's vocabulary. Not because slides are Android, but because it is a token system that already names the hard parts: every foreground colour is defined *against* a background, so unreadable pairs are hard to write by accident.

## What you need from the creator

Ask, but do not stall on it — most of this can be derived and confirmed.

- **The logo**, and whether it has a dark and a light version
- **Existing brand colours**, if any, as hex
- **Where it will be shown**: a projector in a lit room, a laptop screen, an embedded player. This changes contrast more than taste does.
- **What the brand must not look like** — often a competitor, or a house style they are moving away from

If there is no brand yet, derive one from the subject and audience, and say in the file that it was derived rather than given.

## Colour: roles, not a palette

Do not write "the brand colour is #C6FF3D". Write the **role pairs**. Each foreground is defined against the surface it sits on, and both are named.

```
primary            / on-primary
primary-container  / on-primary-container
secondary          / on-secondary
surface            / on-surface
surface-variant    / on-surface-variant
error              / on-error
outline
scrim
```

A palette lets someone put the accent on the accent. Role pairs make that a naming error.

**Every pair carries its measured contrast ratio.** Body text needs **4.5:1**; large text (24px, or 18.7px bold) and UI edges need **3:1**. Write the number next to the pair. A pair you did not measure is a pair that will fail on a projector.

Measure it, do not estimate it. For each colour, convert every channel to a 0–1 fraction, linearise it, then take the weighted sum:

```
c' = c/255
linear(c) = c' <= 0.03928 ? c'/12.92 : ((c' + 0.055)/1.055) ** 2.4
L = 0.2126·linear(R) + 0.7152·linear(G) + 0.0722·linear(B)

ratio = (L_lighter + 0.05) / (L_darker + 0.05)
```

The result runs from 1 (identical) to 21 (black on white). Green weighs nine times more than blue, which is why a blue that looks dark enough often is not.

Define the whole set for **light and dark**. Slides get shown in both, and a deck that only works dark will be presented in a bright room eventually.

**`scrim`** deserves its own line: it is the overlay that makes text survive on top of a photograph. Say how dark it is, and when it is required — any text over a full-bleed image, always. This is the one token that prevents the most common unreadable slide.

## Type scale

Material's five families, three sizes each. For slides you mostly need the top half; define all of it anyway so nothing improvises.

```
display  L / M / S    the one-line statement slide
headline L / M / S    slide titles
title    L / M / S    section labels, callout headers
body     L / M / S    bullets and paragraphs
label    L / M / S    captions, footnotes, code annotations
```

For each: font family, size, weight, line height, letter spacing.

State the **minimum body size**, and treat it as a hard floor. On a slide, text below about 18px is decoration — the person at the back cannot read it, and shrinking type to fit more content is how a slide becomes a document.

## Shape and spacing

Material's shape scale — none, extra-small, small, medium, large, extra-large, full — mapped to actual radii, and which components use which. One radius applied everywhere reads as a template; a scale reads as a system.

Spacing on a consistent step (4 or 8). Say the step and use multiples of it.

## What this brand does not do

The most useful section, and the one most often missing.

Write the explicit anti-patterns: the gradient it never uses, the place the accent colour must never appear, the stock-photo genre that is banned, the effect that belongs to a competitor. Rationing an accent is what makes it read as an accent — a rule of "use it only for the single most important element on the slide" does more for a deck than adding three more colours.

Every entry here should be something a generator would otherwise do by default.

## The logo

How it sits on light and on dark, the minimum clear space around it, the minimum size, and what to do when there is only a dark version and the surface is dark. If the answer is "invert it", say so; if the answer is "use the wordmark instead", say that.

## Output shape

`course/design.md`, written so a generator can obey it without interpretation:

```markdown
# Design — <course>

## Colour roles
| role | light | dark | contrast vs its pair |
|---|---|---|---|
| primary / on-primary | #… / #… | #… / #… | 7.1:1 |
…

## Scrim
…how dark, and when required

## Type scale
| role | family | size | weight | line height |
…

## Shape
…radius scale and what uses what

## Spacing
…the step, and the multiples in use

## Logo
…on light, on dark, clear space, minimum size

## This brand never
- …
```

## It's working if

- A generator can apply the file literally, with no judgement calls left in it
- Every foreground names the surface it sits on, so an unreadable pair is a naming error rather than an accident
- No pair carries a ratio you did not compute
- Someone can build a slide in dark mode and in light mode without asking you anything
- The "never" list makes a generator's default output wrong, rather than describing taste

## Known rough edges

**A passing ratio is not legibility.** Hairline weights, tight tracking and thin strokes fail at 4.5:1 while satisfying it. The ratio catches the worst pairs; it does not certify the good ones.

**The room is not modelled.** A deck built for a laptop washes out on a projector in a lit hall, and nothing in a token file knows which you are in. If the course will be presented live, test one slide in the actual room before committing the palette.

**Nothing stops text landing on a busy image.** The scrim rule mitigates it; a photograph with high-frequency detail behind small type defeats the scrim and only looking catches it.

**Print and video are different mediums.** These tokens assume screens. Anything destined for PDF handouts or heavy compression needs its own check — thin type and low-contrast pairs are the first casualties of both.

## Before you finish

- [ ] Every colour is a **role**, and every foreground names the surface it sits on
- [ ] Every pair carries a measured contrast ratio, and none of them is below 4.5:1 for body
- [ ] Light and dark are both fully defined
- [ ] The scrim rule exists, and says *when it is mandatory*
- [ ] A minimum body size is stated as a floor
- [ ] The "never" list contains things a generator would otherwise do by default
- [ ] Nothing in the file requires taste to apply — a generator can follow it literally
