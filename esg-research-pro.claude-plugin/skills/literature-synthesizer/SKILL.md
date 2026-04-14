---
name: literature-synthesizer
description: Synthesize approved papers into 5 themed literature review sections. Use after screening to build the literature review body of your paper.
argument-hint: "<list of approved papers with abstracts>"
---

# Skill: literature-synthesizer

## Trigger
Use this skill after paper screening is complete. Takes screened, approved papers and synthesizes them into a themed literature review draft organized around the five core themes of this research paper.

## Goal
Transform a set of screened papers into a coherent, themed literature review with inline citations, identified contradictions, and a gap statement for each theme.

## Input Required
- Screened paper CSV (output from paper-screener skill) OR
- A list of approved paper titles/abstracts from Zotero

## Agent File
→ `agents/synthesizer-agent.md`

## Parallel Sub-Agent Instructions
- Assign one sub-agent per theme (5 agents total)
- Each agent receives: all paper abstracts/summaries + its assigned theme
- Main Claude assembles all 5 theme sections into one draft literature review

## The 5 Themes (one agent per theme)

### Theme 1: ESG Framework Applicability to MSMEs
Cover: Which ESG frameworks (GRI, BRSR, ISO 26000, UN SDGs) are relevant to small firms? What are the barriers of standard ESG frameworks for MSMEs? How have researchers adapted global frameworks for small/medium enterprises?

### Theme 2: ESG–Financial Performance Linkage
Cover: What does the evidence say about ESG improving/hurting financial performance? Focus on emerging market and SME-level studies. Highlight contradictions (e.g., short-term cost vs. long-term gain). Note the measurement problem (ROA/ROE vs. non-financial metrics).

### Theme 3: Sustainability Barriers in MSMEs
Cover: What prevents MSMEs from adopting ESG practices? (Cost, awareness, capacity, regulatory complexity, lack of incentives.) India-specific barriers where available. Distinguish between micro, small, and medium tier barriers.

### Theme 4: Indian Regulatory Context
Cover: BRSR mandate by SEBI (top 1000 listed companies), MCA sustainability guidelines, MSMED Act 2006/2020 definitions, SIDBI green finance initiatives, RBI priority sector lending for green MSMEs, UN SDG alignment in Indian policy.

### Theme 5: Measurement and Metrics for ESG at MSME Scale
Cover: How is ESG measured in small firms? Self-reported surveys vs. secondary data vs. composite indices. Validity and reliability concerns. Non-financial performance metrics (supply chain access, credit access, brand trust, employee retention).

## Output Format Per Theme
Each agent returns:
```
## Theme [N]: [Theme Name]

[200–300 word synthesized paragraph with inline citations (Author, Year)]

**Key finding:** [1 sentence summarizing what the literature agrees on]
**Key contradiction:** [1 sentence on what is disputed]
**Gap relevant to this paper:** [1 sentence on what is missing for Indian MSMEs]
```

## Post-Processing (Main Claude)
1. Assemble all 5 theme sections in order
2. Add transition sentences between themes
3. Write a 100-word concluding paragraph: "Taken together, these five streams of literature suggest that..."
4. List all citations used (author-year format) at the end
5. Estimate total word count and flag if under 1,200 or over 2,000 words
6. Offer to save the draft to Google Drive as: ESG-MSME-LitReview-Draft-v1