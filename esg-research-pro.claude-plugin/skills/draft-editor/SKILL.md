---
name: draft-editor
description: Edit draft sections for academic style, precision, and terminology consistency. Use on any section of your paper draft.
argument-hint: "<draft section text>"
---

# Skill: draft-editor

## Trigger
Use this skill whenever you want to refine a drafted section of the paper — Introduction, Literature Review, Methodology, Results, Discussion, or Conclusion.

## Goal
Edit the pasted section for academic style, precision, terminology consistency, logical flow, and compliance with the target journal's expectations. Return a clean diff showing original vs. revised sentences.

## Input Required
- The section text (paste directly into chat)
- Specify which section it is (Introduction / Lit Review / Methods / Results / Discussion / Conclusion)
- Optionally specify the target journal

## Agent File
→ `agents/editor-agent.md`

## Execution Mode
- Single section: Single agent
- Multiple sections simultaneously: Spin up 1 sub-agent per section (max 4 at once)

## Editing Rules Applied to Every Section

### Rule 1: Terminology Consistency
- Use "MSMEs" not "SMEs" — the Indian regulatory context uses MSME specifically
- Use "business performance" not "firm performance" (more accessible to interdisciplinary journals)
- Use "sustainability practices" for operational actions; "ESG" for the framework/reporting dimension
- Use "BRSR" (not "BRR" or "BR&SC") for India's Business Responsibility and Sustainability Report
- Ensure all acronyms are defined on first use: ESG, BRSR, MSMED Act, SEBI, MCA, SIDBI, GRI, SDG, TCFD

### Rule 2: Citation Discipline
- Flag every claim that has no citation (mark with: ⚠️ NEEDS CITATION)
- Flag vague citations like "(see various authors)" or "(many studies show)"
- Replace phrases like "researchers have shown" with specific citations

### Rule 3: Precision Over Vagueness
Replace these vague phrases with specific, cited claims:
- "ESG is increasingly important" → cite SEBI BRSR mandate date and scope
- "MSMEs are important to the Indian economy" → cite Ministry of MSME data (GDP %, employment figure, year)
- "Many firms are adopting sustainability" → cite a specific survey or report
- "Studies have shown a positive relationship" → name at least 2 specific studies

### Rule 4: Tense Consistency
- Literature review: past tense ("Smith (2021) found that...")
- Your conceptual framework: present tense ("The framework proposes...")
- Your empirical results: past tense ("The results showed...")
- Implications/conclusions: present or future ("This suggests that...")

### Rule 5: Paragraph Structure
Every paragraph in the Literature Review must:
1. Open with a topic sentence stating the theme
2. Review 2–3 papers with specific findings
3. Note any contradiction or variation in findings
4. Close by linking back to the Indian MSME context

### Rule 6: Section-Specific Rules

**Introduction:**
- Paragraph 1: Macro context (ESG + India economy)
- Paragraph 2: The specific problem (MSME ESG gap)
- Paragraph 3: Research question and objectives
- Paragraph 4: Contribution statement (use gap-spotter output)
- Paragraph 5: Paper structure overview

**Discussion:**
- Every finding must be interpreted with reference to a cited paper
- Must address: theoretical implication, practical implication, policy implication
- Must include a limitations paragraph before conclusion

## Output Format

### Section-Level Comment
One paragraph summary: overall quality, main strengths, main weaknesses.

### Line-by-Line Edit Table
```
| Original Sentence | Issue | Revised Sentence |
|---|---|---|
| [original] | [issue type: Vague / Needs citation / Wrong tense / Terminology / Structure] | [revised] |
```

### Uncitation-Flagged Sentences
List all sentences marked ⚠️ NEEDS CITATION separately for easy follow-up.

### Word Count
Report: original word count / revised word count / target word count for this section.