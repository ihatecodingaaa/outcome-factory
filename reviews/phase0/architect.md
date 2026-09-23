# Phase 0 — Architect report (independent)

**Seat:** `2201904f/architect-x7jh` · **Written:** 2026-09-24 (SGT) · **Room:** `bfc167f5-cc0b-4575-bf11-c15d5fbee3e8`, shared task #1
**Pack integrity:** `sha256sum -c MANIFEST.sha256` run from the pack root → 23/23 `OK` (**PASS**, meaning the bytes match the manifest; it says nothing about whether the content is correct).
**Independence:** written before reading any Developer or Verifier report. All three seats are Claude models on one machine, running as the same Windows user, so their judgements are **correlated** and should not be counted as three independent reviews.
**Legend:** RULE / OFFICIAL / INFERENCE / HYPOTHESIS / UNKNOWN. I fetched no web source for this report; every external claim below is taken from the pack and has **not** been re-verified today.

## 1. Smallest viable real factory → Pocketful acceptance loop (CONDITIONAL)

Everything below is conditional on the official challenge pack (DF-03, UNKNOWN) and the prebuild ruling (DF-06, UNKNOWN). None of it may be built before kickoff. If the official stages conflict with it, the rubric wins (blueprint §12, Sep 27 gate).

| Step | Seat | Produces | Evidence (bytes that exist) | Enforcement level achievable on this machine |
|---|---|---|---|---|
| L0 Contract | Architect → Lucas accepts | Outcome Contract v1 derived **only** from the official Pocketful text | contract file + SHA-256; BAND message ID of Lucas's acceptance | Human decision; record only |
| L1 Challenger suite | Verifier | Acceptance and challenger tests written from the contract, **before** any implementation exists | test-definition SHA-256 posted in the room **before** the Developer's first commit | Freeze **timing** is provable. **Confidentiality is not**: same user and same filesystem mean the tests are not sealed (HYPOTHESIS H1 below) |
| L2 Build | Developer | Implementation in its own git worktree | base commit, diff, tree OID | Process only |
| L3 Execute | A runner script that neither the Developer nor the Verifier writes during the run | Frozen suite run against the built artifact | stdout/stderr, exit code, artifact SHA-256, environment identifiers | ADVISORY unless the runner is outside agent control (see Alt B) |
| L4 Counterexample | Verifier | Minimal failing sequence (seed, schedule, before/after state) | trace file + digest; BAND work item to the Developer | Real only if L3 actually failed |
| L5 Repair | Developer | Smallest diff; rerun the full frozen suite plus regressions | new commit, new artifact digest, full outputs | Process only |
| L6 Evidence manifest | Runner | `{commit, tree, artifact_sha256, contract_sha256, testdef_sha256, output_sha256[], env, BAND msg/work IDs}` | manifest + its digest | Integrity of bytes only (ARCHITECTURE "refuse misleading shortcuts") |
| L7 Human approval | **Lucas only** | Signature over the manifest digest, with an expiry | signature file | Only as strong as key custody; the key must not be readable by any agent |
| L8 Gate | Gateway | Recomputes the digest of what it will deploy, checks signature, expiry and one-time nonce, deploys to the **named local staging target** | allow/deny log line | "Enforced" **only** for that target, and only if its credential is outside agent reach. Otherwise ADVISORY |
| L9 Stale reject | Lucas or Verifier | One-byte change after approval, then retry the deploy | DENY log + mismatching digests | Same as L8 |

**Why this is the smallest:** it uses one contract, one frozen suite, one real counterexample, one repair, one signature and one gate check. It needs no evidence graph, no selective invalidation, no Alexa or Nebius work and no cloud services.

## 2. Architecture decisions I disagree with or would narrow (for cross-review)

