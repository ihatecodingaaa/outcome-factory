# Phase 0 — Final pre-kickoff engineering readiness report

**Prepared by:** Architect `2201904f/architect-x7jh` · **As of:** 2026-09-24 SGT (2026-09-23 ~17:55 UTC) · **BAND room:** `bfc167f5-cc0b-4575-bf11-c15d5fbee3e8`
**Design pack:** unmodified. `sha256sum -c MANIFEST.sha256` → 23/23 OK, run by all three seats and re-run by the Architect before this report. This file and the two seat reports under `reviews/phase0/` are new files outside the pack.
**Status labels:** RULE / OFFICIAL / INFERENCE / HYPOTHESIS / UNKNOWN for claims; PASS / FAIL / NOT_RUN / UNKNOWN for checks.

---

## 0. Review status — one of three reviews is INCOMPLETE

| Review | Source | Status |
|---|---|---|
| Architect (#1) | `reviews/phase0/architect.md`, SHA-256 `b6298cf201ef7de83bf82cb9aef38ff591bef2ddce8c16cf66e58cd03c5a1b94` | **COMPLETE.** Written before reading the other reports. Its positions have not been cross-reviewed |
| Developer (#2) | `reviews/phase0/developer.md`, SHA-256 `9f004bdbdc5c3238d36b96f6f5c61bb61b6aa6d85543eb7cf4975c0fdc442f2d` | **COMPLETE.** Independent. The Architect re-checked its key claims (§4) |
| Independent Verifier (#3) | BAND msg `fabe66ae-093f-4a89-a07f-909845ab49b4` (17:50:46Z); no file, by Lucas's decision | **INCOMPLETE.** A safety classifier blocked the written report. On Lucas's instruction the Verifier posted permitted findings only. **Withheld:** (a) novelty falsification, (b) trust-boundary falsification, (c) the five negative tests, (d) competitor-overlap conclusions. **Reported:** (e) rubric-coverage check, first-party source list with access times, unresolved questions, recommendations |
| Cross-review round | — | **NOT_RUN** |

**This report does not claim that all three reviews passed.** The core novelty claim, the trust-boundary design and the competitor matrix have had **no completed adversarial review** and remain **UNVERIFIED**. Limitation: all three seats are Claude models on one machine running as one Windows user, so their agreement is correlated judgement.

---

## 1. Critical blockers (prioritized)

| # | Blocker | Evidence | Owner | Gate |
|---|---|---|---|---|
| **B1** | **The official rules are unknown and the question list is incomplete.** DF-03 (stages, criteria, weights), DF-06 (prebuild boundary: pre-written mandates and pre-created seats and room), Pocketful's domain, and **DF-01, a new question**: does "Build a software factory **in BAND Desktop**" accept Claude Code seats attached through the jam CLI? Nothing records the organizer questions as sent. | Luma, fetched by the Verifier at 17:21:57Z and by the Architect at ~17:35Z; `ORGANIZER_QUESTIONS.md` has no sent record and no DF-01 question | Lucas | Questions posted before kickoff; ledger updated within 60 minutes of the brief |
| **B2** | **The adversarial review is incomplete.** Novelty, the trust boundary, the negative tests and competitor overlap are withheld. No differentiation or "enforced" claim may be made until Lucas decides how, or whether, to complete them. | §0 | Lucas | Before any public claim; no later than 2 Oct |
| **B3** | **There is no trust boundary on this machine.** All seats run as Windows user `lucas`. The Claude Code sandbox: "Native Windows is not supported" (OFFICIAL, verified). On private repos on Free, Pro or Team, "required reviewers are only available for public repositories" (OFFICIAL, verified). There is no Docker, and the owner's GitHub token (`repo`, `workflow` scopes) sits in the user keyring. **Every "enforced" control is ADVISORY today.** | Developer §5; Architect re-checks | Lucas | Boundary set up before kickoff, or accept ADVISORY labels throughout |
| **B4** | **No git repository, and CRLF.** There is no rollback, no worktrees and no tree OIDs to bind evidence to. `core.autocrlf=true` system-wide makes working-tree digests diverge from Linux and judge digests, so the "one-byte change → deny" beat can false-deny. | `git rev-parse` fails; `git config --system core.autocrlf` → `true` (verified) | Lucas | Authorize a local `git init` and `.gitattributes`, at kickoff at the latest |
| **B5** | **Commit attribution conflict.** The Claude Code harness instructs agents to add a `Co-Authored-By: Claude` trailer; the Architect's own session context contains it. `CLAUDE.md` forbids it. | Developer R8; Architect confirms from its own context | Lucas | Before any seat commits |

**Also high:**
- Test libraries (hypothesis or fast-check, playwright) and possibly a database need approved installs at kickoff.
- The mandates don't meet the README exit criterion "explicitly prohibit self-escalation".
- The research spike is not in the pack.
- The 15-minute rollback has never been timed.
- Whether three concurrent seats hit shared subscription usage limits is UNKNOWN.

---

## 2. Architectural disagreements

| # | Disagreement | Positions | Resolution |
|---|---|---|---|
| **X1** | Human signature in V1 | Architect: keep Lucas's signature over the evidence-manifest digest; it's the only signature from a distinct trust domain, and agent-held keys add no independence here (Architect D1). Developer: first cut under time pressure is "SHA-256 manifest + recorded approval, ADVISORY" | **Open → Lucas.** Recommendation: keep a real signature **only if** B3's separate account exists, because key custody is the whole point; otherwise record the approval and label it ADVISORY |
| **X2** | Route to real enforcement | Architect offered "separate OS account, container or CI". Developer: containers are infeasible (no Docker) and CI approval gates are unavailable on private repos | **Resolved by primary docs** (GitHub, verified). The only local route is a separate Windows account (HYPOTHESIS, untested). Residual risk: `lucas` is in the filtered Administrators group, so any UAC elevation a human approves from a seat's session defeats it. Lucas's GitHub plan is UNKNOWN |
| **X3** | Wallet or money assumptions in the pack | Verifier: DESIGN_SPEC, the storyboard, the thesis and experiment tasks 1–3 assume a money domain without a caveat | **Partly upheld.** Upheld for DESIGN_SPEC ("Can this wallet build ship?") and the storyboard ("Transfer funds"). **Refuted for EXPERIMENT_PROTOCOL:** line 7 says "fixed challenge-agnostic tasks… Final Dark Factory domain examples depend on official challenge pack". PRODUCT_THESIS's "payment/booking" describes the product's buyer, not Pocketful (Architect's reading; unconfirmed by the Verifier) |
| **X4** | Pocketful's domain | Architect and Developer framed the loop and edge cases as "Pocketful-style transactional". Verifier: the domain is unpublished | **Verifier upheld.** Treat the domain as UNKNOWN until kickoff |
| **X5** | Is mandate genericity required? | Architect treated it as a requirement. Verifier: the blueprint lists it as an open question | **Verifier upheld.** It's our design choice until the organizer rules |
| **X6** | Sealed tests and the "only deploy gateway" (Architect D2, D3) | Architect: claim "frozen and fingerprinted before implementation", not "sealed"; claim "only path to named target X", not "only deploy path". Developer agrees both are ADVISORY without a separate account | **Agreed by two seats.** The Verifier's trust-boundary review, which would test this, is withheld |
| **X7** | Evidence-debt graph | Architect and Developer: cut from the Dark Factory scope; keep conservative "any digest change invalidates the approval" | **Agreed by two seats** |

**Design alternatives** (Architect's proposal, not independently reviewed):
- **Alt A — Local gate under a separate Windows account.** No spend; works offline; a real OS boundary for one named staging target. Costs: setup before kickoff and the UAC residual. Recommended for Dark Factory.
- **Alt B — Hosted CI executor and gate.** A third-party trust domain and Linux build parity. But it needs a public repo on Free, Pro or Team, or Enterprise; it exposes the code early; the owner token must still be separated from the seats; and the loop is slower. Revisit for Nebius, which must be public anyway.

---

## 3. Competition compliance (Dark Factory)

| Ledger | Requirement | Status today | Evidence or gap |
|---|---|---|---|
| DF-01 | Factory built **in BAND Desktop**; submit factory, run and clean-room result | **RULE, verified today** (Luma). Whether our setup complies is **UNKNOWN** | Our seats are CLI-attached Claude Code sessions. Question not yet asked (B1) |
| DF-02 | Two tracks, Pocketful and Tablekeeper | RULE in pack, **not re-verified today** | Track descriptions are unpublished; the domain is UNKNOWN (X4) |
| DF-03 | Four graded stages | Existence verified; **details UNKNOWN** | ADR-004 states "judges require meaningful agent collaboration" as fact; it is an INFERENCE (Verifier; wording confirmed by grep) |
| DF-04 | ≥3 seats, each with a mandate file | **Screenshot only** (not in pack) | Three seats exist and are bound to the room (verified via `jam`). The blueprint's `[RULE]` label on "seats may share runtime/model" is unsourced in the pack |
| DF-05 | Kickoff 26 Sep 16:00 UTC; submit 5 Oct 06:59 UTC | RULE in pack, **not re-verified today**. Luma confirms "Sept 26 – Oct 5" | Times agree across the ledger (UTC) and the blueprint (SGT) |
| DF-06 | Prebuild or clean-room boundary | **UNKNOWN** | Mandates are pre-written and in the manifest; this is **compliance-at-risk** until organizer Q2 is answered. Keep them provisional, and plan to regenerate them in the window if ruled out |
| Pack rule | No challenge-specific code before kickoff | **Complied.** No application, gate or test code exists | Verified: the pack is docs only; `reviews/` holds reports only |
| Pack rule | No `Co-authored-by` trailers | **At risk** (B5) | Harness default conflicts |

**Compliance posture:** nothing breaches a published rule today. Two items are **at risk pending organizer answers**: DF-01 (CLI seats) and DF-06 (pre-written mandates).

---

## 4. Engineering feasibility

**Time.** The window is 206 h 59 min wall-clock. Throughput is limited by one human approving three seats' permission prompts, commits and pushes. INFERENCE (Developer); agreed.

**Toolchain.**

Verified by the Developer and re-run by the Architect:
- git 2.54 with system `core.autocrlf=true`
- node 24.16 with `node:sqlite` 3.53.0
- python 3.14.5 with pytest; hypothesis, psycopg and playwright absent
- docker, psql, sqlite3 and cosign absent

Reported by the Developer only (not re-run):
- Windows 11 Home; PowerShell 5.1 with no `pwsh`
- WSL 2 (`kali-linux`) present
- uv, openssl, gpg and jq present
- 16 logical CPUs, 31.4 GB RAM

**Edge cases a deterministic harness can reproduce here** (Developer; conditional on the domain):
- Idempotent retry and app-level atomic failure: **yes**.
- Concurrent lost update: **only with a designed test seam** that forces the interleaving.
- Database isolation anomalies such as write skew: **not reproducible** without Postgres.
- Decimal handling: reproducible. A SQLite `NUMERIC` sum of 0.1 three times gave `0.30000000000000004`; the Developer ran this and I did not re-run it.
- Power-loss durability: **UNKNOWN**; don't claim it.

**Keeping a runnable app.** The product app must run with every factory component switched off. Use one gate command, `green-NNN` tags created only from a clean checkout, and one worktree per seat. The 15-minute rollback is **UNKNOWN** until a timed drill passes. All of this depends on B4.

**Enforcement feasibility** (Developer §5, key rows verified):

| Control | Feasible here? |
|---|---|
| Push, repo and workflow actions | Only if the owner token is removed from the seats' reach |
| Staging deploy and release token | Only via a separate account (Alt A) |
| Sealed challenger tests | Only via a separate account |
| Mandate edits | Detect only |
| Forbidden shell or network access | **Infeasible** in the window; ADVISORY |
| Spend caps | ADVISORY |

**Where post-test checks must run:**
- At runner start **and** end: tree OID, lockfile, test definitions and config allowlist.
- At the gateway: copy the artifact, hash it and deploy **that** copy, so nothing can change between check and use.
- Human approval digests must be recomputed from the tag, never copied from chat.

**Smallest authentic failure → repair → reject-stale demo** (conditional on the official pack):
1. Contract from the official text only.
2. The Verifier's suite is frozen and its digest posted **before** implementation.
3. The built tarball is bound to its tree OID.
4. **Pre-registered authenticity rule:** a real failure is the demo; if none occurs, report "no failure found" and show the gate with a **disclosed, labelled SYNTHETIC** mutation.
5. Repair, then rerun the full frozen suite.
6. Lucas approves the exact digests.
7. The gateway denies a one-byte-changed artifact. Labels stay honest throughout.

**Cut order** (Developer; the Architect agrees):
1. Amazon and Nebius work
2. Post-deploy observation
3. Living twin and animation
4. Selective invalidation
5. Tablekeeper run
6. Baseline experiment
7. Cryptographic signing (reduce to recorded approval, ADVISORY)

**Never cut:** the official stages, a runnable app, the real BAND run record, honest labels.

**Gates (SGT):**

| Date | Gate |
|---|---|
| **27 Sep 00:00** | Kickoff. Ledger updated within 60 minutes; the rubric overrides the architecture where they conflict |
| 30 Sep | Working app plus a genuine BAND trace |
| **2 Oct** | Real loop running, or cut every extra |
| 4 Oct | Frozen tag and demo |
| **5 Oct 14:59** | Submission deadline. Submit hours early |

---

## 5. Decisions requiring Lucas's approval

| # | Decision | Recommendation |
|---|---|---|
| L1 | How, or whether, to complete the Verifier's withheld items (a)–(d) | Look into the block in the Verifier's window yourself. Until it's resolved, keep these claims UNVERIFIED and out of every submission |
| L2 | Set up a separate Windows account for the gate, approval key, challenger-suite store and staging target (Alt A) before kickoff, or accept ADVISORY everywhere | Set it up if it can be done before 26 Sep |
| L3 | Authorize a **local-only** `git init`, an `eol=lf` `.gitattributes` and a tag convention (no GitHub repo) | Authorize, at kickoff at the latest |
| L4 | X1: keep a human signature in V1, or use a recorded approval | Signature only together with L2 |
| L5 | Commit attribution: a project `attribution` setting (a settings change), or a manual `git log -1 --format=full` check before each push | The setting, plus the manual check |
| L6 | Pre-approve project-local test-library installs, and possibly a database, at kickoff | Pre-approve the scope; confirm the specific packages after the brief |
| L7 | Approve pack corrections; each edits a manifested file and needs the manifest regenerated | Approve the list below |
| L8 | Provide the research spike's location, license and authorship, or declare it out of scope | Declare out of scope unless it is needed |
| L9 | Post the organizer questions, including DF-01 | Post before kickoff |

**Corrections in L7:**
- (a) The runbook's Verifier handle becomes `2201904f/independent-verifier-x7j`; `x7jk` is its display name (verified via `jam chat participants`).
- (b) The README's blueprint filename.
- (c) ADR-004's reason relabelled INFERENCE.
- (d) Wallet and "Transfer funds" wording in DESIGN_SPEC and the storyboard marked conditional.
- (e) The blueprint's `[RULE]` label on "seats may share runtime/model".
- (f) DF-04 sub-claims (shared model, mandate genericity) recorded as UNKNOWN.
- (g) Explicit self-escalation wording in all three mandates. Proposed: "Must not modify its own or any other seat's mandate, policy or permissions, or request escalation except through the human owner."
- (h) The DF-01 question added to ORGANIZER_QUESTIONS.
- (i) The blueprint's `rubric-ledger.md` name reconciled with `REQUIREMENTS_LEDGER.md`.

---

## 6. Recommended next steps

**Before kickoff** (research and tool readiness only; nothing starts without Lucas's go-ahead):
1. **L9:** post the organizer questions, including DF-01; record permalinks and dates in the ledger.
2. **L1:** decide how to handle the Verifier's withheld review.
3. **L2, L3, L5:** decide the environment setup. If approved, Lucas sets up the separate account; `git init` locally with `.gitattributes`; configure attribution.
4. **L7:** apply the approved pack corrections and regenerate `MANIFEST.sha256`.
5. Read-only checks: docs.band.ai for how BAND runs are recorded and exported; the subscription usage limits for three concurrent seats; Lucas's GitHub plan.
6. Re-verify the DF-02 and DF-05 LabLab page and the DF-04 screenshot source on 26 Sep.

**Wait for the official briefing (27 Sep 00:00 SGT):**
- Track selection and Pocketful's domain; the Outcome Contract and invariants.
- The stack and database choice, and every dependency install.
- Writing and freezing the challenger suite.
- **Any** application, gate or evidence-schema code.
- Regenerating the mandates if DF-06 excludes pre-written ones.
- The timed rollback drill against the real app; the baseline experiment.
