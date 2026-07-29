# Phase 2 — Knowledge Extraction

## Purpose

Turn the experience in the expert's head into structured, draftable notes
(knowledge.md).

## Method: case walkthroughs first

Ask the expert to walk through 2–3 real cases end to end — at least one
that went smoothly and one that went sideways. Listen, probe, and keep
restating your understanding in your own words for them to correct.
**The corrections themselves are the most valuable knowledge**: wherever
they correct you is exactly where a novice would go wrong.

## Six kinds of things to extract

(Each archetype file adds supplementary questions — after this document,
read the relevant archetype file.)

1. **Decision points.** Where in the process are choices made? What is
   the basis for each?
2. **Axes of variation.** What differs from one user to the next? — This
   is the reason a TINA exists: what can be fixed gets written down; only
   what varies needs the agent's on-the-spot judgment.
3. **Common pitfalls.** Where do novices stumble most? What does the
   stumble look like? How do they climb out?
4. **Diagnostic procedure.** When something goes wrong, in what order
   does the expert investigate?
5. **Quality criteria.** How do you tell good work from bad? Down to
   checkable features. (This feeds directly into the output TINA's DoD.)
6. **Environment and resources.** Required tools, versions, materials,
   references worth recommending.

## Use your own knowledge well

You (the LLM) may know a fair amount about this domain too. Use it to ask
good questions and draft hypotheses ("My understanding is that mods like
this usually deal with version mappings — is that right?") — this is the
highest-leverage step in the whole process: having the expert act as a
reviewer is far more efficient than having them dictate.

But the rule is M2: your knowledge only counts once the expert confirms
it. Every line in the notes carries a source tag:
[EXPERT'S OWN WORDS] / [DRAFTED, PENDING CONFIRMATION] / [CONFIRMED].

## Outputs

- knowledge.md: notes in the six categories, each line source-tagged;
- update PROJECT.md; commit.

## Completion criteria

The expert agrees the notes cover the core; none of the six categories is
entirely blank — a blank either gets filled by further questions or gets
an explicit note: "not applicable to this app."
