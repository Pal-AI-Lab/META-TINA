# Archetype: Mentor

## Definition & examples

The user does things in the real world; the app guides, answers, and
follows up. Examples: a sourdough starter mentor, a first open-source
contribution mentor, a home vegetable-garden planner.

## Core loop

Understand the current situation → give the next step → user goes and
does it → comes back and reports → diagnose and adjust → loop.

## State-area shape

profile.md (the user's situation and goals), plan.md (route and
milestones), JOURNAL.md (each report and adjustment).

## DoD shape: milestones

Break "learned it / finished it" into a chain of milestones, each with an
external sign the user can judge on their own: "The dough has doubled in
volume; poke a hole and it springs back slowly." Reaching the last
milestone is completion.

## Supplementary extraction questions

- What is a novice's typical progression route? The typical sticking
  point at each stage?
- How do the user's verbal descriptions map to diagnoses? ("The bread is
  sour" could be which causes, checked in what order?)
- Which mistakes must be corrected on the spot, and which can they be
  allowed to run into themselves (sometimes hitting the wall teaches
  faster)?

## Archetype-specific risks

- **The agent cannot see reality.** It must ask, not guess. The guidance
  documents should teach the agent to ask "observational questions":
  "Describe what the dough's surface looks like," not "Is it done
  proofing?"
- **Reports may be distorted.** Design cross-checking questions; when a
  conclusion contradicts the user's description, suspect incomplete
  information first and keep asking.
- **Safety red lines.** In domains involving electricity, fire, knives,
  or health, the red lines are hard-coded into its app invariants: when
  unsure, stop and recommend getting someone competent on site. This is
  not negotiable.

## Skeleton notes

app/{roadmap, diagnostic manual, guidance documents};
state/{profile.md, plan.md, JOURNAL.md}.
First run = build the profile: current situation, goals, conditions,
frequency.
