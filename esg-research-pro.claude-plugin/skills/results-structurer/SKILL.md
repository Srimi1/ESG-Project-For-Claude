---
name: results-structurer
description: Structure raw statistical output (SEM fit indices, regression tables, mediation results) into a narrated Results section (1000–1200 words) with APA-7 in-text reporting, a hypothesis decision table, and flagged missing statistics.
argument-hint: "<raw statistical output: regression/SEM tables + hypothesis list + descriptive stats>"
---

# results-structurer — Results Section Builder

Takes numbers from your analysis software and turns them into a publication-ready Results section. Does not interpret findings — that is the Discussion section's job.

## Agent File
→ `agents/results-agent.md`

## Execution Mode
- Single agent for regression-only or SEM-only studies
- Up to 3 parallel sub-agents if study includes SEM + mediation + moderation (one sub-agent per analysis type)

## Input Required
1. **Hypothesis list** — numbered (H1, H2, ...) with direction and variable names
2. **Descriptive statistics table** — means, SDs, correlations
3. **Main analysis output** — regression coefficients / SEM path coefficients / fit indices
4. **Mediation/moderation results** (if applicable) — indirect effects, confidence intervals
5. **Common Method Bias test result** (if conducted)
6. **Software used** — SmartPLS / AMOS / R / SPSS

## Section Structure (Target: 1000–1200 words)

### Sub-section 1 — Descriptive Statistics (~150 words)
- Narrate the means, SDs, and correlations table
- Flag multicollinearity if VIF > 10 or correlation > 0.85 between predictors
- Report sample characteristics (firm size tier, sector, years of operation) in 2–3 sentences
- APA-7 format: "The mean score for environmental practices was M = 3.72 (SD = 0.81)"

### Sub-section 2 — Measurement Model / Reliability (for SEM studies, ~200 words)
- Report Cronbach's Alpha (> 0.70) and Composite Reliability (> 0.70) per construct
- Report Average Variance Extracted (AVE > 0.50) for convergent validity
- Report HTMT ratio (< 0.85) or Fornell-Larcker criterion for discriminant validity
- Confirm whether measurement model fits: CFI > 0.95, RMSEA < 0.06, SRMR < 0.08

### Sub-section 3 — Hypothesis Testing (~600 words)
- One paragraph per hypothesis (or hypothesis group if closely related)
- Each paragraph: state the hypothesis → report the statistic → state accepted/rejected
- APA-7 in-text format: "β = 0.34, SE = 0.07, t = 4.86, p < 0.001, 95% CI [0.21, 0.47]"
- For SEM: report path coefficient, t-value (bootstrapped), and p-value
- For regression: report β, t, p, and ΔR² where relevant
- For mediation: report indirect effect with bootstrapped CI (Hayes PROCESS or PLS bootstrapping)

### Sub-section 4 — Hypothesis Summary Table (~50 words + table)
| H# | Hypothesis | β / Indirect Effect | p | Decision |
|---|---|---|---|---|
| H1 | [statement] | [value] | [value] | Supported / Not Supported |

### Sub-section 5 — Additional Diagnostics (~100 words, if applicable)
- CMB: report Harman's single-factor variance (< 50% threshold)
- Endogeneity: report IV results or robustness check
- Moderation: report interaction term significance and plot direction

## SEM Fit Index Thresholds (baked into agent knowledge)
| Index | Acceptable | Good |
|---|---|---|
| CFI | > 0.90 | > 0.95 |
| TLI | > 0.90 | > 0.95 |
| RMSEA | < 0.08 | < 0.06 |
| SRMR | < 0.10 | < 0.08 |
| χ²/df | < 5.0 | < 3.0 |

## Flags Raised by Agent
- ⚠️ Missing: effect size (Cohen's f² or R²) not reported
- ⚠️ Missing: confidence intervals for key coefficients
- ⚠️ Non-significant result not acknowledged in text
- ⚠️ SEM fit indices below threshold — must address in limitations
- ⚠️ Results section contains interpretation — move to Discussion
