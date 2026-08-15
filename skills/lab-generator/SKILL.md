---
name: lab-generator
description: Write the hands-on lab for one lesson — one milestone from the contract, starting where the previous lab ended, every step verifiable. Decides nothing the contract already decided. Use after the lesson content exists.
---

# Lab Generator

One lab, one milestone. Read `course/contract.md` first: it already decided the artifact, the milestone order, the success signals, and where the lab runs. None of that is yours to change here — if the order looks wrong, that is a finding to take back to the expert, not a decision to make in a lab.

## You are continuing, not starting

This is the failure that ruins hands-on courses, and it is invisible to whoever writes each lab alone.

An audit of eight generated labs found the same defect from three angles: lesson three told the student to initialise the project from scratch, discarding what lesson two built; lesson five demanded "the Go service from the previous lesson" when every earlier lesson was Python; and the set used three languages and three credential styles. No lab knew what the others had done.

So:

**Open by naming the state you inherit.** "You should have the server running from lesson four, with one user created." One line. If the student is not there, they find out before they type, not five steps in.

**Never rebuild what an earlier milestone built.** If you need something from before, reference it — do not re-create it. Re-initialising is how a student loses twenty minutes of their own work and stops trusting the course.

**Close by naming the state you leave.** That is the next lab's opening line, and writing it makes the seam explicit.

**Keep the same language, tool and credential style as the earlier labs.** Consistency here is not taste; a second language in lesson five means the student now maintains two setups.

## Every step is verifiable

A step the student cannot check is a step they perform on faith. Faith compounds: they carry a broken system forward and blame themselves at the point it finally surfaces, three lessons later.

For each step: the action, then how to know it worked.

```
Add the trunk:

    <exact command>

You should see `Registered: yes`. If you see `Timeout`, the firewall is
dropping the port — check that 5060/udp is open before continuing.
```

The check earns its place three times over. It stops the student advancing broken, it turns a support question into a self-answer, and it tells you whether the step is even well specified — a step whose success you cannot describe is a step you have not thought through.

**The milestone's own success signal comes from the contract.** Steps inside the lab need their own smaller checks; the milestone check is the one that says the whole thing worked.

## Commands are complete or they are not commands

Copy-pasteable, in full. No placeholders the student cannot resolve, no "configure appropriately", no "adjust as needed".

If a value genuinely varies — their domain, their key, their region — say exactly where it comes from and what it looks like:

> Replace `ACME_KEY` with the key from the dashboard, under Settings → API. It starts with `ak_` and is about 40 characters.

"Set the appropriate value" is where a lab stops being a lab.

## Respect where it runs

The contract says which of these you are in, and it changes everything.

**The student's own machine.** Expect variation and meet it. Say which operating systems you tested, name the version that matters, and handle the common divergence inline rather than in an appendix nobody opens. This is where "works on my machine" is written into a course.

**An environment you provide.** Be exact — the ground is known, so there is no excuse for vagueness. But say how to get back to a clean state, because someone will break theirs.

**A third-party service.** Exact, but fragile: sign-up flows and free tiers change without telling you. Pin what you can, date what you cannot, and tell the student what to do if the screen no longer matches.

## Do not skip steps, because they will

Number the steps and say plainly that skipping breaks later ones. Students skim, recognise a step they think they know, and jump.

The defence is not a warning banner. It is that each step ends in a check — the skipper fails the check and finds out immediately, instead of four steps later with no idea which one they missed.

## Say what breaks

For each step likely to fail, name the symptom and the cause, inline, next to the step.

Not "if you have problems, check the logs" — the student cannot read logs they have never seen. The symptom in their words, the likely cause, the fix:

> **Nothing happens and the terminal hangs.** Almost always the daemon is not running. `systemctl status <service>` will say `inactive`.

The expert already knows these; they watch people hit them every week. It is one of the highest-value things to get from the interview, and it is what separates a lab from a transcript of someone who got it right the first time.

## Length

A lab is one milestone, not a chapter. If it needs more than roughly ten steps, either it is two milestones wearing one name, or you are teaching concepts inside the lab — move those to the lesson and leave the lab to the doing.

## It's working if

- The first line says what the student should already have, and the last says what they now have
- Every step has a check, and no check is "it should work"
- Every command can be pasted as written
- Nothing is rebuilt that an earlier lab already built
- The failure notes name symptoms in the student's words, not in the system's
- A student who skipped a step finds out at the next check, not at the end

## Known rough edges

**Nothing verifies the seam between labs.** Each one declares its inherited state, but no step checks that the previous lab actually leaves it. Reordering lessons breaks this silently — the same way it breaks glossary ownership.

**Drift against the real tool.** A lab pinned to a version rots when the tool moves; a lab not pinned rots faster. Date the labs, and treat a course with hands-on work as something that needs re-running, not just re-reading.
