# Three Worldwide Hackathons: Research, Competitive Pre-Mortem, Product Thesis, and Execution Blueprint

**Research date:** 24 September 2026, Singapore time\
**Owner:** Lucas, GitHub `ihatecodingaaa`\
**Status:** Research-based **working decision**, not a locked specification. Dark Factory's complete four-stage challenge pack remains an official kickoff dependency.\
**Competition schedule:** BAND Dark Factory → Amazon Build, Ship, Shape → Nebius × NVIDIA.\
**Operating constraints:** One human entrant, one product core, private canonical GitHub repository, sole human Git author, independent verification, no fabricated performance claims.

> **Product hypothesis:** Transform a human-defined software outcome into a bounded engineering mission; construct and challenge the implementation; bind release approval to the exact artifact and evidence; then measure real outcomes after deployment. The core product is an **outcome-to-release control plane**, not just a chat-based coding swarm.
>
> **Working slogan:** *No evidence, no unattended release.* This does **not** mean ordinary tests can prove that production software is universally safe.

---

## 0. How to read this report: evidence and uncertainty

- **[RULE]** A directly published requirement in official competition rules.
- **[OFFICIAL]** A sponsor or developer-platform statement about a capability.
- **[OBSERVED]** A specific public competitor or community statement, not a representative sample of entrants.
- **[INFERENCE]** An evidence-backed interpretation that still needs customer or experimental validation.
- **[HYPOTHESIS]** Our own proposed product/design. Not yet built, verified, or established as unique.
- **[UNRESOLVED]** A necessary official clarification, external dependency, or actual test result still missing.

