# Phase 5 — Test Drive

## Purpose

Behavioral verification. A conformant workspace is not the same as an app
that runs — this step answers the question: can an agent that has never
seen it, accompanying a user who "doesn't know the field," actually get
things done with it?

## Principle: clean context

The test-driving agent must not carry build memories — otherwise it is
grading its own homework.

## Two methods (prefer A)

**A. A genuinely new session.** Guide the expert to open workspace/ in a
brand-new agent session and run it from "start": first run + one core
task. The expert plays the end user — remind them to deliberately "act a
little clueless" and ask the questions a layperson would ask. You stand
by in this session; the expert brings observations and issues back to
you.

**B. Strict simulation.** If a new session is truly impossible, you
simulate within this session, but you must: declare to the expert that
this is a simulation and less reliable than a real new session; act only
on the text inside workspace/; and the moment you catch yourself "knowing
something that isn't in the text," record it as a defect — it means that
piece of knowledge never got written down.

## What to watch for

- Does the first run clearly explain what it is and what you'll do
  together?
- Are the key guidance documents read at the right moments?
- Can the core task reach the app's own DoD verdict, and is that verdict
  executable?
- Does the tone meet the voice requirements (any naked jargon,
  condescension, fake enthusiasm)?
- Manufacture one frustration (e.g. give a vague request) and see whether
  the stuck protocol triggers gracefully.

## Recording and repair

Record all findings in state/projects/<project-name>/testdrive.md, graded
by severity: blocking (doesn't run) / degraded (runs but the experience
is poor) / polish (wording level). Go back to assembly or drafting to
fix, then re-run the affected paths.

## Clearing the ground after a drive

A drive leaves a `.git` inside workspace/: its first run initializes one,
and coding agents often do that on their own when they open a project.
That is expected. While it exists, this workspace's git treats
workspace/ as an embedded repository and stops seeing changes inside it.
So after every drive, before fixing anything: delete workspace/.git,
delete everything the drive produced in its state area (clones,
artifacts, journal entries), restore the state templates, and check that
this workspace's git reports workspace/ changes again. The product's own
git begins at release (6-release.md), never earlier.

## Completion criteria

One complete end-to-end pass with no blockers + the expert explicitly
saying "it's good."
