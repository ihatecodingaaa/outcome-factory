# Product thesis, personas and claim boundaries

## User and job-to-be-done (hypothesis)

**Initial user:** one senior engineer or tech lead reviewing AI-generated changes in a small team that owns transaction-critical backend services. They already use Claude Code/Codex/CI. We do **not** ask them to replace their entire developer stack; we orchestrate those tools and make a consequential release decision inspectable.

**Job:** "Show me whether this exact version of my new consequential feature (e.g. payment or booking) satisfies the few properties I cannot afford to get wrong, what was attempted to falsify it, and what has changed since I approved it."

**Evidence gap:** A green test suite is a property of a test run; it is not permission to deploy any later commit. LLM statements about completed checks aren't independently verifiable evidence. Novelty is **an integrated, fail-closed human authorization flow tied to an artifact, explicit bounded assertions and actual observed agent execution**—not a claim no other product implements these primitives.

**Differentiate against:** GitHub Spec Kit (structured spec and convergence), OpenHands Verification Stack (agent critic + repo QA), DUBSOpenHub Dark Factory (sealed QA, cross-family models, red team, outcome evaluation), AWS AgentCore (actual policy and bounded identity), Sentry Seer (incident investigation/repair). See `docs/COMPETITOR_MATRIX.md`.

## First end-to-end demo

An AI team builds a small, usable clean-room target application. A controlled but genuine concurrency/retry defect survives initial development checks. An independent verifier discovers a minimal failing sequence using a harness that runs against real backend behavior, not prewritten narrative text. The developer repairs it. The gate issues a **bounded release authorization** ONLY for the code+test+spec digests that were actually evaluated and human-approved. Changing the artifact invalidates authorization. The consumer app stays polished and functional.

**Before claiming it:** publish real seed, command, environment, failing trace, fix diff, green retest, gate rejection, final artifact digest and limitations.

## Product wedge and enterprise extension

Start with release-critical verification for AI-assisted changes in transaction-sensitive APIs. Future plausible enterprise upgrades: verified branch protection/CICD webhook integration, signed attestations from independent trust domains, policy-as-code, SSO/RBAC, reproducible sandbox provenance, migration-specific rollback proof, observability and policy-driven exceptions. **Do not claim enterprise production readiness during the hackathon.**

## Failure modes that kill this idea

- A conventional coding agent + default test suite identifies/reproduces the same defects with equivalent review burden.
- Gate can be bypassed by a different deployment path while UI says 'enforced'.
- Test author and implementer share assumptions and synthetic counterexamples are not executed.
- A beautiful standalone platform consumes time while Pocketful or the official graded stages remain incomplete.
- Alexa+ has no independently useful natural conversation task for the actual person using it.
- The Nebius edition is just a decorative model API call with no genuine Sandbox execution.

**Decision rule:** show an empirical advantage on at least one preregistered consequential task or reduce differentiation claims to the honest integration/UX improvements shown. No invented accuracy rates, company endorsements, customer interviews or revenue forecasts.
