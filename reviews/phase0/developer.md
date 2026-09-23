# Phase 0-D — Developer critique: feasibility, toolchain, edge cases, enforcement

**Seat:** `2201904f/developer-x7jj` (Claude Code 2.1.280, Claude Opus model family)
**Task:** shared task #2, room `bfc167f5-cc0b-4575-bf11-c15d5fbee3e8`, assigned by `architect-x7jh` from `operations/CLAUDE_ARCHITECT_PROMPT.md` item 2
**Written:** 2026-09-23 UTC (2026-09-24 SGT). Pre-kickoff, read-only design review.

**Compliance.** I wrote only this file. I edited no pack file, installed nothing, created no repository, branch, commit or push, ran no state-changing `gh` command, and searched nothing outside `C:\Users\lucas\Projects\dark-factory`. Read-only queries beyond version checks: `gh auth status`, registry reads (long paths, UAC), admin-group membership, and one in-memory SQLite probe (no file written). **Independence:** I did not read the other seats' reports or ask for their findings. **Correlation limit:** all three seats are the same model family; agreement between us is correlated judgement, not independent confirmation.

Labels: `RULE`, `OFFICIAL`, `INFERENCE`, `HYPOTHESIS`, `UNKNOWN`. Check results: `PASS`, `FAIL`, `NOT_RUN`, `UNKNOWN`.

## 0. Integrity check

| Command (Git Bash, pack root) | Output | Result |
|---|---|---|
| `sha256sum -c MANIFEST.sha256` | 23 lines `…: OK`, exit 0 | **PASS** |

Limitation (INFERENCE): the manifest sits in the same writable directory and does not cover itself, so it detects accidental change, not a same-user actor who rewrites both.

## 1. Time and resource feasibility

- RULE (as recorded in `REQUIREMENTS_LEDGER.md` DF-05; I did not re-fetch the page): window 26 Sep 16:00 UTC → 5 Oct 06:59 UTC. Arithmetic: 206 h 59 min wall-clock.
- RULE (`CLAUDE.md`): only Lucas authorizes branches, commits, pushes and environment changes. INFERENCE: throughput is bounded by Lucas's attention, not agent hours. Three seats' permission prompts and commit requests queue on one person, and kickoff is 00:00 SGT.
- UNKNOWN: whether three concurrent seats on one Claude subscription hit shared usage limits mid-window. Not measured; check usage before kickoff.
- INFERENCE: the pack's own gates (Sep 30 app + trace, Oct 2 full loop, Oct 4 freeze; `EXPERIMENT_PROTOCOL.md`) leave little slack, and the four official stages are UNKNOWN in size. Everything above "mandatory" must be pre-committed as cuttable.

| Tier | Item | Verdict (INFERENCE, conditional on official pack) |
|---|---|---|
| Mandatory | Official app core + all four official stages | Must fit; everything else yields to it |
| Mandatory | Genuine BAND run record with real handoffs | Fits if logged from hour 0; export method UNKNOWN (organizer Q5) |
| Mandatory | One real counterexample → repair → re-verify | Fits only if a test seam is designed into the app on day 1 |
| Differentiating | Artifact-bound acceptance record (digest manifest + fail-closed evaluator) | Fits as **ADVISORY** local tooling |
| Differentiating | *Genuinely enforced* promotion gate | Fits only if Lucas does the §5 account setup **before** kickoff; otherwise label ADVISORY |
| Conditional | Software twin, selective evidence invalidation, post-deploy observation, Tablekeeper run, 5-task baseline experiment, Alexa+/Nebius | Does not fit alongside the above |

