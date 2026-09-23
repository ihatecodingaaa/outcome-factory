# L7 documentation corrections — change log

**Applied by:** Architect `2201904f/architect-x7jh` on 2026-09-24 SGT, at Lucas's instruction ("PHASE 0: ENGINEERING BASELINE", Task 1).
**Source of the corrections:** `reviews/phase0/PHASE0_READINESS_REPORT.md` §5, item L7 (a)–(i).
**Not changed:** the Phase 0 reports (`architect.md`, `developer.md`, `PHASE0_READINESS_REPORT.md`) are preserved as written. The Verifier's withheld findings are untouched; its independent review remains **INCOMPLETE** (BAND msg `fabe66ae-093f-4a89-a07f-909845ab49b4`).
**Why this log exists:** the git repository was created *after* these corrections, so git history cannot show the pre-correction text. This log records every edit and the pre-correction digest of each changed file.

**Pre-correction manifest:** SHA-256 of `MANIFEST.sha256` before the edits was `1bd4cff9c1432853a619700bf46b5a16e1951631f8034b6c86390a482efd9de3`. After the edits it failed for exactly the 13 files below and passed for the other 10, so no other file changed.

## Corrections

| L7 | File | Change (before → after, abridged) |
|---|---|---|
| (a) | `operations/BAND_RUNBOOK.md` | Verifier handle `2201904f/independent-verifier-x7jk` → `2201904f/independent-verifier-x7j`, noting that `x7jk` is the BAND display name. Evidence: `jam chat participants`, 2026-09-24 |
| (a) | `docs/PRIOR_THREE_HACKATHON_RESEARCH_BLUEPRINT_2026-09-24.md` §6 | Seat list `independent-verifier-x7jk` → `independent-verifier-x7j`, with a display-name note |
| (b) | `README.md` | Prior-baseline filename `THREE_HACKATHON_RESEARCH_AND_EXECUTION_BLUEPRINT_2026-09-24.md` → `docs/PRIOR_THREE_HACKATHON_RESEARCH_BLUEPRINT_2026-09-24.md` |
| (c) | `docs/ADRS.md` ADR-004 | "judges require meaningful agent collaboration" (stated as fact) → "[INFERENCE; DF-03 judging criteria are UNKNOWN until the official pack] judges are likely to look for…" |
| (d) | `ux/DESIGN_SPEC.md` | Added a domain caveat. "Can this wallet build ship?" → "Can this build ship?" (e.g. an illustrative wallet build) |
| (d) | `docs/UX_DEMO_STORYBOARD.md` | `Transfer funds` presented as an illustrative example; the real feature depends on the UNKNOWN track domain |
| (d) | `docs/THREAT_MODEL.md` | "synthetic financial/booking data only" → "synthetic data only (domain UNKNOWN…; no real financial or personal data in any case)" |
| (d) | `docs/PRODUCT_THESIS.md` | "my new payment/booking feature" → "my new consequential feature (e.g. payment or booking)" |
| (d) | Blueprint §5, §6, §7 | Caveats added: the §5 user journey is illustrative; the §6 Pocketful acceptance targets are CONDITIONAL on a money domain (UNKNOWN); the §6 Tablekeeper double-booking example is conditional; the §7 "Move money safely" beat is illustrative |
| (e) | Blueprint §2.1 | The single `[RULE]` paragraph is split. `[RULE]` now covers the Luma statements only. Track names are attributed to LabLab [S2], not Luma, because Luma's page shows no track names (Architect fetch, 2026-09-23 ~17:35 UTC). The seat claims are relabelled `[USER_SCREENSHOT, not in this pack; UNKNOWN until reconfirmed]`. "Seats may share runtime/model" and "mandates must be generic" are marked UNKNOWN |
| (f) | `competition/REQUIREMENTS_LEDGER.md` | New UNKNOWN rows: DF-01a (CLI-attached seats "in BAND Desktop"), DF-02a (track domains), DF-04a (shared runtime/model), DF-04b (mandate genericity). DF-01 is marked re-verified. DF-06 records the mandates as provisional. Lucas's 2026-09-24 decision not to ask further organizer questions is recorded |
| (g) | `mandates/architect.md`, `mandates/developer.md`, `mandates/independent_verifier.md` | Each gains an identical, domain-independent section, "## No self-escalation": "Must not modify its own or any other seat's mandate, policy or permissions, or request escalation except through the human owner…". Architect: "another agent's permissions" → "its own or another agent's permissions". Developer: "may not silently increase scope" → "may not increase its own scope (silently or otherwise) without human approval" |
| (h) | `competition/ORGANIZER_QUESTIONS.md` | Added Q7 (DF-01a) plus a status note. Lucas decided not to ask additional questions. Whether Q1–Q6 were posted is UNKNOWN; Q7 is not posted; all seven are UNRESOLVED |
| (i) | Blueprint §9A, §14 | `competition/rubric-ledger.md` → `competition/REQUIREMENTS_LEDGER.md` (§9A keeps an "originally planned as" note) |

