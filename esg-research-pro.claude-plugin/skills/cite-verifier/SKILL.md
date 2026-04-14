---
name: cite-verifier
description: Validate all references against CrossRef and Semantic Scholar. Use before submission to catch citation errors and formatting issues.
argument-hint: "<reference list or bibliography>"
---

# Skill: cite-verifier

## Trigger
Use this skill when you want to validate all references in your paper before submission, or after adding a batch of new references.

## Goal
Verify every reference against CrossRef, Semantic Scholar, and OpenAlex. Flag broken DOIs, mismatched metadata, unofficial sources, and Indian regulatory citations missing formal identifiers.

## Input Required
- A CSV or list of your references (Title, Authors, Year, Journal, DOI)
- Or export directly from Zotero as CSV

## Agent File
→ `agents/citation-agent.md`

## Parallel Sub-Agent Instructions
- Spin up 1 sub-agent per 15 references
- For 60 references: 4 sub-agents of 15 each
- Main Claude merges results and produces final audit report

## Verification Checks Applied to Every Reference

### Check 1: DOI Validity
- Does the DOI resolve to the correct paper?
- Status: VALID / BROKEN / MISSING
- If broken: attempt to find correct DOI via Semantic Scholar or CrossRef

### Check 2: Metadata Match
- Do author names match the DOI record?
- Does the year match?
- Does the journal name match?
- Flag any discrepancy (common with name changes, errata, or corrections)

### Check 3: Journal Legitimacy
- Is the journal indexed in SCOPUS, Web of Science, or DOAJ?
- Is it listed in Beall's list of predatory publishers?
- Flag: LEGITIMATE / PREDATORY RISK / CHECK REQUIRED

### Check 4: Indian Regulatory Citation Standards
For any reference citing Indian government documents (SEBI, MCA, SIDBI, RBI, Ministry of MSME):
- Must include the exact circular/notification number (e.g., "SEBI/LAD-NRO/GN/2021/22")
- Must include the official URL (sebi.gov.in, mca.gov.in, rbi.org.in, msme.gov.in)
- Must include the exact date of issue
- Status: COMPLETE / MISSING CIRCULAR NUMBER / WRONG URL / USE OFFICIAL SOURCE

### Check 5: MSME Statistics Source Check
For any statistic about Indian MSMEs (GDP contribution, employment numbers, count of MSMEs):
- Acceptable sources: MSME Ministry Annual Report, SIDBI MSME Pulse Report, RBI Annual Report, ASI (Annual Survey of Industries), CMIE Prowess
- Unacceptable: News articles, blog posts, Wikipedia, press releases
- Status: ACCEPTABLE SOURCE / FLAG — USE OFFICIAL SOURCE

### Check 6: Preprint vs. Published Version
- Is the paper cited in its preprint form (SSRN, arXiv, ResearchGate) when a published version exists?
- Flag: UPDATE TO PUBLISHED VERSION with journal name and DOI

### Check 7: Self-Citation Audit
- What percentage of citations are self-citations?
- Flag if self-citations exceed 15% of total references

### Check 8: Recency Check
- Flag references older than 2010 that are not foundational/classic citations
- Suggest: "Check if a more recent paper makes the same point"

## Output Format

### Full Reference Audit Table
```
| # | Reference (short) | DOI Status | Metadata | Journal | India Reg. | Source Type | Issue | Action Required |
|---|---|---|---|---|---|---|---|---|
| 1 | Smith et al. (2021) | VALID | MATCH | LEGITIMATE | N/A | Published | None | ✓ Keep |
| 2 | SEBI (2021) | N/A | N/A | GOV | MISSING CIRCULAR | Official | No circular no. | Add: SEBI/LAD... |
```

### Summary Dashboard
```
Total references reviewed: [N]
✓ Valid and complete: [N]
⚠️ Needs minor fix: [N]
✗ Critical issue: [N]
Predatory journal risk: [N]
MSME stat from unofficial source: [N]
Self-citation rate: [X]%
References pre-2010 (non-foundational): [N]
```

### Action List (Prioritized)
1. Fix immediately (broken DOIs, predatory journals)
2. Update (preprints with published versions)
3. Verify manually (uncertain journal status)
4. Acknowledge (acceptable limitations like pre-2010 foundational works)