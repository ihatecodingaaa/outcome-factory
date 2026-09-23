# Architecture decision register

## ADR-001: Initial wedge = artifact-bound acceptance, not general coding swarm
**Status:** proposed 24 Sep. **Reason:** Multi-agent planning, hidden tests and automated repair already exist. Novelty needs an empirical user benefit. **Test:** Can an engineer inspect/reject stale approval in <2 minutes using real recorded evidence? **Reversal:** If same workflow is well covered by existing competitors, narrow to target-domain verification tooling.

## ADR-002: Independent verifier cannot issue production approval
**Status:** proposed. **Reason:** Builder/verifier/human authority belong to separate trust domains. **Mechanism:** verifier signs bounded evidence; human signs reviewed release request; external gateway enforces. **Residual risk:** compromised verifier key/test environment can lie; HMAC spike offers no true isolation.

## ADR-003: No forced formal proof for every task
**Status:** proposed. **Reason:** useful proofs depend on explicit bounded models, safety assumptions and checker coverage. **Mechanism:** property/stateful tests for transaction invariants; browser tests for UX; model checking only if transparent about bounded state. **Non-claim:** 'zero unsafe reachable states' for the entire app.

## ADR-004: BAND's run is first-class evidence, not the sole evidence
**Status:** proposed. **Reason:** [INFERENCE; DF-03 judging criteria are UNKNOWN until the official pack] judges are likely to look for meaningful agent collaboration, yet BAND chat logs alone cannot demonstrate test execution or policy enforcement. **Mechanism:** embed room/work IDs in evidence manifest, reference hashes of executed artifacts and real commands.

## ADR-005: One core, sponsor-native extensions only if independently compelling
**Status:** provisional. Dark Factory = clone and factory; Amazon = *task-native* Alexa+ accessibility/context/incident experience with real MCP or disclosed simulation; Nebius = live open-model + Sandbox execution + public complete source. **Reversal:** Amazon's UX fails independent task validation by Oct 8 -> rework the interaction even if it becomes a separate presentation layer.

## ADR-006: Reuse established attestations; innovate in evidence invalidation and decision UX
**Status:** proposed. **Reason:** Sigstore/in-toto, GitHub artifact attestations and SLSA already bind build provenance to artifacts; invented signatures aren't differentiation. **Implementation target:** existing verifiable provenance where supported, a release decision policy bound to exact tested artifact+contract, an evidence-dependency graph marking claims stale when relevant code/contracts change, human-legible failed counterexamples, and an actually enforced staging gate. **Limit:** A broad code change may invalidate all evidence conservatively; selective invalidation must not silently overlook dependencies. **Sources:** https://docs.sigstore.dev/cosign/verifying/attestation/ and https://docs.github.com/en/actions/concepts/security/artifact-attestations . Private GitHub Free/Pro/Team attestation limitations require choosing a compatible alternative until public OSS release.
