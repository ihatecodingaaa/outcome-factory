# Competition requirements and verification ledger

**Source snapshot:** 24 September 2026. These are selected confirmed public conditions, not an assertion that the unpublished BAND four-stage pack has been inspected. At kickoff, replace placeholders with the actual published requirements. Never convert an assumption to `PASS` based on our own interpretation.

Legend: `RULE` official published; `USER_SCREENSHOT` user's event portal evidence; `UNKNOWN` unresolved; `PLANNED` implementation has not occurred.

| ID | Event | Published condition | Source | Status | Evidence we must produce |
|---|---|---|---|---|---|
| DF-01 | Dark Factory | Factory built in BAND Desktop; submit factory, run and resultant clean-room app | https://luma.com/darkfactoryhackathon (wording re-verified 2026-09-23 ~17:35 UTC) | RULE | Three identifiable seats, meaningful work handoffs, original run and tested result |
| DF-01a | Dark Factory | Whether Claude Code seats attached through the jam CLI count as a factory "in BAND Desktop" | Not addressed by any official source seen | UNKNOWN | Resolve from the official pack at kickoff; until then do not claim compliance |
| DF-02 | Dark Factory | Two tracks: Pocketful and Tablekeeper | https://lablab.ai/ai-hackathons/wearedevelopers-hackathon/live | RULE | Select **one** formal track after official pack |
| DF-02a | Dark Factory | Domain and functional scope of each track (e.g. whether Pocketful involves money movement) | Unpublished (not on luma or LabLab as checked 2026-09-23) | UNKNOWN | Do not assume a financial domain; record the official track brief at kickoff |
| DF-03 | Dark Factory | Four graded stages | https://luma.com/darkfactoryhackathon | UNKNOWN detail | Insert official stage names, scoring, acceptance criteria on Sep 27 |
| DF-04 | Dark Factory | ≥3 distinct BAND coding-agent seats, each with mandate file | User's LabLab screenshot; reconfirm at kickoff | USER_SCREENSHOT | 3 linked mandates, all seats in recorded BAND session |
| DF-04a | Dark Factory | Seats may share runtime/model | Screenshot not in pack; no official source seen | UNKNOWN | Reconfirm at kickoff; disclose that all seats are the same model family |
| DF-04b | Dark Factory | Mandate files must be generic / domain-independent | No official source seen (blueprint §13 lists it as open) | UNKNOWN | Treat genericity as our design choice, not a confirmed rule |
| DF-05 | Dark Factory | Kickoff Sep 26 16:00 UTC, submission Oct 5 06:59 UTC | https://lablab.ai/ai-hackathons/wearedevelopers-hackathon/live | RULE | Submit with several-hour buffer and screenshot receipt |
| DF-06 | Dark Factory | Exact clean-room/prebuild boundary, allowed outside test suites, whether mandates prewritten | Organizer clarification required | UNKNOWN | Keep challenge-specific code at zero until written ruling/kickoff. Pre-written mandates are **provisional**; regenerate in the build window if ruled out |
| AM-01 | Amazon | Primary Alexa+: working Agent Skill **or** self-hosted MCP spec ≥2025-11-25 Streamable HTTP; alternatively source-included simulated Alexa+ experience | https://amazonappdev2026.devpost.com/rules | RULE | Real functional MCP call/skill **or** genuine runnable simulation with disclosure |
| AM-02 | Amazon | AWS Builder mini-challenge: substantively use an eligible AWS service/tool and document it | https://amazonappdev2026.devpost.com/rules | PLANNED | Runtime trace/config and candid product feedback if entering |
| AM-03 | Amazon | Pass/fail viability then equally weighted tech implementation/design/impact/idea | https://amazonappdev2026.devpost.com/rules | RULE | Distinct Alexa+-native problem, coherent UX, actual technology evidence |
| AM-04 | Amazon | Code repo GitHub public + license **or** private + designated reviewers invited, accepted and retained | https://amazonappdev2026.devpost.com/details/faqs | RULE | Repo access audit + checklist ~7 days before close |
| AM-05 | Amazon | Public <3-minute YouTube/Vimeo video, tool-specific product feedback, AWS usage as appropriate, optional friction log bonus up to 10% | https://amazonappdev2026.devpost.com/rules | RULE | Video, readable README, genuine friction log since first AWS experiment |
| AM-06 | Amazon | Deadline Oct 23 noon PDT = Oct 24 03:00 SGT | https://amazonappdev2026.devpost.com/rules | RULE | Submission receipt before close |
| NE-01 | Nebius | Runtime uses Token Factory API or Nebius AI Cloud, plus ≥1 NVIDIA **open-source** model | https://nebiusglobalaihackathon.devpost.com/rules | RULE | Recorded successful live model call, actual code path; not mocked |
| NE-02 | Nebius | Coding & Agentic Engineering: code written, run and tested in Token Factory Sandboxes | https://nebiusglobalaihackathon.devpost.com/rules | RULE | Sandbox execution logs and real artifact |
| NE-03 | Nebius | Public open-source **complete** repo with license, runnable instructions, functioning demo URL and public YouTube video <3 min | https://nebiusglobalaihackathon.devpost.com/rules | RULE | Clean-clone acceptance, deployed demo, OSS license |
| NE-04 | Nebius | Pass/fail fit, then equally weighted tech/design/impact/idea | https://nebiusglobalaihackathon.devpost.com/rules | RULE | Native sponsor role, authentic open-model evaluation, product UX |
| NE-05 | Nebius | Deadline Oct 30 10AM PDT = Oct 31 01:00 SGT | https://nebiusglobalaihackathon.devpost.com/rules | RULE | Submission receipt before close |

## Event-specific difference we must NOT gloss over

Dark Factory judges a genuine **process** and its resulting application. Amazon judges a **human-facing Amazon-native use case**. Nebius judges an **actual NVIDIA/Nebius runtime solution** and requires public complete source. We can reuse a trustworthy core, but a voice-enabled release dashboard or an API-swapped Nebius demo may fail fit.

## Exact unverified items requiring organizer approval

See `competition/ORGANIZER_QUESTIONS.md`. **Decision 2026-09-24 (Lucas):** proceed without asking the organizers additional questions; UNKNOWN rows stay UNKNOWN until the official kickoff pack resolves them. Update this ledger within 60 minutes of the kickoff brief and repeat before submission. Do not manufacture BAND's unpublished stage names or weights.
