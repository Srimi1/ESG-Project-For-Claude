---
name: hypothesis-builder
description: Derive formal numbered hypotheses or propositions from your conceptual framework and theoretical basis, with one-line directional rationale and citation per hypothesis. Use before writing the Methodology section.
argument-hint: "<conceptual framework + theory used + independent/dependent/moderating variables>"
---

# hypothesis-builder — Hypothesis & Proposition Builder

Produces publication-ready hypotheses for quantitative studies or propositions for qualitative/mixed-method studies.

## Agent File
→ `agents/hypothesis-agent.md`

## Execution Mode
Single agent.

## Input Required
1. **Conceptual framework description** — variables and their proposed relationships
2. **Theory used** — Stakeholder Theory / Resource-Based View / Institutional Theory / Signaling Theory / other
3. **Variable list:** IVs, DVs, moderators, mediators (with construct names)
4. **Study type** — quantitative (hypotheses) or qualitative/mixed (propositions)
5. **Direction of expected relationships** — positive / negative / curvilinear / context-dependent

## Output Format

### Directional Hypotheses (Quantitative Studies)

Standard format for each hypothesis:
```
H[N]: [IV] is significantly and positively/negatively associated with [DV]
      among Indian MSMEs.

Rationale: According to [Theory], [mechanism in one sentence] (Author, Year).
```

For moderation:
```
H[N]: The relationship between [IV] and [DV] is moderated by [Moderator],
      such that the relationship is stronger/weaker when [Moderator] is high.

Rationale: [Theory] suggests [moderating mechanism] (Author, Year).
```

For mediation:
```
H[N]: [Mediator] mediates the relationship between [IV] and [DV].

Rationale: [Theory] proposes [causal chain] (Author, Year).
```

### Propositions (Qualitative / Mixed-Method Studies)
```
P[N]: [Phenomenon/practice] is associated with [outcome/characteristic]
      in the context of Indian MSMEs.

Theoretical basis: [Theory application] (Author, Year).
```

## Theory Application Guide (baked into agent knowledge)

**Stakeholder Theory (Freeman, 1984):**
- Predicts: ESG practices respond to stakeholder pressure → improve legitimacy → improve performance
- Use for: ESG → financial/non-financial performance hypotheses

**Resource-Based View (Barney, 1991):**
- Predicts: ESG capabilities are rare, inimitable resources → competitive advantage
- Use for: ESG investment → firm competitiveness / market differentiation hypotheses

**Institutional Theory (DiMaggio & Powell, 1983):**
- Predicts: MSMEs adopt ESG due to coercive (regulatory), mimetic (industry peer), normative (professional) pressure
- Use for: regulatory context → ESG adoption hypotheses

**Signaling Theory (Spence, 1973):**
- Predicts: ESG disclosure signals quality to external stakeholders → reduces information asymmetry
- Use for: ESG reporting → financing access / customer trust hypotheses

## Post-Build Checklist
- [ ] Each hypothesis is testable with the proposed methodology
- [ ] Direction is specified (positive/negative) not just "significant"
- [ ] Each hypothesis has one and only one IV and DV (no compound hypotheses)
- [ ] Null hypothesis implied (agent generates null form as reference)
- [ ] Hypotheses are numbered sequentially and match conceptual model
