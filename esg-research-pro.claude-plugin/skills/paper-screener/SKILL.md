---
name: paper-screener
description: Screen academic papers for MSME/India/ESG relevance. Use when you have a list of papers to evaluate — returns a scored CSV with Include/Maybe/No decisions.
argument-hint: "<CSV or list of papers with titles and abstracts>"
---

# Skill: paper-screener

## Trigger
Use this skill when you have a list of academic papers and need to evaluate their relevance to the research on ESG practices and business performance in Indian MSMEs.

## Goal
Screen any number of academic papers against five strict relevance criteria specific to this research paper. Return a scored, sortable CSV output.

## Input Required
- A list or CSV of papers with: Title, Authors, Year, Journal, DOI, Abstract

## Agent File
→ `agents/screener-agent.md`

## Parallel Sub-Agent Instructions
- Spin up 1 sub-agent per 10 papers
- Maximum 5 sub-agents at once
- Each agent receives its own batch of 10 papers
- Main Claude collects all results and merges into one final CSV

## Screening Criteria (applied by each sub-agent)

### Criterion 1: MSME / SME Level
Does the paper study sustainability or ESG at the level of small or medium enterprises (not just large/listed firms)?
- Score: YES / PARTIAL (includes SMEs among others) / NO

### Criterion 2: India or Emerging Market Context
Is the study set in India, South Asia, or another emerging/developing market?
- Score: INDIA / EMERGING MARKET (specify country) / DEVELOPED ONLY / CONCEPTUAL

### Criterion 3: ESG Dimensions Covered
Which ESG pillars does the paper address?
- Score: E only / S only / G only / E+S / E+G / S+G / ALL THREE / GENERAL SUSTAINABILITY

### Criterion 4: Business Performance as Outcome
Does the paper measure or discuss business/financial performance as a result of ESG or sustainability practices?
- Score: YES (financial) / YES (non-financial) / YES (both) / NO

### Criterion 5: Research Method
- Score: Survey / Secondary data / Case study / Mixed methods / Conceptual / Meta-analysis

## Output Format
Return a CSV with these exact columns:
```
Title | Authors | Year | Journal | DOI | MSME_Level | Geography | ESG_Dimensions | Performance_Outcome | Method | Relevance_Score (1-5) | One_Line_Finding | Include (Yes/Maybe/No) | Reason
```

## Relevance Scoring Guide
- 5: MSME-level + India + ESG + performance outcome + empirical
- 4: MSME-level + emerging market + ESG + empirical
- 3: SME-level or India context, but missing one key criterion
- 2: Large firms or developed market, but useful for framework/theory
- 1: Tangentially related, conceptual only

## Post-Processing (Main Claude)
After all sub-agents return results:
1. Merge all CSVs into one master file
2. Sort by Relevance Score (descending)
3. Flag all Score 4–5 papers as "Add to Zotero"
4. Summarize: total screened / included / excluded / maybes
5. Offer to add approved papers to Zotero collection: ESG-MSME-India/Screened & Approved