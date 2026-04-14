---
name: data-analysis-guide
description: Generate the Data Analysis Techniques subsection of your Methodology with justification for PLS-SEM/CB-SEM/regression/mediation, step-by-step analysis sequence, fit index thresholds, CMB test specification, and sample size check.
argument-hint: "<analysis type + sample size + software + number of constructs and indicators>"
---

# data-analysis-guide — Data Analysis Techniques Subsection Builder

Produces the "Data Analysis" or "Analytical Procedure" subsection of your Methodology section. This sub-section typically runs 150–250 words within the 600–800 word Methodology target.

## Agent File
→ `agents/analysis-agent.md`

## Execution Mode
Single agent.

## Input Required
1. **Analysis type** — PLS-SEM / CB-SEM / Multiple regression / Mediation (Hayes PROCESS) / Moderation / Mixed
2. **Sample size** — number of usable responses
3. **Software** — SmartPLS 4 / AMOS / R (lavaan) / SPSS / Stata
4. **Constructs** — number of latent constructs and number of indicators per construct
5. **Measurement scale** — Likert-5 / Likert-7 / binary / continuous

## Output Components

### 1. Method Justification Paragraph (~80 words)
- Why this method is appropriate for this model and data type
- Cite the canonical source: Hair et al. (2019) for PLS-SEM; Anderson & Gerbing (1988) for CB-SEM; Hayes (2018) for PROCESS
- Address sample size fit: "PLS-SEM is recommended for complex models with smaller samples (Hair et al., 2019); with N=[n], this study meets the minimum 10-times rule"
- If CB-SEM: justify why multivariate normality assumption is met or addressed

### 2. Analysis Sequence (numbered steps)
**For PLS-SEM:**
1. Assess measurement model: Cronbach's Alpha, CR, AVE, HTMT
2. Assess discriminant validity: Fornell-Larcker criterion / HTMT ratio
3. Run structural model: bootstrapping (5000 iterations), path coefficients, t-values, p-values, R²
4. Assess model fit: SRMR < 0.08
5. Conduct blindfolding for predictive relevance (Q² > 0)

**For CB-SEM:**
1. Confirmatory Factor Analysis (CFA): fit indices (CFI, TLI, RMSEA, SRMR)
2. Convergent validity: AVE > 0.50, CR > 0.70
3. Discriminant validity: HTMT < 0.85
4. Structural model: path coefficients, significance, R²
5. Model comparison if alternative models tested

**For Multiple Regression (OLS):**
1. Assumption checks: normality, homoscedasticity, independence (Durbin-Watson)
2. Multicollinearity: VIF < 10, Tolerance > 0.10
3. Hierarchical regression: enter controls in Block 1, IVs in Block 2
4. Report: β, t, p, ΔR², F-change

**For Mediation (Hayes PROCESS):**
1. Direct effect (path c')
2. Indirect effect via bootstrapping: 5000 iterations, 95% CI
3. Report: a × b indirect effect, LLCI, ULCI (significant if CI excludes zero)
4. Model number: PROCESS Model 4 (simple mediation), Model 6 (serial), Model 7 (moderated mediation)

### 3. Fit Index / Threshold Table
| Index | Threshold | Where to find in [software] |
|---|---|---|
| CFI | > 0.95 | Model Fit output |
| RMSEA | < 0.06 | Model Fit output |
| SRMR | < 0.08 | Model Fit output |
| AVE | > 0.50 | Construct Reliability output |
| CR | > 0.70 | Construct Reliability output |
| HTMT | < 0.85 | Discriminant Validity output |

### 4. Common Method Bias (CMB) Specification
- Test: Harman's single-factor exploratory factor analysis
- Threshold: single factor must not account for > 50% of total variance
- If Harman's > 50%: recommend marker variable technique or post-hoc statistical remedies
- Report in Results: "Harman's single-factor test revealed that one factor accounted for [X]% of variance, below the 50% threshold, indicating CMB is not a major concern"

### 5. Sample Size Adequacy Check
- PLS-SEM minimum: 10 × maximum number of paths pointing to any construct
- CB-SEM minimum: 200 (complex models) or 5–10 observations per indicator
- OLS minimum: 20 observations per predictor variable
- Report verdict: "The sample of N=[n] [meets / exceeds / marginally meets] the minimum requirement of [formula result]"
