# Command: /methods-check

## Trigger
Type `/methods-check` in Claude Co-work chat.

## Purpose
Stress-test the methodology section against 9 validity dimensions specific to ESG–MSME India research. Returns a prioritized issue table with exact fixes. Single skill, single agent.

## When to Use
- BEFORE data collection — to catch design flaws early
- After designing your survey instrument — to validate before pilot
- Before sharing methodology with supervisor or co-authors
- As part of /pre-submission (it runs automatically there too)
- Anytime a reviewer or supervisor raises a methodological concern

## Input Prompt to Show User
```
/methods-check activated.

Please provide:
  1. Paste your full methodology section text below
     OR type "fetch from Drive [document name]" to pull from Google Drive
  2. What stage are you at?
     A: Pre-data collection (designing the study)
     B: Post-data collection (preparing for submission)
  3. What is your primary data collection method?
     [Survey / Secondary data (CMIE/MCA) / Mixed methods / Case study]
  4. What is your planned analysis technique?
     [PLS-SEM / CB-SEM / Multiple regression / Descriptive / Qualitative]
```

## Execution Steps

### Single Agent Run (methods-agent.md)
```
You are a research methodology reviewer for an ESG-MSME India paper.
Load your instructions from: agents/methods-agent.md
Stage: [A: pre-data / B: post-data]
Primary method: [method]
Analysis technique: [technique]
Review this methodology section across all 9 validity dimensions.
Return the full issue table and priority action list.
Methodology section: [paste text]
```

## Stage-Specific Focus

### Stage A (Pre-data collection) — Priority Checks
Focus on these first (still time to fix design):
1. MSME definition — is MSMED Act 2020 used?
2. Sampling frame — is it feasible? (Udyam Registration, SIDBI lists, industry associations)
3. ESG measurement — is a validated or pilotable instrument designed?
4. Sample size — is it sufficient for chosen analysis method?
5. Endogeneity — is a time-lag or control variable strategy planned?

### Stage B (Post-data collection) — Priority Checks
Focus on what can still be fixed:
1. Common method bias — can Harman's test be run post-hoc?
2. Non-response bias — can wave analysis be done?
3. Construct validity — have you run CFA and reported AVE/CR/Cronbach's alpha?
4. Sector controls — is sector included as a control variable?
5. Endogeneity — must be acknowledged in limitations if not addressed

## Final Output

```
METHODS-CHECK COMPLETE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

METHODOLOGY REVIEW REPORT
Stage: [Pre/Post data collection]
Method: [your method] | Analysis: [your technique]

ISSUE TABLE
[full 9-dimension table: Dimension | Issue | Severity | Fix]

CRITICAL ISSUES (Must Fix)
[numbered list — each with exact fix]

MODERATE ISSUES (Should Fix)
[numbered list — each with exact fix or acknowledgment text]

MINOR ISSUES (Acknowledge in Limitations)
[numbered list — draft limitation text provided]

METHODOLOGICAL STRENGTHS
[2–3 genuine strengths — do not change these]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
NEXT STEPS:
→ Address CRITICAL issues before proceeding
→ Type /write-review to edit the methods section with fixes applied
→ Type /pre-submission when ready for full paper review
```

## Bonus: Survey Instrument Check Mode
If you paste your survey questions instead of a methodology section:
```
"Check my survey instrument, not my methods section.
[paste survey questions]"
```
Claude will switch to survey critique mode: checking each question for clarity, cultural fit, double-barreled language, leading questions, and response scale consistency for an Indian MSME audience.


---

> **Final output only:** when all steps above are complete, run `human-writer` to humanize the assembled result and save it as `Methods-Critique-[YYYY-MM-DD].docx`.