**Cut order (first cut first):** (1) any Amazon/Nebius work inside the DF window; (2) post-deploy observation; (3) living twin and animated views → one static release-decision screen plus one counterexample trace; (4) selective invalidation → "any digest change invalidates all" (already the proposal's fallback); (5) Tablekeeper genericity run; (6) baseline experiment → one task, or after submission; (7) cryptographic signing → plain SHA-256 manifest + recorded human approval, labelled ADVISORY. **Never cut:** official stages, a runnable app, the real BAND run record, honest status labels.

## 2. Toolchain and platform risks on this machine

| Command | Output (abridged) | Result |
|---|---|---|
| `git --version` | `git version 2.54.0.windows.1` | PASS |
| `git rev-parse --is-inside-work-tree` | `fatal: not a git repository` | **FAIL** |
| `git config --system --get core.autocrlf` | `true` | PASS (risk R2) |
| `git config --global --get core.autocrlf` / `core.longpaths` / `core.hooksPath` | unset (exit 1) | PASS |
| `git config --global --get user.name` | `Lucas Tan` (email deliberately not recorded) | PASS |
| `node --version` / `npm --version` / `pnpm --version` | `v24.16.0` / `11.13.0` / `11.5.2` | PASS |
| `node -e "…require('node:sqlite')…"` | `node:sqlite ok 3.53.0` | PASS |
| `python --version`; `uv --version` | `Python 3.14.5` (GIL enabled, sqlite 3.50.4); `uv 0.11.19`; 3.12.10 also installed | PASS |
| `python -c "…find_spec…"` | pytest, fastapi, sqlalchemy, uvicorn present; **hypothesis, psycopg, playwright absent** | PASS (info) |
| `docker --version`; `psql --version`; `sqlite3 --version` | `command not found` ×3 | **FAIL** |
| `gh --version`; `gh auth status` | `2.100.0`; logged in `ihatecodingaaa` (keyring), scopes `gist, read:org, repo, workflow` (token masked) | PASS (risk R7) |
| `$PSVersionTable.PSVersion`; `pwsh --version` | `5.1.26100.9444`; not found | PASS |
| `Get-ExecutionPolicy -List` | Process `Bypass`, CurrentUser `RemoteSigned` | PASS |
| `LongPathsEnabled` (HKLM FileSystem) | `1` | PASS |
| `Win32_OperatingSystem` / `Win32_ComputerSystem` / `Get-PSDrive C` | Windows 11 Home build 26200; 16 logical CPUs; 31.4 GB RAM; 767.2 GB free | PASS |
| `wsl --status` | default `kali-linux`, WSL 2 | PASS |
| `whoami /groups`; UAC policy values | `BUILTIN\Administrators … Group used for deny only`; `EnableLUA 1`, `ConsentPromptBehaviorAdmin 5`, `PromptOnSecureDesktop 1` | PASS |
| `claude --version`; `jam --version`; `make`; `openssl`; `gpg`; `jq` | `2.1.280`; `0.4.10`; `4.4.1`; `3.5.6`; `2.4.9`; `1.8.2` | PASS |
| `cosign`, `go`, `java`, `dotnet`, `bun`, `deno`, `yarn` | not found | FAIL (info only) |

**Risks**

- **R1 No git repository** (INFERENCE). Nothing to roll back to, no per-seat worktrees, no commit or tree IDs to bind evidence to. `PREBUILD_REVIEW.md` Q5 cannot be met today. Needs Lucas to authorize a local repo and tag convention, at kickoff at the latest.
- **R2 CRLF** (INFERENCE). With `core.autocrlf=true`, working-tree bytes differ from index and Linux bytes. Hashing files on disk will not match hashes computed by judges or Linux CI, so the "change one byte → deny" beat can false-deny. Mitigation: repo-local `.gitattributes` (`* text=auto eol=lf`), and bind evidence to the git tree OID plus a built-artifact tarball digest, never to working-tree bytes.
- **R3 Shell divergence** (INFERENCE, not measured here). PowerShell 5.1 redirection can emit UTF-16/BOM output, and 5.1 has no `&&`. Write every evidence file from one runtime (node or python) with explicit bytes, and keep scripts in one shell.
- **R4 No Docker or Postgres.** If the official pack requires either, an approved install lands on day 1's critical path. Default to SQLite, which is built into both node 24 and python.
- **R5 Test libraries absent** (hypothesis or fast-check, playwright). Install project-locally at kickoff. Playwright's browser download adds to the rollback time budget.
- **R6 Windows file locking** (INFERENCE). Open SQLite files and running servers block replacement, so rollback must stop processes first.
- **R7 Owner GitHub token usable by every seat** (see §5).
- **R8 Commit attribution.** OFFICIAL: `attribution.commit` "Change or hide the trailer Claude Code adds to commits" [S8]. Observed: this session's harness instructs adding a `Co-Authored-By: Claude …` trailer, which conflicts with RULE `CLAUDE.md` (no Co-authored-by). Lucas must configure it (a settings change, his decision) or check before each push.
- **R9** `where python` lists the WindowsApps alias first. Pin with `.python-version` and a uv venv. Low risk.

## 3. Killer edge cases (Pocketful-style, conditional on the official pack)

| Case | Failure | Deterministic here? | How, and limits |
|---|---|---|---|
| Idempotent retry (same key twice; same key with a different payload; retry after commit when the response was lost) | Double debit | **YES** (INFERENCE) | Sequential replay plus a fault hook that fails after commit and before the response |
| Concurrent lost update / double spend | Negative balance or money created | **PARTIAL** | Deterministic only via a test seam (barrier between read and write) that forces the bad interleaving. Free-running load is probabilistic: report seed and iteration counts, not "reproduced". OFFICIAL: SQLite WAL allows "only one writer at a time" [S11], so it reproduces app-level read-then-write races but **not** DB isolation anomalies (e.g. write skew); those need Postgres, which is absent → NOT reproducible now |
| Decimals | Rounding drift, float contamination | **YES** | Probe below. OFFICIAL: SQLite has no DECIMAL class; NUMERIC text converts to INTEGER/REAL [S10]. Use integer minor units, or TEXT plus a decimal type. Rounding mode and currency exponent are UNKNOWN until the pack |
| Atomic failure | Debit without credit | **YES** for app-level faults (exception between legs; process killed at a hook) | Power loss / OS-crash durability cannot be genuinely reproduced → UNKNOWN; don't claim it |
| Also likely (INFERENCE) | Access to another user's wallet; zero, negative or huge amounts; self-transfer; ledger ordering ties (order by sequence, not timestamp) | YES | — |

Probe (**PASS**, ran). Command: `python -c "<in-memory probe: create table t(n NUMERIC, r REAL, x TEXT); insert '0.10' into each; sum three cast('0.1' as numeric)>"`. Output: `(0.1, 'real', 0.1, 'real', '0.10', 'text')` and `sum of NUMERIC 0.1 x3 = 0.30000000000000004`. A `DECIMAL`-declared SQLite column silently becomes binary floating point.

## 4. Keeping a runnable application at every checkpoint

INFERENCE design; depends on R1.

1. **Separate the product app from the factory tooling.** The app must start and pass its smoke test with the gate, evidence store and UI extras absent (feature flags default off). A broken gate must never break the app.
2. **One gate command**: frozen-lockfile install, lint, unit, acceptance, smoke. "Green" means exit 0 on a clean checkout.
3. **Checkpoints**: annotated tag `green-NNN`, created only after the gate passes on a clean checkout. The tag message records tree OID, lockfile digest, command and exit code.
4. **Seat isolation**: one worktree per seat. The verifier tests a clean checkout of the tag, never the developer's worktree.
5. **Rollback within 15 minutes**: stop processes → `git worktree add <dir> green-NNN` → install from lockfile using the local cache → seed → smoke. The git steps take seconds; install and seed use up the budget. Actual time on this machine is **UNKNOWN**. Run a timed drill on day 1, repeat it daily, record it as evidence, and don't claim "≤15 min" until a drill passes.
6. **Daily checkpoint**: run the gate on the latest green tag, not just HEAD.

## 5. Actions that need external enforcement

Context (checks in §2): every seat runs as Windows user `lucas` with a filtered admin token, and elevation needs a UAC prompt on the secure desktop. Anything `lucas` can read or write, every seat can too. OFFICIAL: Claude Code's OS sandbox — "Native Windows is not supported" [S7]. OFFICIAL: managed settings (`C:\Program Files\ClaudeCode\managed-settings.json`, not present here) override user and project settings, but "a developer who is an administrator on the machine can edit the managed source" and they "bind Claude Code only" [S9]. INFERENCE: Bash deny patterns can be sidestepped by indirect execution (python or node subprocesses).

| Action | Mechanism feasible here | Status |
|---|---|---|
| Push, create repos, change visibility, edit workflows | The owner token (`repo`, `workflow`) is in the user keyring. Take it out of the seats' reach: log out for the build window and have Lucas push from a separate session, **or** run seats under a separate standard Windows account without gh/vercel credentials. Server rules don't help against the owner's token: admins bypass branch protection by default [S3]; private-repo protected branches are a Pro feature [S2]; Lucas's plan is UNKNOWN (not queried) | **ADVISORY** today; enforceable after separating credentials |
| Staging deploy / release token | Gateway process and signing key under a **separate Windows account**, key file restricted to that account, seats reach it only over HTTP. GitHub environment required reviewers are not available for private repos on Free, Pro or Team [S4] | **ADVISORY** today; feasible with Lucas's admin setup |
| "Verifier-signed" evidence | Same separate-account signer. GitHub attestations: private-repo plan availability UNKNOWN (not confirmed by me; [S5] confirms private repos use a GitHub instance with no transparency log) | **ADVISORY** today |
| Sealed challenger tests | Store and run them under the separate account, black-box against the built artifact | **ADVISORY** today; feasible |
| Mandate or policy edits | Prevention infeasible for the same user (the owner can rewrite ACLs; INFERENCE). Detection feasible: digests held outside agent write scope | **DETECT-ONLY** |
| Forbidden shell or network access | No OS sandbox on native Windows [S7]. The WSL2 sandbox would move all seats into WSL and require re-onboarding BAND identities, which conflicts with `BAND_RUNBOOK.md` | **INFEASIBLE** in the DF window → ADVISORY |
| No Co-authored-by trailer | `attribution` setting [S8] plus Lucas's `git log -1 --format=full` before each push; server-side commit-metadata rules UNKNOWN | **PARTIAL** |
| Spend caps | Provider hard caps UNKNOWN; AWS Budgets alerts rather than stops (blueprint §11) | **ADVISORY** |
| Claude Code deny rules via managed settings | Changing them needs UAC elevation (a human click), but indirect execution bypasses them | **PARTIAL** (defense in depth, not a boundary) |

HYPOTHESIS: one separate standard Windows account holding the deploy/signing key and challenger suite is the single highest-leverage real boundary available on Windows 11 Home. Lucas must create it, before kickoff, as tool readiness. Without it, every "enforced" claim in the demo must read ADVISORY.

## 6. Where post-test artifact checks must occur

| Point | What is recomputed | Bypass on this machine |
|---|---|---|
| Runner start **and** end | Tree OID, lockfile digest, test-definition digest, config-allowlist digest; the end check catches mutation during the run | Runner code is editable by any seat → ADVISORY unless the runner lives in the separate account |
| Human approval | Digests recomputed from the tag and shown to Lucas, never copied from an agent message | Approving a digest pasted into chat |
| Deploy gateway | The gateway copies the artifact into its own directory, packs a tarball, hashes it, and deploys **that** tarball (no check-then-use swap) | A same-user gateway's key and state are editable → ADVISORY |
| Lockfile | Frozen install; lockfile digest recorded | Postinstall scripts; platform-specific optional dependencies (same lockfile, different installed bytes on Windows vs Linux); runtime network fetches; global tools |
| Config / environment | Hash of a declared allowlist of keys | Code reading undeclared environment variables, remote flags, locale or timezone |
| Runtime | node and python versions recorded | PATH shadowing (two Pythons on PATH here) |
| Post-deploy | `/version` reporting the digest | Self-reported by the app → corroboration only |

## 7. Research-only spike

**UNKNOWN / NOT_RUN.** It is not in the pack, and `CLAUDE.md` forbids searching outside it. Lucas would need to provide the path or an archive, its report, a commit or digest, its license and authorship, and explicit permission for a seat to read that path. Its code must not be imported.

## 8. Pack inconsistencies (factual)

- `README.md` cites `THREE_HACKATHON_RESEARCH_AND_EXECUTION_BLUEPRINT_2026-09-24.md`, but the pack file is `docs/PRIOR_THREE_HACKATHON_RESEARCH_BLUEPRINT_2026-09-24.md`.
- The blueprint (§9A) names `competition/rubric-ledger.md`; the pack uses `competition/REQUIREMENTS_LEDGER.md`.
- `PREBUILD_REVIEW.md` Q5 requires rollback to a green baseline, but no repository exists (R1).
- `ORGANIZER_QUESTIONS.md` has no sent or unresolved dates, which the README exit criteria require.
- `CLAUDE.md` bans Co-authored-by trailers, but the harness adds attribution unless configured (R8).

## 9. Decisions for Lucas (via the architect)

1. Authorize a local git repo and tag convention (before or at kickoff).
2. Create a separate Windows account for gateway, signing and challenger suite, or accept ADVISORY labels.
3. Configure `attribution` for this project, or accept a manual pre-push check.
4. Pre-approve project-local dependency installs at kickoff (test libraries, possibly a database).
5. Provide the spike's location, or accept UNKNOWN.

## Sources (all accessed 2026-09-23 UTC)

- [S2] GitHub's plans — https://docs.github.com/en/get-started/learning-about-github/githubs-plans
- [S3] About protected branches — https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches
- [S4] Deployments and environments — https://docs.github.com/en/actions/reference/workflows-and-actions/deployments-and-environments
- [S5] Artifact attestations (concepts) — https://docs.github.com/en/actions/concepts/security/artifact-attestations
- [S6] About rulesets (states Team/Enterprise availability; personal-plan applicability UNKNOWN) — https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets
- [S7] Claude Code sandboxing — https://code.claude.com/docs/en/sandboxing
- [S8] Claude Code settings reference (`attribution`) — https://code.claude.com/docs/en/settings-reference
- [S9] Claude Code managed settings — https://code.claude.com/docs/en/managed-settings
- [S10] SQLite datatypes — https://www.sqlite.org/datatype3.html
- [S11] SQLite WAL — https://www.sqlite.org/wal.html
- [S1] Pack files: as verified by `MANIFEST.sha256` (§0). The build-window dates come from `REQUIREMENTS_LEDGER.md` DF-05; the LabLab page was not re-fetched (NOT_RUN).
