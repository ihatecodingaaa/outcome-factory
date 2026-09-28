# Outcome Factory | Phase-0 engineering pack

**Owner:** Lucas (`ihatecodingaaa`)\
**Prepared:** 24 September 2026 (SGT)\
**Status:** pre-kickoff design pack. The organizer's official kickoff package has since been released; its baseline is recorded in `competition/REQUIREMENTS_LEDGER.md`. This is **not** a completed hackathon application or a verified claim of performance.\
**Prior baseline:** `docs/PRIOR_THREE_HACKATHON_RESEARCH_BLUEPRINT_2026-09-24.md`; use that with this pack.

## Decision

Work toward **Outcome Factory**, an agent-independent release assurance layer that uses BAND to coordinate a real autonomous build and requires *externally verifiable evidence about the exact artifact* before promotion. The killer demonstration is a realistic failure discovered and replayed, not an animation of agent cooperation.

**Critical constraint:** the organizer's released package, at the baseline recorded in `competition/REQUIREMENTS_LEDGER.md`, governs Dark Factory work wherever this pre-kickoff pack differs from it. Code in a graded stage folder must come from the band's own run (kickoff audit R-14), so the research spike never moves into a competition source tree.

**Owner of decisions:** Lucas. Other agent seats can research, propose and challenge, and carry out the local work that a run authorization from Lucas covers (see `CLAUDE.md`); only Lucas authorizes permissions, spending, irreversible mutations and release.

## Start here

1. Read `competition/REQUIREMENTS_LEDGER.md`, `competition/ORGANIZER_QUESTIONS.md` and `docs/PRODUCT_THESIS.md`.
2. Review `docs/ARCHITECTURE.md`, `docs/THREAT_MODEL.md` and `docs/ADRS.md`.
3. Load generic BAND role mandates from `mandates/` *only in the designated hackathon collaboration*; the pre-connected seats listed in `operations/BAND_RUNBOOK.md` already exist.
4. Done before kickoff (Phase 0): the **read-only** design review in the existing BAND room, run with `operations/CLAUDE_ARCHITECT_PROMPT.md`. Its results, including the incomplete Verifier review, are in `reviews/phase0/PHASE0_READINESS_REPORT.md`.
5. Use `experiments/EXPERIMENT_PROTOCOL.md` to decide what would falsify the core thesis. Don't claim superiority until comparative measurements exist.
6. Kickoff has happened and the official package is recorded in the ledger; application code comes only from the factory's runs. The deliverable is the factory + its actual run + the resulting clone.

## Scope ladder

**Mandatory first:** compliant BAND run + official challenge app + independent counterexample and repair if supported by final rules.\
**Differentiating second:** signed, artifact-bound acceptance record and genuinely enforced fail-closed promotion in a safe test environment.\
**Conditional later:** interactive software twin and post-deploy observation; Alexa+ task-native on-call experience if it passes a user-task test; Nebius runtime integration and measured NVIDIA-model comparisons.

**Not in v1:** general autonomous production privileges, customer financial data, own LLM training, global multi-tenant IAM, blockchain, claimed formal proof of the whole app, fabricated reliability/benchmark percentages.

## Repos and release policy

Keep `C:\Users\lucas\Projects\dark-factory` as the working directory and create a **new private** `ihatecodingaaa` repository after owner approval. ChatGPT's existing GitHub connector can currently access other private repos but new-repo visibility must be verified. Local commits use Lucas's verified Git identity, except that seat commits use the seat's own identity (see `CLAUDE.md`); no commit carries a `Co-authored-by` trailer. Disclose AI assistance truthfully in competition submissions.

**Nebius requires a public, fully runnable, open-source submission**, unlike Lucas's preferred private canonical repo. Plan a sanitized, licensed public mirror containing all necessary functional code. If unwilling to release it, do not enter Nebius while claiming compliance. See `operations/GIT_AND_IP.md`.

## Exit criteria for this preparation stage

- Organizer questions sent or marked unresolved with dates.
- Each published rule has an owner, link, verification target and dated status.
- All four mandates explicitly prohibit self-escalation and fabrication.
- Diagram and trust boundaries reviewed independently; significant disagreement recorded.
- A frozen first-user/task thesis, demo beat sheet, five falsification cases and research-only spike report.
- Fresh BAND sessions can reattach to existing peers **without creating new identities**.

## Evidence language

`PASS` means a particular check passed against a particular subject. It does **not** mean a subsystem is 'safe', a feature is perfect, or a production outcome is guaranteed. `NOT_RUN`, `FAILED`, `BLOCKED`, and `UNKNOWN` are first-class states. If an external permission gate is not wired into the only deploy path, report **advisory only** rather than 'enforced'.
