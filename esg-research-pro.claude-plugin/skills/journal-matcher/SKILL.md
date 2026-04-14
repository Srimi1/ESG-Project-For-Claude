---
name: journal-matcher
description: Match your paper to 7 target journals with fit scores and submission framing advice. Use when deciding where to submit.
argument-hint: "<abstract and keywords>"
---

# Skill: journal-matcher

## Trigger
Use this skill when deciding which journal to target for submission, or when you want to reframe your contribution for a different venue.

## Goal
Evaluate fit between this paper and 7 target journals. Return a ranked list with fit scores, contribution framing advice, and submission requirements for each journal.

## Input Required
- Your abstract (paste text)
- Your keyword list
- Your method (survey / secondary / mixed / conceptual)
- Your primary contribution angle (A: operationalization / B: policy / C: business case)

## Agent File
→ `agents/journal-agent.md`

## Execution Mode
Single agent — analytical matching task.

## The 7 Target Journals to Evaluate

### Journal 1: Journal of Cleaner Production
- Publisher: Elsevier | Impact Factor: ~11 | Quartile: Q1
- Scope: Sustainable production, cleaner technology, environmental management, circular economy
- MSME fit: YES — publishes SME sustainability studies
- India fit: YES — strong emerging market coverage
- Method preference: Quantitative, survey-based, secondary data
- Special requirements: Highlights (5 bullets, 85 chars each), structured abstract, data availability statement, AI use declaration
- Typical time to decision: 3–4 months

### Journal 2: Business Strategy and the Environment
- Publisher: Wiley | Impact Factor: ~13 | Quartile: Q1
- Scope: Corporate sustainability, ESG strategy, environmental management, SDGs
- MSME fit: PARTIAL — prefers firm-level strategy; MSMEs need strong framing
- India fit: YES — emerging market studies published
- Method preference: Mixed methods, quantitative
- Special requirements: Structured abstract (Aims/Methods/Results/Policy Implications)
- Typical time to decision: 2–3 months

### Journal 3: Sustainability (MDPI)
- Publisher: MDPI | Impact Factor: ~3.9 | Quartile: Q2
- Scope: Broad sustainability — environmental, social, economic dimensions
- MSME fit: HIGH — very SME and developing country friendly
- India fit: HIGH — frequently publishes India-specific studies
- Method preference: All methods accepted
- Special requirements: Open access fee (~$2,400 APC), fast review (4–6 weeks)
- Typical time to decision: 4–8 weeks

### Journal 4: Journal of Small Business Management
- Publisher: Taylor & Francis | Impact Factor: ~8 | Quartile: Q1
- Scope: Small business strategy, entrepreneurship, SME management
- MSME fit: HIGH — core focus on small/medium enterprises
- India fit: MODERATE — accepts emerging market but not the primary focus
- Method preference: Survey-based, quantitative
- Special requirements: Strong entrepreneurship/management framing required
- Typical time to decision: 3–5 months

### Journal 5: Journal of Business Ethics
- Publisher: Springer | Impact Factor: ~7 | Quartile: Q1
- Scope: Business ethics, CSR, stakeholder theory, corporate governance
- MSME fit: MODERATE — large firm bias; MSME angle must be justified
- India fit: YES — publishes India corporate governance studies
- Method preference: Conceptual, qualitative, mixed methods
- Special requirements: Strong ethical/stakeholder theory grounding required
- Typical time to decision: 4–6 months

### Journal 6: Asia Pacific Journal of Management
- Publisher: Springer | Impact Factor: ~4.5 | Quartile: Q2
- Scope: Management in Asia-Pacific context; strategy, governance, entrepreneurship
- MSME fit: MODERATE — business performance framing works well
- India fit: HIGH — India is a core region for this journal
- Method preference: Quantitative, survey-based
- Special requirements: Must situate findings within Asia-Pacific management theory
- Typical time to decision: 3–4 months

### Journal 7: IIMB Management Review
- Publisher: IIM Bangalore / Elsevier | Impact Factor: ~2.5 | Quartile: Q3
- Scope: Indian business, management, policy — generalist
- MSME fit: HIGH — strong India policy and MSME focus
- India fit: HIGHEST — India-specific journal; Indian context is a strength not limitation
- Method preference: All methods; policy-relevant papers preferred
- Special requirements: Policy implication section strongly preferred; Indian data required
- Typical time to decision: 2–3 months

## Fit Scoring Rubric (1–5)
- 5: Perfect scope match + MSME fit + India fit + method match
- 4: Strong match on 3 of 4 criteria
- 3: Good fit but requires reframing contribution
- 2: Possible with significant reframing
- 1: Unlikely fit without major repositioning

## Framing Options for Each Contribution Angle
- **Angle A (Methods):** "This paper develops and validates an ESG measurement instrument for MSMEs in India..." → Best for JCP, BSE, Sustainability
- **Angle B (Policy):** "This paper examines the regulatory gap between BRSR mandates for large firms and ESG capacity of MSMEs..." → Best for IIMB MR, JBE, APMJ
- **Angle C (Business Case):** "This paper provides empirical evidence that ESG adoption enhances business performance and competitiveness for Indian MSMEs..." → Best for JSBM, BSE, JCP

## Output Format

### Ranked Journal Table
```
| Rank | Journal | Fit Score | Best Angle | APC | Time to Decision | Key Requirement |
|---|---|---|---|---|---|---|
| 1 | [name] | [1-5] | [A/B/C] | [fee/free] | [months] | [main requirement] |
```

### Top 3 Recommendations with Rationale
For the top 3 journals: write 3–4 sentences explaining exactly why it fits and what you must emphasize in the abstract and introduction to maximize acceptance chances.

### Submission Checklist for Recommended Journal
Generate a complete submission checklist for your top choice journal.