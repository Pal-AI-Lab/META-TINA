# Workspace Conventions

The spec covers only the minimal promises; what a good app looks like is
governed by these conventions. Output TINAs adopt the full set by
default; deviations need a reason, recorded in their AGENTS.md.

## 1. Partitioning

`app/` = the author's program, read-only at runtime (protected by I4);
`state/` = everything writable at runtime. AGENTS.md, README.md, and the
compatibility stubs at the root are app-natured.

## 2. JOURNAL.md (state area)

The app's long-term memory. Format, per entry:

    ## YYYY-MM-DD — one-line title
    - What was done this time:
    - What was decided, and why:
    - Next step:

Append at milestones or before a session ends (this is how I3 is carried
out).

## 3. Startup sequence

AGENTS.md in full → the last 3–5 journal entries → (archetype-specific
checks) → report to the user: where things left off, how they stand,
2–3 options for what's next.

## 4. First run

Detection: the state area has no substantive content. Contents: a
two-or-three-sentence self-introduction; environment self-check as
needed (each item with a fallback plan); initialize the state area; ask
the first guiding question.

## 5. Stuck protocol

After roughly 3 failed attempts at the same problem: stop; commit the
scene; record a failure summary in the journal (what was tried, how each
attempt failed); explain in plain language where things are stuck; offer
options: roll back to the last checkpoint / try a different approach /
pause and resume later / suggest outside help.
Silent infinite retries are forbidden — getting stuck gracefully beats
spinning silently.

## 6. README push-down

A sub-workspace README stays ≤150 lines; when it won't fit, split details
into a deeper sub-workspace.

## 7. git rhythm

Commit at milestones (not every change); write commit messages in plain
language about "what this step did" — they are part of the trail log;
report to the user in "checkpoint/save" language, not tool jargon (I5).
A directory under state/ that is a repository of its own (see the
builder archetype) is gitignored by the workspace and committed on its
own rhythm; the workspace never treats it as an embedded repository.

## 8. Separate facts from judgment

Concrete facts that expire (version numbers, download links, prices) go
into a dated facts file; judgment, reasoning, and diagnostic method go
into the guidance documents. For future updates, only the facts file
changes; the guidance documents stay long-lived.
