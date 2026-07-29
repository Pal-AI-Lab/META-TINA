# Phase 4 — Assembly

## Purpose

Assemble the reviewed drafts into a complete, conformant TINA workspace.

## Location

state/projects/<project-name>/workspace/

Once assembled, it is a complete TINA in its own right; and because its
root contains a README.md, it is also a sub-workspace of this workspace —
from then on, before working inside it, read its README first (I2). That
is exactly the courtesy the protocol intends.

## Steps

1. **Choose the skeleton.** Build the directory tree per the "skeleton
   notes" in the primary archetype file. Default to the app/ + state/
   split (see craft/workspace-conventions.md).
2. **Write AGENTS.md.** Section by section per
   craft/agents-md-template.md; complete front matter; protocol
   invariants **copied verbatim** from app/spec/TINA-SPEC-0.1.md, then
   diff-checked after copying (M3).
3. **Place the guidance documents.** The reviewed drafts go into its app
   area.
4. **Write the conventional fixtures.** Empty journal template, startup
   sequence, first run, stuck protocol — all per
   craft/workspace-conventions.md.
5. **Write the voice section (M5).** Starting from craft/voice.md,
   adapted to this app's user profile, written into its AGENTS.md.
6. **Write the human README.** Its storefront, addressed to its end
   users, in the spirit of this workspace's root README: what it is, how
   to start, who owns the data, interruption is fine.
7. **Compatibility stubs.** CLAUDE.md and GEMINI.md, one pointer line
   each.
8. **Do NOT git init yet.** Note: do **not** initialize git inside
   workspace/ at this point. During the build, its files are archived by
   this workspace's git (M6); its own independent git history begins only
   at the release phase (M7). An early init would make the outer git
   treat it as an embedded repository and stop tracking its contents,
   breaking the build's archival trail.

## Mechanical conformance checklist

- [ ] AGENTS.md exists; front matter contains name / description /
      author / version / tina-spec;
- [ ] The protocol invariants block matches section 2 of
      app/spec/TINA-SPEC-0.1.md verbatim (diff-checked);
- [ ] App description, directory structure, and app invariants are all
      present;
- [ ] A Verification (DoD) section exists with executable criteria;
- [ ] An environment and capability declaration exists (what it needs +
      what it promises not to do);
- [ ] A first-run procedure exists;
- [ ] CLAUDE.md / GEMINI.md contain only a pointer to AGENTS.md;
- [ ] Every sub-workspace has a README.md of ≤150 lines;
- [ ] The root README.md is written for humans;
- [ ] The state area structure is complete (empty journal template,
      etc.);
- [ ] No [PENDING EXPERT CONFIRMATION] tags remain anywhere.

## Outputs

- The complete workspace/;
- Checklist results, item by item, recorded in PROJECT.md; commit.
