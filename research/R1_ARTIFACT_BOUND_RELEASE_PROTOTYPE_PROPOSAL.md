# R1 — Research prototype proposal: artifact-bound evidence and fail-closed release

**Author:** Architect `2201904f/architect-x7jh` · **Date:** 2026-09-24 SGT · **Status:** PROPOSAL ONLY. No code exists; nothing is installed.
**Scope:** a domain-independent research prototype developed **separately** from the Dark Factory competition source tree. It uses no Pocketful or track-specific content. Its code must not be copied into a competition build unless the organizer allows it (ledger DF-06, UNKNOWN).
**Review status:** Architect-authored and **not independently reviewed**. The negative controls in §5 are this seat's own design-level checks, not the Independent Verifier's withheld tests. The Phase 0 adversarial review remains **INCOMPLETE**.

## 1. What the experiment must show

| # | Objective | Falsifiable claim |
|---|---|---|
| O1 | Requirements bound to exact artifacts | Every evidence record names requirement IDs, the requirements-file digest and the artifact digest; the gate rejects evidence that lacks any of them |
| O2 | Reproducible independent verification | A second, independent rebuild and re-run from a clean checkout produces the **same artifact digest and the same verdict** |
| O3 | Evidence invalidation after change | A change to artifact, requirements, test definition or policy digest makes every dependent evidence record and approval unusable. The rule is conservative: invalidate everything, no selective reuse |
| O4 | Fail-closed release | Any missing, unknown, unverifiable, expired or erroring input yields **DENY** with a reason code, never ALLOW |
| O5 | Stale evidence and changes between verification and use | The gate deploys exactly the bytes it hashed. Approvals are bound to digest, environment, expiry and a single-use nonce |

Non-goals: agent orchestration, a UI, an evidence graph, cloud deployment, production security claims, and any Dark Factory domain logic.

## 2. Smallest experimental architecture

