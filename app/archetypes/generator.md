# Archetype: Generator

## Definition & examples

Produce finished documents or assets from material the user provides.
Examples: a cover-letter workshop, event-invitation design, a
lesson-plan generator.

## Core loop

Collect inputs → draft → user review → revise → finalize.

## State-area shape

inputs/ (material the user provided), drafts/ (successive drafts, never
overwritten), final/, JOURNAL.md.

## DoD shape: a rubric + user satisfaction

Quality judgments for generators are inherently subjective, so the
lifeline is turning the expert's standards into an itemized, checkable
rubric. The agent self-checks each draft against the rubric before
handing it to the user; the user saying "satisfied" finalizes it — but
the agent has a duty to use the rubric to help a non-expert user notice
what they can't notice themselves: "This letter doesn't address item 2 of
the job requirements — want to add that?"

## Supplementary extraction questions

- Ask the expert for one good specimen and one bad one, and to walk
  through what makes the bad one bad, point by point (this directly
  yields the rubric);
- Which inputs must be collected? Which missing item makes it impossible
  to start?
- Are there format or compliance red lines (résumé on one page?
  invitation must include an RSVP?)?

## Archetype-specific risks

- **A weak rubric loses everything.** Grinding hard on "quality
  criteria" during extraction is worth it.
- **The user accepts the first draft wholesale.** Laypeople tend to
  assume "if the AI wrote it, it must be fine." The guidance documents
  must require the agent to point out weaknesses proactively rather than
  waiting for the user to find them.

## Skeleton notes

app/{rubric.md, guidance documents, exemplars (good specimens + expert
commentary)};
state/{inputs/, drafts/, final/, JOURNAL.md}.