The report references dated public sources as `[S#]` in the [Source register](#source-register). It is not a claim that every registered team or private competition submission can be inspected. The Amazon and Nebius project galleries were not publicly published when checked; the publicly visible BAND team idea pages are early intentions, not evaluated completed products [S12][S13][S14].

## 1. Executive decision

**Build one core, make three genuinely sponsor-native demonstrations.** Do not simply resubmit an unchanged app to three sponsors; do not build three unrelated products either. Make the base architecture reusable and make each competition's particular capability critical in that submission.

| Event | Mission | Non-negotiable fit | Main danger |
|---|---|---|---|
| **Dark Factory**, kickoff 27 Sep 00:00 SGT; submit **5 Oct 14:59 SGT** | Prove a working BAND-governed *factory, run, and resulting clean-room application*; Pocketful planned pending final challenge pack. | At least three separate BAND coding-agent seats with individual reusable mandate files, shown in Lucas's official event screenshot; actual recorded work/handoffs/checks. Luma confirms two tracks and four graded stages [S1][S2]. | Polishing our own platform while neglecting the official four stages or the resulting application. The full four-stage scoring details were **not verified publicly** before kickoff. |
| **Amazon**, submit **24 Oct 03:00 SGT** | Give the same product a useful **Alexa+-native interaction model**—not a cosmetic voice wrapper—and potentially enter AWS Builder. | Alexa+ can use a working self-hosted MCP over Streamable HTTP or a source-included simulated Alexa+ experience; four equally weighted judging criteria; friction logs can yield up to 10% bonus [S3][S4]. | A developer release dashboard controlled by voice without a real reason to exist *within Alexa+*. Weak sponsor-native experience can fail despite an excellent factory. |
| **Nebius × NVIDIA**, submit **31 Oct 01:00 SGT** | Make the coding/agentic engineering platform operate on live Nebius Token Factory with an NVIDIA open model and demonstrate real repository write/run/test. | Pass/fail sponsor/track fit, then equal weights for implementation, design, impact, idea. Public runnable open-source repo is mandatory [S5][S6]. | Merely swapping a model endpoint, pretending mock calls are runtime evidence, or failing the public-source requirement. |

**Schedule nuance:** Dark Factory's advertised start is 26 Sep at 16:00 UTC, corresponding to 27 Sep midnight Singapore; the 5 Oct close is 06:59 UTC. Most pre-kickoff work should remain research, tool setup, original design exploration, and tests of generic utilities unless organizers approve earlier challenge-specific implementation. [S1][S2]

**Practical result:** The true engineering dependency is **Dark Factory first**. The other two are not reasons to add unused SDKs before the first submission is finished.

## 2. What judges really filter, and how to design for it

### 2.1 Dark Factory — visibly demonstrate the run, not just the result

**[RULE]** The official event description asks for the *software factory, the run that produced the result, and the result*. It has two tracks and four graded stages [S1]; the track names (Pocketful, Tablekeeper) come from the LabLab page [S2], and their domains are not published (UNKNOWN). **[USER_SCREENSHOT, not in this pack; UNKNOWN until reconfirmed]** Lucas's event screenshot adds at least three distinct agent **seats** in BAND Desktop, each with a mandate file. The sub-claims "seats may share runtime/model" and "mandates must be generic" are **UNKNOWN** (see ledger DF-04a/DF-04b). The full challenge-pack stage names and scoring details are **not yet public evidence here**. *(Relabelled 24 Sep after Phase 0 review.)*

**[INFERENCE]** A judge reviewing agents in BAND will likely seek a credible causal work trace, not three decorative avatars. Prepare authentic proof that the architect allocated work, the developer produced code, the verifier contested a claim, a test actually failed, the developer corrected it, and the final app actually behaves as required. Label inferred judging expectations as inference until the 27 Sep briefing. Do not fabricate a proposed four-stage rubric.

**Pre-kickoff official question:** Are mandate files allowed to be designed in advance? What core code is prohibited before kickoff? Exactly how are four stages evaluated? Are internal demonstrations on both challenge domains allowed when formally entering only Pocketful? Capture the written reply or kickoff recording.

### 2.2 Amazon — explicit screening plus limited judging attention

**[RULE]** Amazon may use expert panels, peer review, automated AI-driven analysis, or a combination; **it does not promise a particular AI filter**. Stage One is pass/fail for baseline viability/fit with sponsor technology. Stage Two weights technological implementation, design, potential impact, and quality of idea equally. It explicitly distinguishes a basic Alexa+ Q&A/MCP wrapper from stateful multi-service autonomous workflows and interactive media/MCP Apps. Its internal review team may recommend a friction-log bonus **up to 10%** for the Stage Two panel [S3].

**[RULE]** A public YouTube/Vimeo video must be shorter than three minutes. Judges may rely solely on submitted text, pictures, and video without testing the app; they are not required to watch past three minutes [S3]. Therefore build a fully comprehensible, *muted-screen-readable* first 15–30 seconds. Link each key claim to the precise code location and runtime evidence. Do not gamify filters or obscure the sponsor integration.

**[RULE]** Crucial September 16 repository update: a **private GitHub repo is permitted** only with Amazon's named GitHub reviewers and Devpost (`testing@devpost.com`) granted access. Their FAQ says invitations expire after seven days and require acceptance; invite around submission and verify acceptance. If we instead publish, include an open-source license [S3][S4]. Amazon allows a simulated Alexa+ experience built with any agentic tool, with **no mandatory MCP-shaped source for that alternate route**, so do not falsely claim Amazon requires every entrant to build MCP. Build a real MCP server if it strengthens authenticity and portability; do not build it solely to satisfy an invented rule.

**[RULE]** AWS Builder can be layered on the primary track. A documented integrated service/workflow matters. Per updated rules, Kiro Crew used during development can also qualify on its own; runtime AgentCore integration is a separate, possibly stronger engineering choice, not an absolute eligibility requirement [S3]. Record real friction logs as they happen (attempt, steps, expected, actual, severity, workaround, actionable fix).

### 2.3 Nebius — a visible sponsor-dependent technical core

**[RULE]** Must run on Token Factory or Nebius AI Cloud and use at least one NVIDIA open-source model. The Coding and Agentic Engineering track asks for agents that write, run, and test code in Token Factory Sandboxes. A real runtime call to Token Factory counts toward the platform requirement; owning a Token Factory account or mentioning Nemotron in a README does not [S5].

**[RULE]** Stage One is pass/fail sponsor/track fit; Stage Two equally weighs technical implementation, design, potential impact, and idea quality. Public open-source repo **with license at repo top**, full source/assets/setup, runnable demo, public YouTube demo **under three minutes**, and Nebius/NVIDIA feedback are required. Nebius states judges are not obliged to execute the app and may rely on the submission materials [S5][S6].

**[INFERENCE]** Demonstrate *one actual end-to-end model-backed autonomous loop*: inspect a real repository → generate a scoped change → run in Token Factory Sandbox → independent challenge and failing test → repair → passing evidence. Show live model request IDs, actual Sandbox task IDs, telemetry, token/cost and truthfully interpreted outcomes. Only offer model-routing claims based on repeated matched evaluations with known denominators.

**Bonus:** Tavily's bonus requires a **functional runtime Tavily API call**, not a document or slide that says “we used web search” [S5]. Use only if research freshness genuinely affects a decision.

## 3. The market problem: documented, not imagined

**[SURVEY]** In Stack Overflow's **2025** Developer Survey, 46% of respondents to the relevant trust question distrusted AI tool accuracy versus 33% who trusted it; 66% of respondents to the frustration question cited nearly correct AI solutions, and 45% cited the burden of debugging generated code. Do not present these as 2026 findings or as market-purchase intent; survey response subsets differ by question [S7].

**[RESEARCH]** The 2025 DORA research, drawing on responses from nearly 5,000 professionals and qualitative research, argues that AI amplifies existing organizational practices; a high-quality internal platform and clear workflows affect results. This supports a product that improves engineering process, not a claim that any particular implementation is needed or will sell [S8].

**[COMMUNITY, anecdotal]** Public 2026 developer discussions repeatedly raise regressions resurfacing during long agent-driven refactors and the burden of reviewing very large autonomous PRs. Reddit is useful for identifying candidate pains and language users employ, **not** for estimating how prevalent a pain is [S9][S10].

**[HYPOTHESIS] Initial buyer and user:** a 5–30-person software team shipping transactional or operational applications with material AI-generated code; technical founder or engineering lead makes the purchase; developer/reviewer handles daily usage. Why this wedge: measurable invariants and change risk, a visible workflow owner, and manageable scope. These are *discovery hypotheses*, not validated customers. Demand evidence would be people providing real anonymized examples of bad agent PRs, trying our evidence package on a production-adjacent change, and requesting integration or committing to a pilot.

## 4. Competitive landscape: be precise about what is already claimed

| Public project/platform | Publicly documented overlap | What it means for our hypothesis |
|---|---|---|
| [**OpenHands**][S11] | Automated critic before PR, repo-level code review, QA agent, iterative refinement; enterprise agent control plane [S11][S12a]. | “AI verifier,” “continuous QA,” and “enterprise agent governance” **are not unique**. Compete only with side-by-side reproducible evidence in a narrow use case. |
| [**DUBSOpenHub Dark Factory**][S15] | Sealed hidden tests, model-family separation, spec ambiguity gate, adversarial red team, repair and model tournaments. | **TwinForge as originally proposed is already substantially covered**. Do not copy its special agents then present them as inventions. |
| [**Factory**][S16] | Autonomous software development, enterprise control/observability, automated triage/review/QA/docs and incident response. | “Complete autonomous software lifecycle” is no longer a novel positioning claim. Choose a far narrower, measurable wedge. |
| [**Devin / Cognition**][S17] | Plans, writes, tests and ships production code; integration into real engineering teams. | Rebuilding a generic coding agent for this audience is an unattractive differentiation thesis. |
| [**GitHub Spec Kit**][S18] | Specify → plan → tasks → implement → converge, plus bug fixing and assessment extensions. | “Spec-first agent” by itself is not novel. Need enforceable outcome-to-evidence semantics. |
| [**Sentry Seer**][S19] | Telemetry-informed issue analysis and proposed fixes, with automation [S19]. | Incident-to-code repair already exists. Claiming production healing as our original invention would be wrong. |
| [**OPA**][S20] and [**GitHub attestations**][S21] | External policy decisions and verifiable provenance of built artifacts. | Policy-as-code and software attestations are available primitives to **integrate**, not inventions to rename. GitHub attestation availability on private repos depends on plan; do not assume personal private repo supports it [S21]. |

**Public BAND team-idea scan:** At least one public team describes specialized agents building Pocketful, one describes AI workflows linked to CI/CD, and one proposes agent behavior diffs. These are **intent statements**, not the final field. Amazon/Nebius galleries remain unpublished [S13][S14][S22].

### Competitive conclusion, stated narrowly

**[HYPOTHESIS]** The potentially useful space is **artifact-bound release accountability for agent-generated, high-invariant systems**. The value is not simply generating a spec, testing a PR, or collecting logs: it is attaching a bounded authorization, falsifiable acceptance criteria, independent counterexample traces, exact-code revision, runtime observation and human release decision to *one change*. We **do not yet have evidence** that no commercial competitor implements this complete combination. Our validation task is a side-by-side demonstration against existing tools on identical failures.

## 5. Kill-or-commit concept selection

We investigated four broad product shapes:

1. **Independent AI coding tournament (“TwinForge”).** Fast demo, fits BAND and Nebius, but DUBSOpenHub and other agents already cover independent model families, sealed tests, repairs and tournaments. **Do not use as the core differentiator.** Its techniques may still be useful inside the product.
2. **Universal self-operating software company (“FORGE OS”).** Ambitious workflow completeness, but huge scope and directly overlaps mature enterprise vendors. **Keep as long-term vision, reject as an eight-day promise.**
3. **Live incident-to-autofix platform.** Strong customer pain and demo potential; overlaps existing incident agents and demands real observability/deploy access. **Treat as a later integrated extension.**
4. **Outcome-to-Release Contract (provisional working concept).** A narrowly defined chain from business requirement to independent release evidence, binding decisions to the exact build artifact. **Pursue as a falsifiable research/build hypothesis**, conditional on Dark Factory's released rubric and Amazon's user-experience validation.

### One-sentence promise

**“Give autonomous engineers a bounded mission, and receive a release decision that can be audited back to the exact request, code, counterexamples and independent checks.”**

### First actual user journey

*(Illustrative product journey for the platform's own buyer; not an assumption about the Dark Factory track domain, which is UNKNOWN.)* A founder wants a concurrent wallet-transfer capability. The founder writes the intended outcome and selects limits. The system asks for missing business policy only where a consequential ambiguity exists. The Architect creates a typed mission. A separate Developer implements it in an isolated worktree. The Independent Verifier runs reproducible acceptance tests, challenges edge cases and returns the *shortest failing trace it can find*. The Developer repairs that trace. The release panel shows which claims have passed which level of evidence, what is unverified, and the **exact commit/artifact hash** the founder can approve. A sandbox deployment is observed; a real incident or controlled synthetic event is linked back to its requirements and replay trace.

**Critical distinction:** agent-authored tests are not independent simply because they live in a different file or agent seat. Seats may share Claude; report this correlation. Independence can be improved with sealed suites, model diversity, deterministic external oracles, property generators and ultimately human-reviewed hidden cases.

### Product objects (first-class types, not just chat messages)

- **Mission/Outcome Contract:** outcome, user, version, acceptance invariants, prohibited actions, affected repo scope, budget, escalation policy, expiry, required evidence.
- **Capability Envelope:** permissions actually enforced by an external execution boundary. A prompt that says “do not deploy” is not a sandbox.
- **Change Set:** repo/branch, diff, dependency/migration impact, commit and artifact hashes.
- **Counterexample:** input, schedule, environment, exact observed output, invariant broken, reproduction script, persistence location.
- **Evidence Item:** type (test, property, model-check, browser trace, static analysis, security, human approval), tool/version, test inputs, result, digest, limits, link to artifact.
- **Release Decision:** fail closed on required missing evidence, expired policy, changed code hash or unavailable verifier; human override only with a clearly recorded explanation, never silently forged PASS.
- **Operational Observation:** version, telemetry, incident provenance, reproduction, suspected defect, proposed patch, verified canary, actual outcome (when a genuine deployment exists).

**Release gate design:** An approval token is bound to the exact approved commit/artifact digest, policy revision and expiry. If code changes after verification, the old token is invalid. Start with an actual deterministic gate for a small test application before promising general production enforcement. OPA or another policy engine can separate authorization decisions from model persuasion [S20].

### Avoid verification theatre

- Never show `SAFE` or `PROVEN` on the basis of a finite random stress suite alone. Say “passed 10,000 generated schedules under these assumptions, seed X.”
- A state-space model can establish a property **of the model, under its assumptions and explored bounds**, not automatically establish correctness of deployed code. Link model abstraction, bounded state graph and implementation-level conformance tests separately.
- Never invent percentile success rates, false “risk scores” or phantom production incidents.
- Controlled fault injection must be prominently labelled as synthetic; production claims require an actually instrumented deployment.
- Do not let agents create hidden tests and then claim independence while sharing those tests or model family.
- The verifier must be capable of rejecting the architect and developer, with its rejection captured in the BAND run.

## 6. A credible technical implementation

### Stage A: BAND hackathon, live factory first

Three connected seats already exist on Lucas's machine: `architect-x7jh`, `developer-x7jj`, `independent-verifier-x7j` (display name `independent-verifier-x7jk`; corrected 24 Sep, see `operations/BAND_RUNBOOK.md`) (verify current online state and restart short-lived listeners when working). Each must receive a **distinct generic mandate file**. Keep *role mandate* separate from a *mission-specific contract*. A role mandate should also work unchanged on a reservation system.

**Architect:** converts accepted requirements to contract, identifies ambiguous external/business choices, allocates work with bounded scope, records decisions. Cannot certify own implementation or raise developer permissions.

**Developer:** implements and writes ordinary tests in isolated workspace; reports actual diffs, builds, failures, full command outputs and unresolved items. Cannot edit independent acceptance suite or self-certify.

**Independent Verifier:** owns acceptance suites and replay traces; observes final artifact hash; may reject or block release; documents test design assumptions and blind spots; must not quietly fix the implementation it judges.

The initial communication checks are **setup evidence**, not proof that the competition workflow has run. Save logs from a fresh, attributable, challenge-period run.

**Pocketful acceptance targets (pending organizer challenge pack; CONDITIONAL on Pocketful involving money movement, which is UNKNOWN because its domain is unpublished):** money conservation for the relevant closed model; non-negative balances; authorization; idempotent request IDs; no double-spend under controlled concurrent schedules; exact decimal arithmetic; atomic failure behavior; deterministic replay and audit receipt correctness. Do not silently assume whether fees, credits, chargebacks or refunds change conservation semantics until the official specification says so.

**Suggested instrumentation:** real database transactions and locking constraints; deterministic race harness; property/stateful testing with [Hypothesis][S23] or corresponding JS tools; targeted model checking where the state is genuinely manageable; browser interaction and accessibility testing. Unit tests alone are not a convincing concurrency oracle. Prefer a minimal operational Pocketful UI that is excellent at real tasks over many incomplete screens.

**Genericity experiment:** run unchanged role mandates and a separately configured mission contract against a small Tablekeeper-style prototype (e.g. double-booking, if Tablekeeper turns out to be a reservation domain; its domain is UNKNOWN). This is an **internal proof of role generality**, not a second formal entry unless organizers approve. Do not divert scarce time from Pocketful stage requirements.

### Stage B: Amazon, create a real reason to use Alexa+

**The single-product assumption is weakest here.** “Alexa, approve my pull request” is a poor product if ordinary developers prefer keyboard, IDE and diff tools. We must validate an interaction that voice/ambient context makes meaningfully better. Research candidates:

- An **on-call decision room**: while handling an incident hands-busy, ask what release changed the invariant, hear concise verified evidence, and use visual MCP cards to inspect/authorize **only** safe reversible operations.
- A **founder’s mission brief**: express an outcome by voice while away from a workstation; the system clarifies constraints, persists state and produces a draft mandate for later precise approval on screen.
- An **accessible engineering cockpit**: voice + interactive, keyboard-accessible cards designed for users who benefit from hands-free investigation. Do not claim to have validated accessibility use cases without real users.

**Kill gate by 8 Oct:** If no distinct end-user workflow requires Alexa+, **do not force it** merely to reuse the same product. A single core may support a new surface without giving the sponsor a credible customer need. Choose the native feature only after user-task testing. One backend + a genuinely purpose-built human interface is consistent with the “one product” requirement.

Build a real standards-compliant self-hosted MCP server with Streamable HTTP only if the intended interaction benefits from external-client portability. Amazon also accepts a simulated Alexa+ web experience [S3][S4]. If using MCP Apps, verify host compatibility and sandboxed UI behavior rather than promising universal rendering. The MCP Apps SDK offers interactive tool views, but host support varies [S24]. Any operations affecting production should require strong authentication and explicit human approval; reading a summary should not confer deployment authority.

**AWS Builder option:** Make AWS AgentCore or other AWS service responsible for a real identity/runtime/policy boundary, with architecture evidence and a substantive feedback log. Avoid decorative use of S3, Bedrock, etc. AWS cost credits are pending; the existing budget is a notification, **not a hard stop**.

### Stage C: Nebius, open-model verified execution

Evolve the **same mission, change set, evidence graph and release UI**. Introduce a genuine NVIDIA open model via Token Factory and execute actual write/run/test loops in Token Factory Sandboxes. Demonstrate one baseline and one improved run on *identical task specifications*, including pass/fail tests, wall-clock time, token cost and retained artifacts. Run multiple trials before making comparative reliability claims; show variation, not fabricated deterministic averages. Add an actual Tavily runtime freshness query only if source-age verification is a real user benefit [S5].

Do not claim that merely executing Claude Code locally meets Nebius; the sponsor-required model and Nebius runtime calls must appear within the relevant project workflow and submitted source. Use the current documented model identifiers at implementation time, not guesses from promotional copy.

## 7. Differentiating UX: the Evidence Cinema, not a decorative dashboard

A judge should understand the core in 20 seconds **with audio off**. *(Illustrative money-movement example; the real mission depends on the official track domain, which is UNKNOWN until the challenge pack.)*

1. The user sees a human-readable mission: **“Move money safely under concurrent retries.”**
2. On a *real working* system, a controlled duplicate transfer is injected. The UI flashes **FAIL**, displays exact before/after balances and a 6–10-event replay strip. The failure is explicitly labelled synthetic if intentionally injected.
3. The Architect assigns repair; the Developer submits a diff; the Independent Verifier reruns the *same failing seed* and additional suites.
4. The evidence panel changes only after the real verifier reports. A new artifact hash is shown; previous approvals are invalidated. The user sees **what was verified and what remains uncertain**, and approves a sandbox/canary release.

**Visual information architecture:** Mission Canvas (user outcome, constraints, human decision); Living Change Graph (requirements → components → test evidence, click-to-inspect); Counterexample Theatre (pause/step/replay exact events and data); Evidence Receipt (auth, traces, hashes, non-claims); Deployment/Recovery (only when backed by genuine runtime). Must remain usable with keyboard, readable text and reduced motion; motion should communicate real state changes, not simulate hidden background work.

**Screens are not proof:** each component's `PASS`, chart, and animated change must link to a real machine-readable evidence object. Make a spectator-friendly read-only/demo mode separate from an authenticated owner approval mode.

## 8. The competitive experiment, not a self-written victory claim

**Experimental objective:** On the same intentionally defected transactional repository, compare our workflow against a conventional agent loop (and where licensing/time permits, an adjacent open-source workflow). Do not conflate one model's raw capability with the orchestration harness.

Run fixed representative tasks: retry idempotency regression; concurrent transfer race; rounding edge case; stale SDK assumption; unauthorized tool request; changed code after passing tests. Pre-register the acceptance suite outside the builder worktree and label any model-family overlap. At least one deliberately unknown/held-out test should be reviewed or sourced independently.

Record: reproducible defects identified; time to first valid counterexample; repair attempts; code diff quality; verification type and limits; reviewer minutes spent; false-positive/false-negative patterns; end-to-end cost; exact versions/commits. A single demo may establish feasibility, **not** statistical superiority. Publish both failures and wins in the competition repo where safe.

**Commitment criteria for the core concept by Oct 2:** the factory independently catches an initially missed bug, reliably reproduces it, truly blocks release while evidence is missing, permits a bounded verified fix, and Pocketful's core user journey works. If this cannot be achieved, reduce scope rather than manufacture a green report.

## 9. Judge-first submission engineering

### A. A machine-readable rubric ledger

Maintain `competition/REQUIREMENTS_LEDGER.md` (the pack's rubric ledger; originally planned as `competition/rubric-ledger.md`) with one row for **each official requirement**, containing: source/date, interpretation, code path, demo timestamp, evidence artifact, responsible agent, current state (`UNSTARTED`, `IN_PROGRESS`, `PASS`, `BLOCKED`, `UNKNOWN`), owner of verification. Unknown sponsor stages remain labelled `UNKNOWN` until kickoff. Add an independent pre-submission checklist, not a self-assigned judge score.

### B. The video storyboard

- **0–15 s:** user pain, visible product and real consequence.
- **15–45 s:** show the true autonomous workflow and why sponsor technology is necessary.
- **45–105 s:** live consequential failure → exact replay trace → independent challenge and repair.
- **105–145 s:** true evidence boundary → human decision; show a beautiful operational experience.
- **145–175 s:** evidence, realistic limitations, buyer, what's demonstrably better/different.

Three **distinct videos** should foreground different proof: BAND trace and challenge implementation; Alexa+-native human workflow and AWS integration; Nebius runtime/NVIDIA/Sandbox execution. The shared backend is allowed where each event's originality/update and required technology conditions are honored [S3][S5].

### C. Reviewers must not have to debug our submission

Provide public (when required) or authorized private source, specific tag/commit, one-command dev bootstrap, `env.example` with fake placeholders, seeded demo dataset, health check, short evidence catalog, clearly documented local demo path and a cloud-hosted read-only version where practical. No actual bank credentials or customer data in Pocketful. Video is publicly viewable without a login. For any private deployed demo, give clear **judge-only credentials**, keep them active through the official judging period, and never place privileged secrets in the README [S3][S5].

## 10. GitHub governance: sole credited author and private source access

**Current verified integration fact (24 Sep):** ChatGPT's connected GitHub integration can list and read Lucas's **existing private** repositories under `ihatecodingaaa`; this verifies the integration on current repos, **not automatic access to any new repo**. Claude Code can use the repo through Lucas's local GitHub authentication on his laptop; check `gh auth status`, `git remote -v`, and the specific repository scope instead of creating another human account.

**Creation policy:** Create a new private canonical repository under `ihatecodingaaa` with an explicit name once Lucas authorizes. Keep a local clone at `C:\Users\lucas\Projects\dark-factory` and push an initial research/architecture snapshot only after verifying clean history, `.gitignore`, `.env.example`, secret scanning and competition prebuild boundaries. **Do not publish a repository URL before it exists.**

**Sole-commit-author policy:** All commits should use Lucas's Git identity (`git config user.name` and the GitHub-verified email). Instruct all Claude Code/BAND agents *not to add `Co-authored-by` trailers*, and not to commit under a bot/agent identity. Let Lucas review and authorize commits, pushes, merges and releases. This is about Git authorship metadata; do **not** falsely claim no AI assistance in applications or sponsorship disclosures where such help must be disclosed. ChatGPT's GitHub connector may make API changes through a tool identity: check any resulting commit's actual author/committer metadata; for strict attribution, prefer Claude's local Git under Lucas's configured identity.

**Privacy conflict:** Amazon permits a **private** repo if all listed Amazon reviewers and Devpost are added with accepted invitations close to submission [S3][S4]. **Nebius does not**: it explicitly requires a **public, open-source, fully runnable repo with a license** [S5]. To preserve a private canonical development repo, prepare an independently auditable **public release/submission repository or mirror** containing all necessary functional code, assets and instructions, sanitized secrets, and an accepted OSI-style open-source license. If preserving proprietary algorithms means refusing to release the functional source, Nebius cannot be satisfied on the current published rules; do not substitute a documentation-only skeleton. Complete license/IP review *before* adopting dependencies. Do not delete internal history or change misleading authorship to camouflage reuse.

**Security:** Never commit API keys, private `.env`, AWS/Nebius tokens, personal customer data, live billing info or invite credentials. GitHub artifact attestations for private repos on GitHub Free/Pro/Team are unavailable under current documentation; use reproducible local hashes/run artifacts and upgrade only if genuinely necessary [S21].

## 11. Resource constraints and scope control

**Known current resources:** Three BAND agents successfully connected in one room; Claude Max on Lucas's laptop; AWS existing credits and a budget alert, with the additional $150 hackathon application **pending**; Nebius $27.25 account balance associated with the **redeemed hackathon code** per Lucas's confirmation, plus separate $1 trial shown at the time. Do not presume another Builder Program credit award merely from a transaction label. Existing recorded consumer project is not yet the BAND challenge run.

**Budget principle:** Each mission gets a hard *application-enforced* ceiling on tokens/attempts/wall-clock and sandbox resource consumption where possible. AWS Budgets is alerting rather than universal automatic enforcement. Nebius billing is active and a card may be charged according to terms; monitor balance and seek provider hard-cap confirmation if zero overage is essential.

**Explicitly defer unless needed:** model fine-tuning, multi-cloud active/active failover, custom LLM model router without enough evaluation data, on-chain proof, generic developer marketplace, broad multi-tenant RBAC, actual financial transfers, automated production writes, elaborate physics animations, and full formal proof of the entire application. None is necessary for the first truthful end-to-end milestone.

## 12. Day-by-day operating plan and go/no-go gates

**24 Sep (prebuild):** freeze public rules snapshot; capture official unresolved BAND questions; finalize five high-risk customer tasks; finish competitor claim matrix and choose a one-sentence buyer; design proof vocabulary and UX storyboard. Current public challenge-specific code should not be prebuilt without a favorable event-specific answer.

**25 Sep:** define three **generic** seat mandates and the typed mission contract as design documents; select small real invariant test harness; prepare read-only research snippets; sketch the spectator-visible failure/replay screen; map AWS/Alexa and Nebius-specific later extension points without building integrations.

**26 Sep:** verify BAND environment, Git identity, disk backups, experiment toolchain and subscriber cost visibility; attend midnight Sep 27 kickoff and the BAND question session. Freeze assumptions as soon as the *official four-stage pack* arrives.

**27 Sep:** reconcile **every** official stage; reset product scope if misaligned. Build a minimal real baseline using BAND and save session logs, commit history and the first real acceptance failure.

**28–30 Sep:** implement the mandatory app workflow and hidden/challenger test harness; fix correctness before bonus UI. Create legible BAND task handoffs. Prepare usable Pocketful application with primary flow, error messages and concurrency instrumentation.

**1–2 Oct:** get one fully real end-to-end counterexample → repair → reverify → explicit release token and bounded sandbox deployment. Independent verifier attempts to invalidate the claims. If the killer loop does not run by Oct 2, stop all optional extras.

**3–4 Oct:** regression suite, rehearsed demo, screenshot/recording evidence, scrub secrets, freeze tag, produce video/README/project submission, verify LabLab form and organizer-specific files.

**5 Oct:** submit with a personal buffer several hours before **14:59 SGT**. Verify all official entry states and capture submission receipts. Freeze the exact BAND v1 tag for traceability.

**6–8 Oct (Amazon gate):** validate the target Alexa+ journey with task trials and official rule checklist. Kill cosmetic voice control. Decide exact self-hosted MCP versus allowed simulator implementation. Begin AWS developer friction log immediately.

**9–20 Oct:** build the genuine Alexa+ experience and carefully chosen AWS Builder service/flow; keep the original BAND application functional. Test on an actual local or hosted runtime with read-only judge mode. Do not assume credit application approval.

**21–23 Oct:** invite private repo reviewers **near submission**, require accepted invitations, finalize concise product feedback and genuine friction log, submit before **24 Oct 03:00 SGT**; tag Amazon v2 and preserve reproducibility through November judging.

**24–29 Oct:** integrate NVIDIA open model live on Token Factory, run code/test through actual Sandbox, perform paired measured comparisons, prepare complete public OSS submission mirror and license, create working demo, record Nebius/NVIDIA feedback and (if real) Tavily integration.

**30 Oct:** publish the independently runnable public artifact only after secrets/license audit; verify package bootstrap using a clean machine/environment; submit before **31 Oct 01:00 SGT**. Keep demo available and avoid post-deadline modifications to the judged version through the December judging period.

### Stop/continue gates

- **Sep 27:** official pack contradicts our architecture? Change architecture; rubric wins.
- **Oct 2:** no real end-to-end BAND factory trace + functioning Pocketful core? Cut optional features immediately.
- **Oct 8:** Alexa+ lacks a convincing native user advantage? Reframe the interaction on a supported real task; do not cosmetically relabel the platform.
- **Oct 26:** no real Nemotron/Token Factory/Sandbox loop? Prioritize minimum eligible functionality over expensive visual polish.
- **At every milestone:** preserve a runnable tag, do not ship fabricated evidence, and do not claim formal safety beyond bounded results.

## 13. Questions that should remain open rather than be hidden

1. **BAND:** What exactly are the four graded stages, exact stage weights, permitted prebuild boundary, role-mandate genericity test, and track/multi-track participation restrictions? Obtain the official 27 Sep release pack.
2. **Amazon:** Is the on-call/mission-brief human workflow compelling *to Alexa+ users* or only to people building FORGE? Validate against user tasks; sponsor-native value is a condition, not a slogan.
3. **Nebius:** Confirm current supported NVIDIA model IDs, Sandbox SDK/runtime and effective costs at integration time. Plan a fully open-source runnable mirror and license, or accept that private-only source conflicts with this event.
4. **Differentiation:** Can the proposed release gate discover or block a real defect that an ordinary coding agent + existing QA review did not catch? Demonstrate an identical-seed comparison before claiming improvement.
5. **Customer:** Which paid buyer will supply a sample incident/PR, use a reproducible evidence receipt and pay to reduce verification burden? Research discussion is not proof of demand.
6. **Safety/limits:** Which tool calls can the external gate actually mediate? Which bypasses remain? Clearly state where isolation is only logical/role-based rather than technically enforced.

## 14. Immediate first result

Prepare a **single reusable eight-part Mission Contract example**, plus a **baseline vs challenged test case** and a **UI storyboard**, as research artifacts before kickoff—subject to official prebuild clarification. Do not create an army of bespoke agents and call that an invention. Once the official pack arrives, update `competition/REQUIREMENTS_LEDGER.md` and promote only requirements that can be evidenced by the actual BAND run, app and clean-room acceptance results.

The strongest honest demonstration is not “our factory never makes mistakes.” It is **“this is a specific mistake an authorized, capable agent made; here's an independently reproducible counterexample, the exact fix and the evidence that does—and does not—justify this release.”**

---

## Source register

Primary official rules override marketing and this plan. URLs below are public navigation links; project status and dates are as checked on 24 Sep 2026.

- **[S1]** [WeAreDevelopers × BAND official companion event page](https://luma.com/darkfactoryhackathon): two tracks, four stages, factory/run/result.
- **[S2]** [LabLab Dark Factory live page](https://lablab.ai/ai-hackathons/wearedevelopers-hackathon/live): dates, tracks and registration snapshot.
- **[S3]** [Amazon Build, Ship, Shape official rules](https://amazonappdev2026.devpost.com/rules): Alexa+ alternatives, AWS Builder, private source disclosure, Stage One/Two, friction-log bonus, video and submission terms.
- **[S4]** [Amazon FAQ](https://amazonappdev2026.devpost.com/details/faqs): gated Alexa+ preview is unavailable to regular entrants, private repo reviewer invitations expire after seven days, Alexa+ hosting not universally required.
- **[S5]** [Nebius × NVIDIA official rules](https://nebiusglobalaihackathon.devpost.com/rules): sponsor runtime/model, track, code/public license, video, prize rules and judging.
- **[S6]** [Nebius official judging guidance](https://nebiusglobalaihackathon.devpost.com/updates/46204-here-s-how-judging-works): pass/fail then four equally weighted criteria; basic code completion insufficient.
- **[S7]** [2025 Stack Overflow Developer Survey, AI](https://survey.stackoverflow.co/2025/ai): trust and frustration responses and denominators.
- **[S8]** [2025 DORA report announcement](https://cloud.google.com/blog/products/ai-machine-learning/announcing-the-2025-dora-report): nearly 5,000 professionals and AI as an amplifier of existing practice.
- **[S9]** [Reddit: long-running AI coding regressions, June 2026](https://www.reddit.com/r/ClaudeCode/comments/1ufur9x/how_do_you_manage_longterm_aiassisted_coding/): anecdotal qualitative pain.
- **[S10]** [Reddit: autonomous issue-to-PR review burden, June 2026](https://www.reddit.com/r/ClaudeCode/comments/1u0jwcv/is_anyone_actually_running_coding_agents/): anecdotal qualitative pain.
- **[S11]** [OpenHands Verification Stack, June 2026](https://www.openhands.dev/blog/20260506-the-verification-stack): automated critic, PR review and QA.
- **[S12a]** [OpenHands enterprise agent control plane](https://www.openhands.dev/blog/openhands-enterprise-agent-control-plane): organization-scale governance and observability positioning.
- **[S12]** [Amazon project gallery](https://amazonappdev2026.devpost.com/project-gallery): unpublished as checked.
- **[S13]** [Nebius project gallery](https://nebiusglobalaihackathon.devpost.com/project-gallery): unpublished as checked.
- **[S14]** [BAND Runtime Rebels team idea](https://lablab.ai/ai-hackathons/wearedevelopers-hackathon/runtime-rebels): early public planned features, not finished competitor.
- **[S15]** [DUBSOpenHub dark-factory](https://github.com/DUBSOpenHub/dark-factory): sealed independent QA, adversarial reviews, tournaments, model-family separation.
- **[S16]** [Factory developer platform documentation](https://docs.factory.ai/): software-factory, QA, enterprise controls, incident capabilities.
- **[S17]** [Cognition / Devin official website](https://cognition.com/): autonomous coding/shipping platform positioning.
- **[S18]** [GitHub Spec Kit official documentation](https://github.github.com/spec-kit/): structured spec-to-implementation process and extensions.
- **[S19]** [Sentry Seer documentation](https://docs.sentry.io/product/ai-in-sentry/seer): issue scan/fix/automation.
- **[S20]** [Open Policy Agent official docs](https://www.openpolicyagent.org/docs): domain-independent policy evaluation.
- **[S21]** [GitHub artifact attestations docs](https://docs.github.com/en/actions/how-tos/secure-your-work/use-artifact-attestations/use-artifact-attestations): provenance, verification and private repository plan restrictions.
- **[S22]** [BAND AgentDiff / TLE team idea](https://lablab.ai/ai-hackathons/wearedevelopers-hackathon/tle): public early behavioral-regression concept.
- **[S23]** [Hypothesis stateful testing docs](https://hypothesis.readthedocs.io/en/latest/stateful.html): generated action sequences to explore failures.
- **[S24]** [MCP Apps official repository](https://github.com/modelcontextprotocol/ext-apps): interactive views, supported-client caveats and SDK.
- **[S25]** [MCP official Streamable HTTP protocol, 2025-11-25](https://modelcontextprotocol.io/specification/2025-11-25/basic/transports#streamable-http): required transport semantics if using self-hosted MCP.
- **[S26]** [BAND Desktop official docs](https://docs.band.ai/band-desktop): coordination, work ownership, agents, rooms and audit visibility.
- **[S27]** [OpenAI, evaluation benchmark limitations, July 2026](https://openai.com/index/separating-signal-from-noise-coding-evaluations/): reminder that green benchmark scores can conceal task defects and contamination.
