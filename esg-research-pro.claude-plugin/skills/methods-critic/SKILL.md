---
name: methods-critic
description: Stress-test your methodology section across 9 validity dimensions. Use before data collection or submission to identify weaknesses.
argument-hint: "<methodology section text or description>"
---

# Skill: methods-critic

## Trigger
Use this skill when you want to stress-test your methodology section before data collection, before sharing with your supervisor, or before submission.

## Goal
Act as a rigorous peer reviewer for the methodology section. Identify critical, moderate, and minor issues across 9 specific validity dimensions relevant to an ESG–MSME India study.

## Input Required
- Your methodology section (paste as text or attach from Google Drive)

## Agent File
→ `agents/methods-agent.md`

## Execution Mode
Single agent — deep critical reasoning task.
Do NOT spin up parallel sub-agents.

## The 9 Validity Dimensions to Check

### Dimension 1: MSME Definition Compliance
- Is the MSMED Act 2020 definition used? (Investment AND turnover criteria, not just investment)
- Is the sample stratified by tier: micro / small / medium?
- Is the geographic scope defined (pan-India, specific states/clusters)?
- CRITICAL if: the paper uses a non-standard or outdated MSME definition

### Dimension 2: ESG Measurement Validity
- How is ESG operationalized? Self-reported survey / secondary BRSR data / composite index?
- If survey: is construct validity established? (Cronbach's alpha, factor analysis, pilot test)
- If secondary: are BRSR disclosures available for MSME-scale firms? (Most aren't listed — flag this)
- If index: which index? Is it validated for the Indian context?
- CRITICAL if: ESG measurement approach has not been validated

### Dimension 3: Business Performance Measurement
- Which metrics are used? Financial (ROA/ROE/revenue growth) and/or non-financial (credit access, supply chain inclusion, customer trust)?
- Is the performance measurement time-lagged relative to ESG adoption? (Best practice)
- CRITICAL if: only one performance type is used without justification

### Dimension 4: Endogeneity / Reverse Causality
- Is it possible that better-performing firms adopt ESG (not that ESG drives performance)?
- Is this addressed via: instrumental variables, lagged variables, difference-in-differences, or explicitly acknowledged as a limitation?
- CRITICAL if: endogeneity is not addressed at all in a causal claim paper

### Dimension 5: Sector Controls
- Are MSME sectors controlled for in the analysis?
- Indian MSME sectors are highly heterogeneous (textiles, food, auto parts, IT)
- ESG pressures differ dramatically by sector (environmental regulations heavier in manufacturing)
- CRITICAL if: sector is not controlled for and the paper claims sector-neutral findings

### Dimension 6: Sample Size and Representativeness
- Is the sample size sufficient for the chosen analysis method?
  - For PLS-SEM: minimum 5x the maximum arrows pointing to any construct
  - For regression: minimum 10 observations per predictor variable
  - For CB-SEM: minimum 200 respondents recommended
- Is the sample geographically representative (one state only = limited generalizability)?
- MODERATE if: sample is convenience-based without acknowledgment

### Dimension 7: Non-Response Bias
- If using a survey: is non-response bias tested?
  - Wave analysis (compare early vs. late respondents)
  - Or comparison with known MSME population parameters
- MODERATE if: not tested and response rate below 50%

### Dimension 8: Common Method Bias
- If both ESG and performance are self-reported by the same respondent:
  - Is Harman's single-factor test conducted?
  - Or is the marker variable technique used?
- CRITICAL if: common method bias risk is high and not addressed

### Dimension 9: Regulatory and Temporal Context
- Does the methodology reflect post-2020 context?
  - BRSR Phase 2 requirements (effective FY2022-23)
  - Revised MSMED Act 2020 (investment + turnover thresholds)
- Is the data collection period specified?
- MODERATE if: data predates 2020 without clear justification

## Output Format

### Issue Table
```
| Dimension            | Issue Found                | Severity   | Suggested Fix                |
|----------------------|---------------------------|------------|------------------------------|
| MSME Definition      | [issue or "None found"]   | Critical/Moderate/Minor/OK | [fix] |
| ESG Measurement      | ...                       | ...        | ...                          |
| Performance Metrics  | ...                       | ...        | ...                          |
| Endogeneity          | ...                       | ...        | ...                          |
| Sector Controls      | ...                       | ...        | ...                          |
| Sample Size          | ...                       | ...        | ...                          |
| Non-Response Bias    | ...                       | ...        | ...                          |
| Common Method Bias   | ...                       | ...        | ...                          |
| Regulatory Context   | ...                       | ...        | ...                          |
```

### Priority Action List
1. MUST FIX before data collection: [list critical issues]
2. SHOULD FIX before submission: [list moderate issues]
3. ACKNOWLEDGE in limitations: [list minor issues that cannot be fixed]

### Strengths
List 2–3 methodological strengths already present in the section.