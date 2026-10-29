# AI-assisted proposal triage

## Assumptions and scoring policy

The category configuration stores mandatory conditions, project limits, weights, scoring functions and tie-breakers. An admin approves a version before review begins. The numerical rubric below is my proposed configuration, because the brief supplies weights but not score formulas. It is not a claim about industry standards.

Budget and schedule are project eligibility gates: a confirmed amount above CAD 260,000 or duration above 16 weeks is ineligible; an unknown value requires clarification. Missing mandatory evidence is flagged; an explicit failure is ineligible. A bidder relying only on a future subcontractor does not satisfy the requirement to hold its own licence. Documents support a statement of compliance, not independent verification of a licence or insurance.

Experience uses the five years preceding the evaluation date. Counts must be supported for commercial projects of at least 100 kW within that window. “Since 2020” does not prove that every project is recent enough. A's and E's “since 2021” counts are provisionally accepted as the supplied summaries' intended five-year evidence; at a real evaluation in late 2026, exact dates for these would also need confirmation. This assumption is recorded for the sample exercise only.

Each criterion has a 0–100 subscore:

| Criterion | Configured rule | Weight |
| --- | --- | --- |
| Experience | min(100, verified qualifying count / 10 × 100) | 30% |
| Price | min(100, 200,000 / price × 100), positive CAD totals only | 25% |
| Timeline | min(100, 10 / completion weeks × 100), positive durations only | 15% |
| Warranty | 50 × min(panel years / 25, 1) + 50 × min(workmanship years / 10, 1) | 15% |
| Team / approach | 25 each: stated named lead, described crew, safety plan, monitoring plan | 15% |

CAD 200,000 and 10 weeks are fixed scoring anchors proposed for admin approval. Fixed anchors avoid changing everyone's scores when a new bidder arrives. Warranty benefits cap at the configured target; E's extra workmanship years remain visible as supporting detail. A summary's assertion of a named lead counts for this exercise; a production workflow requests the actual identity.

Total = sum(subscore × weight / 100). Calculate without intermediate rounding; display two decimals. Ties use lower price, then shorter duration, then proposal letter. Unknown required scoring evidence blocks a final score; absent optional team-plan evidence earns zero for that component, with the absence shown.

## 1. AI vs. rules

Upload validation, file limits, malware scanning, PDF text extraction and OCR run before AI. AI converts varied proposal language into typed facts with short evidence quotes and locations. It does not decide eligibility or rank. Code validates the schema, compares evidence with extracted source text, checks mandatory conditions, applies the frozen rubric, sorts and produces templated reasons. AI adds value to language interpretation; arithmetic and procurement gates belong in code. The diagram includes clarification and approval checkpoints.

## 2. Consistency and explainability

Freeze source hashes, extracted text, evaluation date, criteria version, rubric, prompt and model version. Persist the reviewer-approved extraction. Identical approved facts and configuration produce identical rankings. A fresh AI extraction can vary even at temperature zero; cache it and require review of changed facts rather than promising perfect model repeatability. Each result shows raw values, evidence locations, gate outcomes, subscores, total and unresolved issues.

| Proposal | Experience | Price | Time | Warranty | Team | Result |
| --- | ---: | ---: | ---: | ---: | ---: | --- |
| A | 100 | 84.0336 | 83.3333 | 100 | 100 | 93.51, rank 1 |
| E | 80 | 82.4742 | 76.9231 | 100 | 100 | 86.16, rank 2 |
| B | — | — | — | — | — | Ineligible: bidder-held licence condition fails |
| C | — | — | — | — | — | Flagged: experience dates and manipulation review |
| D | — | — | — | — | — | Flagged: completion duration unknown |

C's embedded ranking instruction is ignored and recorded. It neither earns points nor automatically disqualifies the bidder. After source review and date clarification, C can be scored normally; the incident itself has no numerical penalty. D needs a confirmed schedule. These are final ranks among currently rankable submissions, not a final award recommendation.

## 3. Human in the loop

The reviewer verifies extracted evidence, resolves flags, and approves the comparison. Corrections change the fact record and trigger deterministic recalculation. Overrides need a reason and identity; preserve both original and revised results. Log timestamps, file and configuration hashes, evidence, model/prompt versions, extraction changes, flags, approvals and award decision. Award approval remains a separate human action.

## 4. Changing criteria

Edits create a new version. Existing runs retain their original configuration and results. A reviewer explicitly starts a new run for all bidders under the new version; reuse approved facts where applicable and extract new fields when necessary. Compare results and require approval before publishing the replacement. Never compare scores generated under different versions.

## 5. Risks and safeguards

- Wrong extraction or invented facts: nullable fields, quotes and locations, source checks, reviewer confirmation; unmatched evidence blocks scoring.
- Manipulation: treat every uploaded character as untrusted data, isolate extraction from tools and secrets, flag commands, validate schema; code alone scores.
- Bias: score only approved criteria, hide irrelevant identifiers where practical, audit overrides and compare outcomes; do not infer ability from writing style.
- Cost and reliability: size/page limits, cached extraction, bounded retries and timeouts; show failure status instead of fabricated results.
- Security: restricted access, encrypted storage, retention limits and no executable document content. Never place private uploads in public repositories.
