---
name: gap-spotter
description: Identify research gaps in the ESG-MSME literature and draft contribution statements. Use after synthesis to position your paper's contribution.
argument-hint: "<synthesized literature sections>"
---

# Skill: gap-spotter

## Trigger
Use this skill after literature synthesis is complete. Identifies specific research gaps in the ESG–MSME literature and drafts contribution statements for the paper's introduction.

## Goal
Systematically audit the synthesized literature across 6 gap dimensions. Return a gap matrix and three ready-to-use contribution bullet points.

## Input Required
- Synthesized literature review (output from literature-synthesizer) OR
- A summary of what the literature currently covers

## Agent File
→ `agents/gap-agent.md`

## Execution Mode
Single agent — this is a reasoning and synthesis task, not a bulk task.
Do NOT spin up parallel sub-agents for this skill.

## The 6 Gap Dimensions to Audit

### Gap 1: Geography Gap
Is India specifically understudied compared to China, Brazil, or developed markets?
Check: How many of the reviewed papers are India-specific vs. general emerging market vs. developed?
Flag if: Fewer than 20% of empirical papers are set in India.

### Gap 2: Firm-Size Gap
Are MSMEs (micro + small + medium) studied separately from large firms?
Check: Do papers disaggregate findings by firm size tier?
Flag if: Most papers lump all firm sizes together or focus only on large/listed firms.

### Gap 3: ESG Dimension Gap
Are Environmental, Social, and Governance dimensions studied separately or always as a composite?
Check: Do papers study individual E, S, G effects vs. composite ESG scores?
Flag if: Most papers use only composite ESG scores without separating dimensions.

### Gap 4: Performance Measurement Gap
Is business performance measured beyond standard financial ratios (ROA/ROE)?
Check: Do papers include non-financial metrics — credit access, supply chain inclusion, customer trust, employee retention, regulatory compliance cost savings?
Flag if: Fewer than 30% of papers use non-financial performance metrics.

### Gap 5: Regulatory Context Gap
Do papers account for the post-2020 Indian regulatory context?
Check: BRSR Phase 2 requirements, revised MSMED Act 2020 investment+turnover definition, SEBI sustainability-linked finance guidelines.
Flag if: Most papers predate 2020 or ignore India-specific regulatory pressure on MSMEs.

### Gap 6: Sector Specificity Gap
Are specific MSME sectors studied (textiles, food processing, auto components, IT services) or is it always pan-MSME?
Check: Do papers control for or stratify by industry sector?
Flag if: Most papers treat Indian MSMEs as a homogeneous group.

## Output Format

### Section 1: Gap Matrix Table
```
| Gap Dimension        | Status in Literature              | Severity   |
|----------------------|-----------------------------------|------------|
| Geography            | [finding]                         | High/Med/Low |
| Firm-Size            | [finding]                         | High/Med/Low |
| ESG Dimension        | [finding]                         | High/Med/Low |
| Performance Metrics  | [finding]                         | High/Med/Low |
| Regulatory Context   | [finding]                         | High/Med/Low |
| Sector Specificity   | [finding]                         | High/Med/Low |
```

### Section 2: Three Contribution Statements
Draft three ready-to-use bullet points for the Introduction section:
```
Contribution 1 (Methods): "This study addresses the gap in ESG measurement 
at the MSME scale by..."

Contribution 2 (Policy): "By examining the Indian regulatory context 
post-2020 BRSR mandate, this paper contributes to..."

Contribution 3 (Theory): "This study extends [theory name] to the MSME 
context in an emerging economy by..."
```

### Section 3: Positioning Statement
One paragraph (100 words) that situates this paper in the literature:
"While prior research has established [X], empirical evidence from Indian MSMEs 
remains limited because [Y]. This paper addresses this gap by [Z]."

## Post-Processing (Main Claude)
1. Present the gap matrix with severity color coding (High = must address, Med = should address)
2. Ask: "Which contribution angle do you want to foreground — Methods, Policy, or Theory?"
3. Based on answer, recommend the best target journal from the journal-matcher skill
4. Offer to save gap findings to Notion page: "Research Gap Analysis — [date]"