## Digests of changed files (first 16 hex characters)

| File | Before | After |
|---|---|---|
| `operations/BAND_RUNBOOK.md` | `d1a832043015fb5c…` | `d1fe10ac29530052…` |
| `README.md` | `bc5e16e761b9dc7d…` | `bdd90918480bfd76…` |
| `docs/ADRS.md` | `cb306c7107cbc277…` | `1829d8ff835a4cf8…` |
| `ux/DESIGN_SPEC.md` | `e8297558ca8a301f…` | `c15ba37089f24e9c…` |
| `docs/UX_DEMO_STORYBOARD.md` | `cea7e79d407cb564…` | `428513d7b6d802ad…` |
| `docs/THREAT_MODEL.md` | `0c90e04884a44f0b…` | `0064b67ce8bc42e6…` |
| `docs/PRODUCT_THESIS.md` | `e6bd8d860b11e0a4…` | `3b5f84dd3538b9d6…` |
| `docs/PRIOR_THREE_HACKATHON_RESEARCH_BLUEPRINT_2026-09-24.md` | `f0a30ba7c1d57dc2…` | see `MANIFEST.sha256` (edited again after this table was first computed) |
| `competition/REQUIREMENTS_LEDGER.md` | `a359def921bd40b8…` | `9a507a5fd2c387d3…` |
| `competition/ORGANIZER_QUESTIONS.md` | `f003aac00cbec34d…` | `c4d53a42a3fc1c6c…` |
| `mandates/architect.md` | `280769734ff94ae2…` | `4e99c917fe46a6be…` |
| `mandates/developer.md` | `fd33815f3cf75f59…` | `c15471aac09803eb…` |
| `mandates/independent_verifier.md` | `90fa83af1caf2ba4…` | `ef12f40157bbf3c9…` |

The authoritative post-correction digests are in the regenerated `MANIFEST.sha256`.

## Checks run after the edits

| Check | Result |
|---|---|
| No remaining `x7jk` used as a handle (only display-name notes) | PASS |
| No reference to the old blueprint filename | PASS |
| ADR-004 carries an INFERENCE label | PASS |
| Every remaining wallet, money or `Transfer funds` mention carries an illustrative or conditional caveat | PASS |
| No `[RULE]` label covers the seat or shared-model sub-claims | PASS (the §2.1 line contains the word `[RULE]` only for the Luma statements) |
| Ledger statuses: DF-01a, DF-02a, DF-04a, DF-04b and DF-06 are UNKNOWN | PASS |
| All three mandates contain "## No self-escalation"; "silently increase scope" is removed | PASS |
| ORGANIZER_QUESTIONS has Q7 and a status note | PASS |
| No `rubric-ledger.md` reference except the "originally planned as" note | PASS |
| All files LF-only | PASS |

## Whitespace normalization before the baseline commit (approved by Lucas 2026-09-24)

`git diff --cached --check` failed (exit 2) on whitespace that was already in the original pack; none of it came from the L7 edits. With Lucas's approval ("Normalize formatting"), exactly the 20 flagged items were fixed and nothing else:

| File | Lines | Change |
|---|---|---|
| `README.md` | 3, 4, 5, 27, 28 | Two-space hard line break → trailing backslash `\` |
| `docs/ARCHITECTURE.md` | 68, 69 | Two-space hard line break → `\` |
| `docs/PRIOR_THREE_HACKATHON_RESEARCH_BLUEPRINT_2026-09-24.md` | 3, 4, 5, 6 | Two-space hard line break → `\` |
| same | 7 | Single trailing space at paragraph end removed (it rendered nothing) |
| same | end of file | Extra blank line at the end removed |
| `experiments/EXPERIMENT_PROTOCOL.md` | 9, 10, 28, 29, 30, 31, 32 | Two-space hard line break → `\` |

**Rendering preserved.** CommonMark 0.31.2, "Hard line breaks": "A line ending is parsed as a hard line break if (a) it is preceded by two or more spaces, or (b) it is a backslash at the end of the line", and "a hard line break at the end of a block or paragraph is not recognized". Every converted line is followed by a line that continues the same paragraph (checked line by line), so each renders the same line break as before. No words were changed.

**Proof that only approved changes exist.** A read-only script reversed, in memory, every L7 edit in this log and every whitespace change above, then hashed the result. **All 23 original pack files reconstructed byte-for-byte to the pre-correction manifest digests** (10 unchanged, 11 L7-only, 2 formatting-only, 2 both). Any unlogged change would have produced a mismatch.
