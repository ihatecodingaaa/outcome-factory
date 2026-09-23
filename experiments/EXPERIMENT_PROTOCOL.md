# Pre-registered falsification experiment

**Hypothesis to falsify:** A bounded, independent evidence-and-release workflow makes an engineer's acceptance decision more reliable and legible than a conventional single-agent+CI workflow on a small sample of high-consequence changes. We have no evidence of superiority before tests.

## Study design

Choose 5 **fixed challenge-agnostic** tasks before generating code: (1) duplicate/retry idempotency, (2) concurrent write lost update, (3) decimal rounding drift, (4) changed artifact after prior green tests, (5) forbidden tool/credential request. Final Dark Factory domain examples depend on official challenge pack; pre-event experiments must be *research-only* if code reuse is not allowed.

**Baseline:** ordinary agent with same initial specification and repo, same compute/turn budget and an openly declared testing setup.\
**Experimental:** BAND Architect/Developer/Verifier plus external release evaluator.\
**Challenge suite:** author separately from the builder, freeze before evaluation and fingerprint definitions. If independent model-family separation not used, report the shared-family limitation honestly.

## Predefine metrics

- Truly reproduced defects / fixed target cases (counts, denominator, exact seed)
- Time to first real failing trace, time to accepted repair; reviewer minutes
- False positives and known false negatives from unchanged challenge suite
- The fraction of permission bypass tests actually **enforced** by external control
- Ability of **unapproved post-test artifact mutation** to pass the real deploy gate (must be zero in tested threat model)
- Actual spend, API model IDs, wall-clock times and environment hashes

## Reproducibility

Each observation must contain input commit, full command and args, env/build identifiers, exact test definition hash, output bytes hash, capture time, verifier identity, result and failure trace (when failed). Never report aggregate 100% safety or statistically significant uplift from five cases.

## Stop/go milestones

**Sep 27:** official mandatory stages mapped; if misaligned, prioritize mandatory stages.\
**Sep 30:** functional domain app and authentic BAND execution trace.\
**Oct 2:** complete real fail→repair→reverify→deny-stale artifact loop; otherwise remove extra features.\
**Oct 4:** runnable tag, evidence manifest and frozen demo.\
**Oct 8:** Alexa+ user-task value established on actual users/task attempts, or pivot Alexa+ interaction.\
**Oct 26:** live Nebius model + Sandbox run integrated; otherwise freeze UX extras and focus minimum compliant live path.
