# Capability matrix — public documented claims, not a ranking

**Source date:** 24 September 2026. This is a *capability overlap matrix* based on public claims, NOT verified head-to-head benchmark performance. Unknown does not mean absent. Re-check before public comparative statements.

| Existing system | Documented overlapping features | What remains to test, not assume | Source |
|---|---|---|---|
| DUBSOpenHub Dark Factory | Eight specialists, isolated worktrees, sealed cross-family QA, ambiguity gate, red team, outcome evaluator, tournaments | Can its reported artifacts be bound to an externally enforced single deploy gate across changed git states? Run adversarial mutation comparison if feasible. | https://github.com/DUBSOpenHub/dark-factory |
| OpenHands verification stack | Agent-level critic, code review skill, QA on actual functionality and iterative refinement | What provenance, artifact/release binding and end-user workflow are actually enforced in deployed configurations? | https://www.openhands.dev/blog/20260506-the-verification-stack |
| GitHub Spec Kit | Specify → Plan → Tasks → Implement → Converge; bug-fix and idea-assessment workflows; extension ecosystem | How does exact-artifact authorization integrate with specific external CI policy? | https://github.github.com/spec-kit/ |
| Amazon AgentCore | Identity, policy-based tool authorization, gateway runtime and external guardrails, if configured correctly | When does the only deploy route truly pass through policy? Can FORGE use it rather than rebuild it? | https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/runtime-security-best-practices.html |
| Sentry Seer | AI issue investigation and remediation capabilities | Our work must add a pre-release contract or cross-agent causal evidence rather than rebrand incident triage | https://docs.sentry.io/product/ai-in-sentry/seer/ |
| BAND | Existing agent identity, messaging, rooms, task/usage visibility and CLI | Avoid building a duplicate coordination chat UI; submit a genuine recorded BAND run | https://docs.band.ai/band-desktop |
| MCP Apps | Inline interactive UI for MCP tools on compliant clients, plus skills and examples | Alexa+ compatibility is not automatic; host support must be demonstrated in allowed simulator | https://github.com/modelcontextprotocol/ext-apps |

## Community observations (qualitative only)

- Developers complain about AI code that reports 'done' when manual clicking finds failures. Sample anecdote: https://www.reddit.com/r/ClaudeCode/comments/1wdgt78/how_are_you_verifying_claude_codes_changes/
- Developers complain review volume grows as AI writes larger PRs. Such posts are self-selected, sometimes promotional; corroborate with actual task testing: https://www.reddit.com/r/ClaudeCode/comments/1ujwjm2/the_code_review_gap_is_getting_dangerous_ai/
- 2025 Stack Overflow AI survey is a dated, broader sample but still survey-specific: https://survey.stackoverflow.co/2025/ai

## Our differentiator to test

**Artifact-bound acceptance *in the full factory-to-deployment product experience***. Its pieces are not new. The research question is whether our design measurably reduces *time and uncertainty required for a human to authorize a consequential change*, without promising impossible universal safety. Independent reviewer should attempt to falsify this before proceeding.

## Important adjacent incumbent, verified after initial matrix

| Existing system | Documented overlapping features | What remains to test, not assume | Source |
|---|---|---|---|
| Sigstore / in-toto / GitHub artifact attestations | Cryptographically signed provenance and integrity assertions bound to software artifacts; verify during deployment; GitHub public repository built-in path. **Private repo use is plan-restricted.** | Instead of rebuilding attestation tech, focus on *dynamic claim-to-code invalidation*, a bounded reviewer experience and a real mandatory release decision; validate any incremental human benefit experimentally. | https://docs.sigstore.dev/cosign/verifying/attestation/ ; https://docs.github.com/en/actions/concepts/security/artifact-attestations |
| joeyfezster/dark-factory | Opaque-code behavioral holdout testing; deterministic gates; semantic reviewers; human review pack | Our externalized artifact/contract versioning plus accessible real-failure decision UX must be shown to improve a decision, not just renamed as proprietary proof. | https://github.com/joeyfezster/dark-factory |
