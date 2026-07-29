# Phase 1 — Admission Interview

## Purpose

Three things: judge whether this idea is a good fit for a TINA; determine
which archetype it belongs to; open the project (or turn it away).

## Mindset

This step is gatekeeping, not selling. An idea that can't succeed is
better honestly turned away here than built and left broken in the
expert's hands — what breaks isn't just their time, but their trust in
this whole paradigm.

## How to ask

Don't fire questions like a survey. This is a conversation: one question
leads to the next, and you regularly restate your understanding in your
own words so the expert can correct you. Cover these seven areas:

1. **Artifact.** What is the thing that ultimately gets made? Can you
   describe a concrete example — what does it look like?
2. **Users.** Who will use it? What do they know and not know? Why can't
   they do this themselves?
3. **Verification.** How would a non-expert user know the result is good?
   Is there a cheap, fast check they can run themselves?
4. **Cost of failure.** What happens if it goes wrong? What does a redo
   cost? (High cost → tighten up; see the tracker archetype's
   guardrails.)
5. **Cadence.** How will users use it? One-shot, or repeatedly over time?
   Can they tolerate each step taking tens of seconds to minutes?
6. **Environment.** What software must be installed, what services
   connected, what materials prepared?
7. **Textualization test.** Ask the expert to recount a real time they
   walked a novice through this: where did they correct the novice? On
   what basis? — If the expert can articulate the basis for a judgment,
   the knowledge can be textualized; if they keep coming back to "feel"
   or "it just looks wrong," discuss honestly: can that part be covered,
   and if not, how much value does the app still have?

## Classification

Determine the primary archetype against app/archetypes/README.md; a
secondary archetype is allowed. Record the classification and its
rationale in the file.

## Pass criteria (all must hold)

- The artifact's boundaries are clear;
- The verification loop is cheap, or at least clearly executable;
- Failure is survivable (or survivable after adding guardrails per the
  tracker rules);
- The latency is tolerable;
- The state fits in text at this scale;
- The core knowledge can be textualized.

## How to turn someone away

First sincerely affirm the idea's value, then point specifically at which
criterion it fails, and finally offer alternatives (narrow the scope? a
different form? start with a subproblem?). Turning away still gets filed:
create a folder under state/projects/, write admission.md, set
PROJECT.md's status to "not admitted" with the reason. If the criteria
change later (say, runtimes get more capable), this file is the restart
point.

## Outputs

- The state/projects/<project-name>/ directory;
- admission.md: interview summary, a verdict on each of the six criteria,
  archetype classification and rationale;
- PROJECT.md: phase = admitted (or not admitted);
- commit.

## A note on tone

The expert is talking about a craft they treasure. Probing for the basis
of their judgments is not questioning their competence — explain up
front: the detailed questions are so the AI can learn it, and teach it
the way they would.
