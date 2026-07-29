# AGENTS.md Skeleton for Output TINAs (Annotated)

[How to use: at assembly, write each section against this skeleton. The
bracketed notes are guidance for you — they must not appear in the
finished product. Keep the whole AGENTS.md under about 200 lines; push
details down into guidance documents in the app area. Write in the end
user's language.]

---

front matter [all five fields required; version starts at 1.0.0;
tina-spec is "0.1"]:

    ---
    name: <app name>
    description: <one-line description>
    author: <expert's name>
    version: 1.0.0
    tina-spec: "0.1"
    ---

## What this is, and who it's for
[Two or three paragraphs: what the app does; who the users are and what
they are assumed to know and not know; state the agent's role explicitly
(build alongside? draft? guide? keep the ledger?).]

## Directory structure
[One line of purpose per directory. Follow the app/state split.]

## Startup sequence
[Read this file → read the last few journal entries → (archetype-specific
checks, e.g. the tracker's deadline scan) → report to the user: last
time, current status, 2–3 options.]

## First run
[How to detect it (state area has no content); a two-or-three-sentence
self-introduction; environment self-check (as the archetype requires,
each item with a fallback plan); initialize state; the first guiding
question.]

## Workflow
[Write per the archetype's core loop. Written as action guidance for the
agent, not a user manual; name which guidance document in the app area to
read at each step.]

## Protocol invariants
[Copy the English block verbatim from Meta TINA's
app/spec/TINA-SPEC-0.1.md. Do not type it from memory — copy, then diff
to verify (M3).]

## App invariants
[Consider at least three kinds: the voice-inheritance clause (see
voice.md, adapted); archetype-specific clauses (the tracker's redundant
honesty and answers-with-receipts, the mentor's safety red lines, the
generator's rubric self-check duty); domain red lines the expert
specifies. Number each one.]

## Verification (what counts as done)
[Write per the archetype's DoD shape; criteria must be concrete and
executable; state which checks the agent runs itself and which require
the user's confirmation.]

## Environment and capability declaration
[Requires: tools, versions, network (none by default). Commitments: never
leave the workspace, data stays local, no remote connections — for
trackers this section is mandatory.]

## Voice
[Starting from voice.md's eight principles, adapted to this app's users,
write 5–8 rules. This is not a decorative section — be concrete, and
include one or two good/bad examples from this domain.]

## Archival policy
[Following the I5 default is enough; write only deviations. If there are
none, write "follows the default policy."]
