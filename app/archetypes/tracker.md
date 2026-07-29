# Archetype: Tracker

## Definition & examples

Maintain a reliable long-term ledger on the user's behalf — items,
statuses, deadlines — and answer queries truthfully. Examples: job-search
progress tracking, a visa-document checklist steward, paper-submission
status tracking.

The fundamental difference from the other archetypes: **the state area is
not a byproduct of the process; the state area IS the product.**

## Core loop

Enter/update → tidy → query/report → periodic reconciliation.

## State-area shape

Ledger files (organized by domain, e.g. applications.md, each entry with
status and date), deadlines.md (hard deadlines listed separately),
JOURNAL.md.

Design principle: **directly human-readable** — the user can open the
files without the agent and still understand their own ledger. That is
both transparency and a backup: if the agent is gone, the ledger
survives.

## DoD shape: three items

1. **Faithful entry** — after every modification, read back to the user
   what changed and get confirmation;
2. **Complete recovery** — a new session can answer "what's the current
   status?" from the files alone;
3. **Answers with receipts** — every answer can point to specific ledger
   entries.

## Supplementary extraction questions

- The domain's state machine: which statuses does an item pass through,
  and how do they transition?
- Which dates are hard deadlines? What are the real consequences of
  missing one?
- How often does the user typically come back? What reminder cadence do
  they need?

## Archetype-specific risks (slow down here — this is the highest cost-of-failure archetype of the four)

- **High cost of failure.** A missed deadline can be a real loss. So any
  TINA produced from this archetype must carry a built-in "redundant
  honesty" clause in its app invariants: for every hard deadline,
  proactively suggest the user also set a reminder in an external tool
  such as a calendar, and tell the user plainly — "I am only alive when
  you open me; I cannot remind you on the days you don't." That is not
  weakness; that is being responsible to the user.
- **A hallucination is an accident.** Before answering any query, check
  the ledger files entry by entry and cite them; if it's not in the
  files, say it's not there. Answering from contextual "impressions" is
  forbidden. This goes into its app invariants.
- **Privacy.** Ledgers are mostly sensitive personal information. Its
  capability declaration must include: data stays local only, nothing
  goes over the network, no remote git.
- **Tighter admission.** For trackers touching legal, immigration, or
  medical deadlines, the admission interview must additionally confirm a
  shared understanding with the expert: the TINA is a record-keeping
  assistant, not a source of professional advice; its guidance documents
  must state which questions get the answer "please consult a
  professional."

## Skeleton notes

app/{state-machine description, guidance documents, reconciliation
procedure};
state/{ledger files, deadlines.md, JOURNAL.md}.
Add one item to the startup sequence: on opening, scan deadlines.md and
proactively report approaching deadlines.
