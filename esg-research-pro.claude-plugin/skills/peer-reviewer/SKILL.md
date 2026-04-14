---
name: peer-reviewer
description: Simulate a formal peer review report with Accept/Minor Revision/Major Revision/Reject recommendation. Use for pre-submission quality check.
argument-hint: "<full paper draft or section>"
---

# Skill: peer-reviewer

## Trigger
Use this skill when you want a simulated peer review of your full paper or any individual section before submission. Run this as the final quality gate.

## Goal
Generate a formal, structured peer review report that anticipates the most likely reviewer objections for a paper on ESG practices and business performance in Indian MSMEs. Help you prepare a pre-emptive response-to-reviewers document.

## Input Required
- Full paper draft (paste or attach from Google Drive) OR
- Individual section if doing a partial review
- Specify target journal for tone calibration

## Agent File
→ `agents/reviewer-agent.md`

## Execution Mode
Single agent — deep critical reading task.
For very long papers (8,000+ words), split into two agents:
- Agent 1: Introduction + Literature Review
- Agent 2: Methodology + Results + Discussion + Conclusion

## Review Structure

### Section 1: Manuscript Summary (reviewer writes this)
3–4 sentences summarizing:
- What the paper claims to do
- What method it uses
- What it finds
- What it contributes

### Section 2: Major Issues — Must Fix Before Acceptance

#### 2a: Novelty and Contribution
- Is the gap in the literature clearly and convincingly established?
- Is the Indian MSME context genuinely understudied or does the paper overclaim novelty?
- Is the contribution differentiated from existing ESG-SME studies (e.g., from China, Europe)?
- Does the paper add to theory (not just fill an empirical gap)?

#### 2b: Theoretical Framework
- Is there a clear theoretical grounding? (RBV, Stakeholder Theory, Institutional Theory, Legitimacy Theory, Triple Bottom Line)
- Is the theory applied consistently throughout the paper?
- Does the paper develop hypotheses or propositions from theory?

#### 2c: Methodology
- Apply all 9 checks from methods-critic skill
- Flag the 3 most serious methodological concerns for this journal

#### 2d: Results and Analysis
- Are results clearly presented and linked to research questions?
- Are statistical results interpreted correctly and meaningfully?
- Are alternative explanations ruled out?

#### 2e: Discussion
- Does the discussion go beyond restating results?
- Are findings compared to prior literature?
- Are theoretical, practical, and policy implications clearly articulated?

### Section 3: Minor Issues — Should Address

- Clarity of writing and terminology
- Inconsistent citation formatting
- Tables/figures that need better labels or explanations
- Abstract completeness (does it cover: purpose, method, findings, implications?)
- Word count compliance with target journal

### Section 4: Strengths
List 2–3 genuine strengths of the paper (reviewers always include these).

### Section 5: Formal Recommendation
Choose one:
- **Accept as is** — (rare, only if truly excellent)
- **Minor Revision** — Strong paper, small fixes needed
- **Major Revision** — Significant issues but publishable potential
- **Reject** — Fundamental problems with contribution or methodology

Justify the recommendation in 3–4 sentences.

### Section 6: 5 Questions the Author Must Answer
Generate the 5 most likely questions a reviewer will ask in a "Response to Reviewers" round. These should be specific to an ESG–MSME India paper:

Example questions this skill is calibrated to generate:
1. "How does the study distinguish between ESG reporting and actual ESG practices at the operational level?"
2. "Given that BRSR is mandatory only for top 1000 listed companies, how were MSMEs incentivized to participate in the survey?"
3. "How is reverse causality addressed — is it possible that better-performing MSMEs simply have more resources to adopt ESG?"
4. "The MSME sector in India is highly heterogeneous. How does the study account for sector-level variation in ESG relevance?"
5. "How does this study's ESG measurement instrument compare to validated instruments used in prior SME sustainability research?"

## Output Format

```
PEER REVIEW REPORT
Journal: [specified journal]
Paper: Integrating Sustainability into MSME Operations in India

SUMMARY
[3–4 sentence summary]

MAJOR ISSUES
1. Novelty: [detailed comment]
2. Theory: [detailed comment]
3. Methodology: [top 3 issues]
4. Results: [comment]
5. Discussion: [comment]

MINOR ISSUES
[bulleted list]

STRENGTHS
[bulleted list]

RECOMMENDATION: [choice + justification]

5 QUESTIONS FOR RESPONSE-TO-REVIEWERS
Q1: [question]
Q2: [question]
Q3: [question]
Q4: [question]
Q5: [question]
```

## Post-Processing (Main Claude)
1. Present the full review report
2. Highlight the 3 most critical items in red/bold
3. For each Major Issue, suggest a specific fix or addition
4. Offer to create a "Response to Reviewers" template document pre-filled with the 5 questions
5. Offer to save the review report to Google Drive as: PeerReview-[Journal]-[date]