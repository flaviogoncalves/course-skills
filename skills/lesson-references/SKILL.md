---
name: lesson-references
description: Find the reference material for ONE lesson — search from that lesson's own title and objectives, read candidates in full, and reject anything that fails an authority test. Use per lesson, never as a course-wide pool to distribute.
---

# Lesson References

Do this **per lesson**. The failure this skill exists to prevent is treating references as a course-level pool to hand out.

That failure is worth naming, because it looks reasonable: research the topic once, collect eight good links, then assign zero to three per lesson. With eight candidates and twenty-five slots, the model is doing set-partitioning under pressure to fill slots — it attaches the least-bad remaining link, and lessons that lose the lottery get nothing. Every lesson ends up with a plausible, almost-relevant source.

And the damage is not cosmetic. If your references become the grounding corpus for the lesson's content, a mis-assigned link does not just look wrong in a footer — it becomes the material the lesson is written from.

## Search from the lesson, not the course

Build the queries from **that lesson's own title and objectives**. Do not ask a model to invent queries first: whatever it invents may not contain the lesson's actual wording, which is the one thing that must be in the search.

Three queries are enough:

1. **The title**, anchored with a domain term if the title is ambiguous on its own. "Handling duplicates" could be anything; "handling duplicate webhook deliveries" is a search.
2. **The first objective**, stripped of Bloom boilerplate. "By the end the student will be able to apply an idempotency key" → "apply an idempotency key".
3. **The title again, restricted to the canonical documentation site** — see below.

Keep queries short, 3–10 words. Search engines degrade on long blobs. Only add the domain anchor when the text does not already carry a domain term, or you get redundant noise.

## Search the official site directly

In open web search, the deep documentation page that serves one lesson loses to the product homepage and to generic tutorials — both rank better on almost any query.

So run one query restricted to the canonical domain — the tool's documentation site, the regulator's site, the professional body, whatever the primary source is for this field. You can usually identify it from the course-level research: if five of eight topic references share a domain, that is it, and each lesson should hunt its own page inside it.

Never scope to a domain with a bad reputation signal — a content farm or SEO blog — or the technique becomes an amplifier for weak sources.

## Read before judging

Fetch the top candidates and read them **in full**, not the search snippet. A snippet cannot tell you whether a page substantively covers the subtopic or merely mentions it.

## The authority gate

For each candidate, both tests must pass.

**Adherence.** The source substantively treats *this lesson's* subtopic — you can extract a fact, procedure, number or example that serves the stated objectives. "It is about the general topic of the course" does not pass: the whole course is about the general topic.

**Authority.** The source is a kind of thing you can ground teaching in. The ranking is the same everywhere, even though its top rung looks different per field:

1. **The primary source** — whoever defines the thing. Official documentation for a tool; the standard or regulation for a compliance topic; the original study for a scientific claim; the institution's own published method for a discipline.
2. **The people who maintain or practise it publicly** — the maintainer's repository, the professional body, the practitioner who publishes their working method with evidence.
3. **Peer-reviewed or officially published work** — a paper, a standard, a government or industry-body publication.
4. **A recognised book, or an author the field itself cites** as a reference.
5. **A deep article with verifiable specifics** — numbers, procedure, worked example, something a reader could check.

Below that is not a course reference. Reject shallow posts that restate the primary source in other words, SEO content, "top 10" listicles, aggregators, machine translations, and marketing copy wearing the field's jargon.

The practical test: **if this page is wrong, does anyone fix it?** A primary source has an owner with a reason to correct it. An SEO blog stays wrong forever.

**A source that is on-topic but has no authority is rejected.** This is the most common case and the most tempting one — the blog talks about exactly the lesson's subject, which is precisely why it looks good.

## Empty is a correct answer — and it blocks the lesson

Approving zero is legitimate and will happen often. A lesson with no source is visible and recoverable; a wrong source approved in silence becomes grounding and is not.

Cap it at three. Do not fill slots.

But report the empty result loudly. Downstream, no sources means the lesson cannot be written yet — the expert supplies a source, their own material is used, or the lesson is written from declared experience. A lesson that silently proceeds with nothing is how half a course ends up grounded in the model's memory.

## Do not let one page serve the whole course

Deduplicate by **page, not by domain**. Twenty-five lessons citing twenty-five different pages of the same official site is the right outcome — forcing domain diversity pushes lessons onto worse sources.

If you are processing lessons in parallel, reserve a page the moment a lesson claims it, and release it if the gate rejects it. Reading committed state is not enough: two lessons in flight both read before either writes, and both claim the same link.

## If the gate cannot run

Approve nothing. When judgement is unavailable — an outage, a rate limit, an unparseable response — the failure is rarely limited to one lesson, and falling back to "top search results" would reference the whole course by raw ranking with no authority test, indistinguishable from real approval.
