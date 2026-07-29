# Phase 6 — Release

## Purpose

Clean up, deliver, and feed what this project taught us back into
Meta TINA.

## Steps

1. **Clean up (M7).** Reset the output TINA's state area to pristine:
   restore the journal to the empty template, delete all data generated
   during the test drive. Confirm no [PENDING EXPERT CONFIRMATION] tags
   remain anywhere (if any do, send it back — M2).
2. **Re-check.** Re-run the mechanical conformance checklist from
   4-assembly.md.
3. **Set the version.** Its front matter version becomes 1.0.0 (or as
   the expert specifies).
4. **Independent git.** Only now run git init inside workspace/ and make
   a single initial commit: "<app name> v1.0.0". This is where the
   deliverable's own history begins. Also commit a release event in this
   workspace. (From here on, that directory is an embedded repository and
   this workspace's git no longer tracks its contents — intentionally:
   the product has shipped, and its future evolution is its own.)
5. **Export.** Ask the expert where they want the product (writing
   outside the workspace requires their explicit consent, I7); copy or
   zip it there.
6. **Handover script.** Teach the expert how to distribute it: "Send this
   folder to your users; have them open it with their own AI assistant
   and say 'start'." Remind them: each user's data stays in that user's
   own copy — copies don't talk to each other; and when the app needs an
   update someday, just bring this folder back to Meta TINA.
7. **Retrospective feedback.** Discuss three questions with the expert:
   where was it smoothest? Where did it snag the most? What do you think
   the templates are missing? Record the answers in state/insights.md —
   this is the raw material for Meta TINA's self-improvement. If it turns
   out a template or archetype document in the app area itself should
   change, propose it to the user via the maintenance-mode procedure
   (I4).
8. **Wrap up.** Append a release entry to the journal; PROJECT.md status
   = delivered; commit.
