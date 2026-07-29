# Archetype: Builder

## Definition & examples

Accompany the user in designing and making a runnable artifact. Examples:
a Minecraft mod builder, a web mini-game workshop, an office-spreadsheet
automation script shop.

## Core loop

Design conversation → implement → build/run → user verification →
iterate.

## State-area shape

design/ (design decisions and rationale, one traceable entry each), the
artifact directory (source or project files), build logs, JOURNAL.md.

## DoD shape: three-level verification

1. **Build passes** — the toolchain reports no errors;
2. **Load passes** — the artifact enters its host environment (the game
   loads it, the page opens);
3. **Behavior confirmed** — guide the user to witness the concrete
   phenomenon with their own eyes: "Enter the game, right-click on grass
   — you should see… do you see it?"

The agent can self-check the first two levels; the third always needs the
user — that is the thing the user actually wanted.

## Supplementary extraction questions

- The target environment's version matrix and known compatibility traps;
- What is the "minimal runnable starting point" (this domain's hello
  world)?
- What is the build toolchain, and where does installation most often get
  stuck?
- A few examples of the mapping: typical request → typical implementation
  approach.

## Archetype-specific risks

- **Environment hell.** The first run must include an environment
  self-check, and every item needs a fallback plan (what to do when X
  won't install, where to get help). Most users die at step one, not step
  ten.
- **Version drift.** Guidance documents should teach "diagnostic
  thinking," not "fixed version-number answers"; concrete version
  numbers and download links go into a separate, dated facts file that is
  the only thing updated when it goes stale (see
  workspace-conventions.md, item 8).

## Skeleton notes

app/{guidance documents, template code or starter project, facts file};
state/{design/, artifact directory, JOURNAL.md}.
First run = environment self-check + getting the starter project running
once.