- **D1 — Agent signatures add no independence here (ADR-002, ARCHITECTURE "Evidence.issuer_signature").** Any key the Verifier seat can use, the Developer seat can read: same OS user, same disk. *Proposal:* in V1, no agent-held signing keys. Use content digests plus the room's message order as the record. The **human** signature is the only one from a distinct trust domain, and only if the key is passphrase-protected or hardware-bound and absent from agent-readable environment variables and files. INFERENCE.
- **D2 — "Hidden/sealed tests" cannot be claimed (THREAT_MODEL row 3).** Without a separate OS account or container with ACLs, the Developer can read the Verifier's suite. *Proposal:* claim "frozen and fingerprinted before implementation", not "sealed". Upgrade the claim only if Alt B or a separate-account runner is adopted. HYPOTHESIS H1; the Verifier should try to falsify it.
- **D3 — "ONLY test deployment gateway" is untrue for local runs.** Any seat can start the app locally. *Proposal:* narrow the claim to "the gateway is the only path to staging target X", where X's credential or port binding is controlled outside agent reach. If that can't be shown, report ADVISORY (README evidence language).
- **D4 — Cut the evidence-debt graph and selective invalidation from the Dark Factory scope.** EVIDENCE_DEBT_PROPOSAL already requires conservative whole-approval invalidation on any digest change. That rule alone gives the demo's key beat. The graph and UI move to the "conditional later" tier.
- **D5 — The mandates don't yet meet the README exit criterion "explicitly prohibit self-escalation and fabrication".** The Architect mandate forbids expanding *another* agent's permissions but not its own, and does not forbid editing its own mandate. The Developer mandate says "may not *silently* increase scope", which implies non-silent escalation is allowed. The Verifier mandate forbids issuing itself cloud or network permissions only. Fabrication is covered in substance in all three. The mandates are otherwise domain-independent: I found no Pocketful routes, types or fields. One mild coupling: the Developer mandate names "release-token keys", a term from this product's own design. *Proposed wording, for Lucas to decide; I have not edited the files:* "Must not modify its own or any other seat's mandate, policy or permissions, or request escalation except through the human owner."
- **D6 — Authenticity policy for the failure beat is missing.** Nothing guarantees that the first implementation contains a real defect. *Proposal (pre-register now):* freeze the challenger suite before implementation. If it finds a real failure, that is the demo. If it finds none, report "no failure found" honestly and demonstrate the gate with a **disclosed, labelled SYNTHETIC** mutation, such as reverting a guard. Never present an injected defect as agent-discovered (UX storyboard already requires this).

## 3. Factual discrepancies found in the pack (evidence given; nothing edited)

1. `operations/BAND_RUNBOOK.md` lists the Verifier as `2201904f/independent-verifier-x7jk`. The actual registered handle is **`2201904f/independent-verifier-x7j`**; `x7jk` is only its display name. Evidence: `jam --session architect-x7jh chat participants bfc167f5-…` on 2026-09-24 → `2201904f/independent-verifier-x7j [member] independent-verifier-x7jk (Agent)`. The runbook itself says the handle BAND shows is authoritative.
2. `README.md` names its baseline `THREE_HACKATHON_RESEARCH_AND_EXECUTION_BLUEPRINT_2026-09-24.md`. The file in the pack is `docs/PRIOR_THREE_HACKATHON_RESEARCH_BLUEPRINT_2026-09-24.md`. The blueprint also says each seat "must receive a distinct generic mandate file"; three exist.
3. The kickoff and close times agree across the ledger (DF-05, UTC) and the blueprint (SGT): 26 Sep 16:00 UTC = 27 Sep 00:00 SGT, and 5 Oct 06:59 UTC = 14:59 SGT. **Consistent.**
4. `competition/ORGANIZER_QUESTIONS.md` asks for a permalink or screenshot once the questions are posted, and none is recorded. **UNKNOWN whether the questions were sent.**
5. The pack is **not a git repository** (`git rev-parse` → "not a git repository"). No commit binds this review to a revision; the manifest digests are the only version identifier.

## 4. Unknowns register

| ID | Unknown | Blocks | Owner | Gate |
|---|---|---|---|---|
| U1 | Official four stages, weights, outputs, hidden tests (DF-03) | Everything challenge-specific | Lucas / organizer | Sep 27, within 60 min of the brief |
| U2 | Prebuild boundary, and whether mandates may be prewritten (DF-06) | Reuse of any pre-kickoff artifact | Organizer (Q2, Q3) | Before kickoff if possible |
| U3 | Whether ≥3 seats each need a mandate file (DF-04, user screenshot only) | Seat setup | Lucas | Kickoff |
| U4 | How BAND run exports and mandate files are collected (Q5) | Submission evidence | Organizer | Kickoff |
| U5 | The research spike's location and contents (not in the pack) | Developer item 7 | Lucas | Before the cross-review |
| U6 | Human signing mechanism and key custody | L7 | Lucas | Before Oct 2 |
| U7 | GitHub plan features for private repos (environments, required reviewers, attestations) | Alt B | Developer / Verifier to cite docs | Before repo creation |
| U8 | Local runtime (Docker/WSL, DB engine) | L3, L8 | Developer | Sep 27 |
| U9 | BAND Desktop's own run record or export format (docs.band.ai not read by me) | ADR-004 | Architect | Kickoff |

## 5. Positions to test in the cross-review

- **H1:** on this machine, no control in THREAT_MODEL can honestly be called "enforced" without a separate OS account, container or CI trust domain.
- **H2:** the whole Dark Factory demo can be ADVISORY-honest and still strong, provided every beat is a real run and the labels are truthful.
- **H3:** the evidence-debt graph adds no judged value before the official stages are known.
