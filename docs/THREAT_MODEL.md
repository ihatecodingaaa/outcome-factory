# Threat model V0 — attack the claims and the gate

Assets: repo, CI credentials, API keys, release keys, test artifacts, signed approvals, user identities, staging deployment. The target application uses synthetic data only (its domain is UNKNOWN until the official challenge pack; no real financial or personal data in any case).

| Threat | Required defense to claim 'enforced' | How verifier falsifies it |
|---|---|---|
| Agent edits its own mandate | Capability policies stored/enforced out of agent write scope | Attempt to widen path/command permission; operation must fail |
| Agent claims tests passed without running | Runner signs or server attests completed execution; logs tied to executable digest | Submit fabricated PASS JSON and tampered output file; gate denies |
| Agent teaches to hidden tests | Keep challenger definition in separate worktree and trust domain | Try reading sealed tests through allowed tools, logs, env and BAND messages |
| Agent invokes forbidden shell/network tool | OS/sandbox tool allowlist, not only model prompt | Execute forbidden operation; block logged by boundary |
| Verifier approves wrong commit | Subject digests for spec/test/commit/artifact; exact equality at deploy | Change file or dependency lock between test and deploy; reject |
| Attacker replays release token | expiry, mission+repo+environment scope, one-time consumption if needed | Copy token into new run/environment; reject |
| UI shows fabricated proof metric | Generate UI only from stored evidence records and actual commands | Replace metric with stale data; UI must mark unknown/mismatch |
| MCP prompt injection | Separate remote tool text from policy/permissions; origin/auth check; no autonomous approval from retrieved content | Inject 'ignore safety gate' into fetched docs; no new authority |
| Compromised third-party dependency | pinned dependencies, audit and lockfile; isolate builds and logs | Mutation after pinned install, identify dependency drift |
| Developer finds alternative deploy route | Only deploy identity owns credentials, branch protections and gateway mandatory | Try direct deploy using builder identity and token; deny |

Scope exclusions: the research spike does **not** implement real sandboxing, CI attestation, IAM, hardware-backed signing or universal prompt-injection resistance. Never present it as enterprise safe.