The subject is a deliberately trivial, domain-neutral program: a small text-normalizing CLI with three written requirements (`REQ-1…3`). It lives in a **separate local repository** (proposed `C:\Users\lucas\Projects\forge-r1`, which needs Lucas's approval).

```
requirements.yaml ─┐                         (verifier-owned) tests/ ─┐
source (git tree) ─┴─► [C2 build] ─► artifact.tar ─sha256─► [C3 verify] ─► evidence.json + .sig
                                          │                                        │
                                          ▼                                        ▼
                         [C4 human approval: signs {artifact, requirements, evidence[], policy,
                                                     env, expires_at, nonce}]
                                          │
                                          ▼
     [C5 gate]  copy artifact into gate-owned dir → hash the COPY → verify signatures →
                OPA default-deny policy → consume nonce → deploy THAT copy → receipt
```

| Component | Minimal mechanism |
|---|---|
| C1 Subject | Toy program, `requirements.yaml` and a verifier-owned `tests/` directory, all in git |
| C2 Build | `git archive --format=tar <tree>` → `artifact.tar` → SHA-256. Uncompressed tar, because gzip embeds a timestamp. Record the git tree OID as well |
| C3 Verify | Extract the artifact into a fresh temporary directory and run the frozen suite with pytest. Emit evidence as an **in-toto Statement v1** (`_type: https://in-toto.io/Statement/v1`; subject = artifact matched by digest). Our own `predicateType` carries `requirement_ids`, `requirements_sha256`, `testdef_sha256`, `runner_sha256`, command, environment, exit code, `stdout_sha256`, `stderr_sha256`, result and timestamps. Sign with `ssh-keygen -Y sign -n forge-evidence` using the verifier's key |
| C4 Approval | Lucas signs an approval request (`-n forge-approval`) with his own passphrase-protected key, which is never loaded into an agent session |
| C5 Gate | Copy, hash, verify signatures against a gate-owned `allowed_signers` file, then `opa eval --fail -d policy.rego -i input.json data.release.allow`. OPA exits non-zero on an undefined result, so the gate defaults to deny. Record nonce consumption in an append-only log. "Deploy" means extracting the hashed copy into `staging/` and writing a receipt that holds the deployed digest |

## 3. Trust boundaries (each tier is measured and reported separately)

| Tier | Setup | What can honestly be claimed |
|---|---|---|
| **T0** | Everything runs as Windows user `lucas`, including the agents | Detection of stale, mismatched or missing evidence. **ADVISORY** against a deliberate same-user forger, who can rewrite keys, logs and policy |
| **T1** | The gate, `allowed_signers`, policy, nonce log and `staging/` belong to a **separate standard Windows account**; agents keep running as `lucas` | "Enforced **for the named staging target**", but only for the negative tests that actually show an OS-level denial. Residual risks: a human-approved UAC elevation, and custody of Lucas's key |
| Always out of scope | Tool sandboxing of agents (the Claude Code sandbox: "Native Windows is not supported", verified 2026-09-23); network egress; hardware-backed keys | Stated as limitations, never claimed |

The verifier is independent only in that it has its own key and owns the test definitions. It shares the machine and the model family with the other seats, and that limitation must be disclosed.

## 4. Dependencies (nothing installed; each install needs Lucas's approval)

| Status | Item | Use |
|---|---|---|
| Present (checked 2026-09-24) | Python 3.12.10 and 3.14.5, pytest, git 2.54, OpenSSH 10.3p1 (`ssh-keygen -Y sign/verify`), openssl 3.5.6, uv 0.11.19 | Build, test, sign, hash |
| Install, project-local, pinned and lockfiled | **Hypothesis** | Stateful property tests of the gate |
| Install, checksum-verified single binary | **Open Policy Agent (`opa`)** | Default-deny release policy, kept apart from agent-editable code |
| Optional, later | in-toto reference implementation, Sigstore `cosign` with a DSSE envelope, SLSA provenance predicates | Only if R1 succeeds with the minimal stack |

Licenses and exact versions are to be **confirmed at install time from each project's primary source**; nothing here asserts them. The prototype uses no cloud services, paid services or network calls at runtime.

## 5. Pre-registered test cases

**Positive controls**

| ID | Case | Expected result |
|---|---|---|
| P1 | build → verify → approve → release | ALLOW; receipt digest equals approved digest |
| P2 | Independent rebuild and re-verify from a clean clone in a second directory (second account at T1), twice | Identical artifact digest and verdict |

**Negative controls.** Each must be denied with the stated reason; any ALLOW is a failure.

| ID | Case | Expected reason |
|---|---|---|
| N1 | One byte of the artifact changed after approval | `ARTIFACT_DIGEST_MISMATCH` |
| N2 | `requirements.yaml` changed after verification | `EVIDENCE_STALE_REQUIREMENTS` |
| N3 | Test definitions changed after verification | `EVIDENCE_STALE_TESTDEF` |
| N4 | Evidence record edited after signing (result or output hash) | `SIGNATURE_INVALID` |
| N5 | Evidence signed by a key not in `allowed_signers`, e.g. the builder's | `SIGNER_NOT_ALLOWED` |
| N6 | No evidence for one required REQ | `MISSING_EVIDENCE` |
| N7 | Approval past `expires_at` | `APPROVAL_EXPIRED` |
| N8 | Approval nonce reused, or approval for environment A used on environment B | `NONCE_REPLAYED` / `SCOPE_MISMATCH` |
| N9 | Artifact file swapped after the gate hashed its copy | The deployed bytes equal the hashed copy. Failure means any code path re-reads the original file |
| N10 | OPA missing or erroring, `allowed_signers` unreadable, or the clock unavailable | `GATE_DEPENDENCY_ERROR` |
| N11 | Policy file changed after approval | `POLICY_CHANGED` |
| N12 | An agent-account write to gate-owned files (T1 only) | OS access denied. At T0 the write is expected to succeed, and the result is recorded as ADVISORY |

**Property test (Hypothesis, stateful).** Generate random sequences of {mutate artifact, mutate requirements, mutate tests, re-verify, re-approve, release, advance clock}, and assert this invariant after every step:

> ALLOW ⇒ the deployed digest equals the digest in a validly signed, unexpired, unconsumed approval whose evidence covers every required REQ with PASS, and every one of those digests matches the current requirements, test definitions and policy.

Report the seed, the number of generated sequences and the violations found. This is not a proof.

## 6. How we decide whether the experiment works

- **Pass:** P1 and P2 pass, and **all N1–N11 DENY with the expected reason code** at T0, with outputs recorded. A single false ALLOW fails the objective it tests. Zero property-test violations over the reported number of sequences.
- **Reproducibility (O2):** report the count of rebuilds with identical digests out of total rebuilds. Any mismatch is investigated and reported, not averaged away.
- **False denies:** report how often an unchanged artifact is denied across repeated runs. The target is 0.
- **Enforcement table:** for each negative test, report whether it was *enforced* (a T1 OS denial was observed), merely *detected* (the gate denied it but the attack would have succeeded at T0), or *advisory*.
- **Descriptive only:** gate wall-clock time and the human's approval time, reported as measurements, not claims.
- **Evidence for every run:** command, environment, tree OID, all digests and hashed outputs, committed to the prototype repo.
- **Kill or reduce criteria:** if T1 cannot be set up, report ADVISORY only. If the tar build is not deterministic, bind to the git tree OID and report the gap. If R1 cannot reach the pass criteria, differentiation claims in the product pack must shrink accordingly (`docs/PRODUCT_THESIS.md` decision rule).

## 7. Reuse versus build

**Reuse:**
- git content addressing (tree OIDs, `git archive`)
- OpenSSH signatures (`ssh-keygen -Y`)
- the in-toto Statement v1 envelope for evidence
- OPA and Rego for the default-deny decision
- Hypothesis and pytest
- Windows local accounts and NTFS ACLs as the T1 boundary
- the `sha256sum` manifest format

**Do not build from scratch:**
- cryptographic primitives or signature formats (no HMAC in the agents' own process as a trust anchor)
- key management
- a policy language
- a transparency log
- a sandbox
- a CI system
- an evidence-graph database or UI (use conservative whole-set invalidation instead)
- a test framework

**Only thin glue is new:** the build and verify scripts, the evidence predicate schema, the approval request schema, the gate's copy-hash-verify-decide-deploy sequence, and the Rego policy.

## 8. Decisions needed from Lucas before any code

1. Approve a separate local repository (proposed `forge-r1`) outside `dark-factory`, with no GitHub remote.
2. Approve project-local installs of Hypothesis and OPA.
3. Decide whether to set up the T1 separate Windows account. Without it, R1 reports T0 (ADVISORY) results only.
4. Create his own passphrase-protected approval signing key. Only the public key goes to the gate.
5. Confirm that R1 stays research-only and is not carried into any competition build unless DF-06 allows it.
6. Optionally ask the Independent Verifier to review §5 once its restriction is resolved. That would count as a separate review, not as completion of the withheld Phase 0 items.
