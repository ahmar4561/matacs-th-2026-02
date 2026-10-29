# AI Proposal Triage Design

Candidate: Ahmar Ali Memon  
Reference: MATACS-TH-2026-02  
Time actually spent: approximately 10 minutes of AI-assisted brief review, drafting and checking (estimate; not a timed 60-minute session).

This design uses AI to extract evidence, deterministic rules to check and score it, and a reviewer to resolve uncertainty. A human makes the award decision.

## Files

- [Design and answers](WRITEUP.md)
- [Extraction prompt](PROMPTS.md)
- [Expected ranking](ranking.json)
- [Process flow](diagram/process-flow.png)

## AI use disclosure

ChatGPT/Codex assisted with interpreting the brief and drafting the design, prompt, diagram and ranking; the preparation was substantially AI-assisted. During the review, the AI draft's arithmetic was corrected: A's initial total of 92.26 became 93.51, and E's initial total of 84.16 became 86.16 after recalculating the published formulas. These corrections were checked programmatically, rather than treating the AI's first totals as reliable.

The repository contains original analysis and proposal letters, without the source brief or proposal text. No application or API connection is required.
