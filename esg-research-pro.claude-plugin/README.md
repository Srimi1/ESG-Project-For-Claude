# ESG-Research-Pro Plugin

> Built for the paper: **"Integrating Sustainability into MSME Operations in India: A Study of ESG Practices and Business Performance"**

---

## What This Plugin Does

This plugin turns Claude Co-work into a full academic research pipeline assistant. It contains 8 skills, 8 sub-agent personalities, and 5 slash commands that cover every stage of your research paper — from literature screening to pre-submission peer review.

---

## Quick Start

### Step 1: Install Required Connectors
Go to **Connectors → Browse** and enable:
- Zotero MCP (paste your Zotero API key)
- Google Drive (sign in)
- Notion (paste integration token)
- Semantic Scholar (free, no key)
- CrossRef (free, no key)

### Step 2: Install This Plugin
Upload `ESG-Research-Pro.zip` via **Plugins → Upload → Install**

### Step 3: Set Memory Context
Paste this into **Memory panel**:
```
Project: ESG practices and business performance in Indian MSMEs
MSME definition: MSMED Act 2020
Key frameworks: BRSR (SEBI), GRI Standards 2021, UN SDGs 8/12/17
Target journals: Journal of Cleaner Production, Business Strategy & Environment
Tools: Zotero, Google Drive, Notion
```

---

## Commands

| Command | What It Does | When to Use |
|---|---|---|
| `/literature-review` | Screen + synthesize + gap-spot papers in parallel | Processing batches of papers |
| `/write-review` | Edit draft section + verify citations | After drafting any section |
| `/methods-check` | Stress-test methodology section | Before data collection or submission |
| `/pre-submission` | Full peer review + citation audit + journal match | Before submitting to journal |
| `/full-pipeline` | Runs all skills end-to-end | Starting a new major draft phase |

---

## Skills Overview

| Skill | Purpose |
|---|---|
| `paper-screener` | Screen papers for MSME-India-ESG relevance |
| `literature-synthesizer` | Organize papers into 5 themed sections |
| `gap-spotter` | Find research gaps + draft contribution statements |
| `methods-critic` | Review methodology for validity and rigor |
| `draft-editor` | Edit prose for academic style and consistency |
| `cite-verifier` | Validate all references against CrossRef and Semantic Scholar |
| `journal-matcher` | Match paper to best-fit journals with framing advice |
| `peer-reviewer` | Simulate formal peer review report |

---

## Batch Size Guide

| Task | Recommended Papers per Agent | Number of Agents |
|---|---|---|
| Paper screening | 10 | 3–5 |
| Citation verification | 15 | 3–4 |
| Survey question review | 12 questions | 3 |
| Section editing | 1 section | 1 per section |

---

## Project Context

- **Topic:** ESG (Environmental, Social, Governance) practices in Indian Micro, Small and Medium Enterprises
- **Research question:** Do ESG practices improve business performance in Indian MSMEs?
- **Key frameworks:** BRSR (SEBI), GRI Standards, UN SDGs, TCFD
- **Key regulatory bodies:** SEBI, MCA, SIDBI, RBI
- **Contribution angles:**
  - (A) ESG operationalization at MSME scale
  - (B) Regulatory gap — BRSR pressure without MSME support
  - (C) ESG as competitive enabler for MSMEs

---

## File Structure

```
ESG-Research-Pro/
├── plugin.json
├── README.md
├── skills/
│   ├── paper-screener.md
│   ├── literature-synthesizer.md
│   ├── gap-spotter.md
│   ├── methods-critic.md
│   ├── draft-editor.md
│   ├── cite-verifier.md
│   ├── journal-matcher.md
│   └── peer-reviewer.md
├── agents/
│   ├── screener-agent.md
│   ├── synthesizer-agent.md
│   ├── gap-agent.md
│   ├── methods-agent.md
│   ├── editor-agent.md
│   ├── citation-agent.md
│   ├── journal-agent.md
│   └── reviewer-agent.md
└── commands/
    ├── literature-review.md
    ├── write-review.md
    ├── methods-check.md
    ├── pre-submission.md
    └── full-pipeline.md
```
