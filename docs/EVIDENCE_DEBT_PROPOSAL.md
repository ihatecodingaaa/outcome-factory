# Research direction: Evidence Debt and the living claim-dependency graph

**Proposed differentiator to test, not unique IP claimed.** Formal verification, branch protection, signed artifact attestation, hidden QA and spec-driven dev already exist. Our proposed integrative experience is a *live debt register* answering which product claims no longer have current supporting evidence after an agent edits code, dependencies, configuration or specification.

## Why it matters

Traditional status badges are often displayed as flat pass/fail. A tested claim is a relation between a specific assertion, test definition, observed environment and one precisely identified artifact. A later change may invalidate some or all of those dependencies. Trust should not survive solely because someone says the change was small.

## How to model V1 without overclaiming

- Nodes: requirement, implementation surface, dependency, test, test runner, execution artifact, evidence statement, approval and released artifact.
- Edges: implemented_by, tested_by, executed_in, derived_from, approved_for, depends_on.
- Every graph node with executable meaning has exact content digest or immutable identifier. An LLM may propose edges; **deterministic conservative rules** decide which claims become stale.
- On *any* changed build-artifact digest, **previous release approval becomes invalid**, even if evidence for some unchanged modules is reusable for internal review. Stale UI immediately names impacted claims and marks unproven dependencies `UNKNOWN`.
- Selective evidence re-use is allowed only for scope whose dependency graph is complete under a documented closed-world assumption; if analysis is incomplete, invalidate all required release claims instead.
- Show "3 claims now stale; 2 untested; 1 previously passed" only when backed by actual graph records. In MVP, no artificial confidence score.

## Sharpest demo beat

Immediately after a full recorded successful test and Lucas's staging approval, modify one implementation byte (or dependency-lock entry). Verify deploy gateway reads the new artifact digest and refuses old approval. Graph updates a visible, specifically scoped debt card. One command reruns required tests on the new artifact; independent verifier issues new bounded evidence; owner may authorize new digest.

## Negative test conditions

1. Modify a transitive dependency not listed in the supplied test plan: conservative invalidation required.
2. Reuse a green run against a different specification version: deny.
3. LLM says a claim is unaffected but dependency coverage is partial: mark UNKNOWN.
4. Artifact digest changes without Git commit change (dirty worktree or nondeterministic build): deny old approval.
5. Signed provenance authentic but test contract incomplete: metadata verified, **claim acceptance still blocked**.

**Benchmark against:** GitHub artifact attestations, Sigstore/in-toto, SLSA, OpenHands verification, DUBSOpenHub dark-factory and GitHub Spec Kit. Do not market this as the first system with an evidence graph.
