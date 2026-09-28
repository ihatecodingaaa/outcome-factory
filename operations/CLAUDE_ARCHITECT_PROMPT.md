# Paste into EXISTING Dark Factory Architect Claude Code session

> **Historical, pre-kickoff (24 September 2026):** this prompt ran the Phase 0 review, when the room had three seats and `mandates/` held three files. There are now four seats, each with a mandate; do not reuse this prompt after kickoff.

We are performing a **PRE-KICKOFF READ-ONLY DESIGN REVIEW** for Lucas's single-human entry across Dark Factory, Amazon Alexa+, and Nebius/NVIDIA. BAND's existing three-agent room and identities must be reused; do not create new seats or rooms. First read the entirety of this pack (`README.md`, competition ledger/questions, product thesis, competitor matrix, architecture, threat model, experiment protocol, all three mandates, UX storyboard) plus the previously saved Three-Hackathon Research and Execution Blueprint if locally available.

Scope: design/research only. DO NOT implement Pocketful, challenge-specific tests, challenge-stage assumptions, AWS or Nebius deployments, or code that would enter a competition build until organizer pre-build rules are clarified or kickoff begins. DO NOT push to GitHub, change global Claude settings, install plugins, create external resources, or incur spend.

Coordinate these **separate** tasks in the existing BAND room:

1. ARCHITECT: outline the smallest viable real BAND factory-to-Pocketful acceptance loop *conditional on the official challenge pack*; identify architecture-decision disagreements and all sources/unknowns. Keep generic role mandates genuinely domain-independent.
2. DEVELOPER: independently critique resource/time feasibility, toolchain/platform risks, likely killer edge cases, how to keep a runnable application, which actions require external enforcement, and where post-test artifact checks must occur. Review the research-only spike but do not import its code.
3. INDEPENDENT VERIFIER: attempt to falsify the core novelty and the trust boundary. Design five pre-registered negative tests (including stale approvals, forged logs, permission escalation). Compare overlap with DUBSOpenHub, OpenHands and GitHub Spec Kit using dated first-party sources. Make no unverified claim of superiority.

Use short, independently authored, reproducible reports. Resolve factual disagreements by citing exact primary docs; unresolved conflict goes to Lucas without agent consensus overriding human authority. Deliver one consolidated report with: confirmed rule vs interpretation vs unknown; top 5 blockers; 2 design alternatives and explicit trade-offs; proposed smallest authentic failure→repair→reject-stale demo; quality cut list and date gates. Wait for Lucas to approve next action. No changes beyond writing locally approved research files under the correct project directory; if this project pack has not been placed in the folder yet, ask Lucas rather than fabricating that you've read it.
