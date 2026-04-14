# Command: /full-pipeline

## Trigger
Type `/full-pipeline` in Claude Co-work chat.

## Purpose
Runs the entire research paper pipeline end-to-end: literature screening → synthesis → gap analysis → methodology check → draft editing → citation verification → peer review → journal matching. Use when starting a major new draft phase or doing a comprehensive paper audit.

## When to Use
- At the beginning of a new major writing phase (e.g., you have new data and are drafting from scratch)
- For a comprehensive quarterly audit of your paper progress
- When onboarding a new co-author — gives them a full picture of the paper status
- NOT recommended for quick single-task work (use individual commands for that)

## ⚠️ Token Warning
This command uses significant tokens and takes 30–60 minutes.
**Recommended: Pro or Max plan only.**
If on a lower plan, run individual commands instead.

## Input Prompt to Show User
```
/full-pipeline activated.

This is the full end-to-end research pipeline. It will run all 8 skills 
in sequence. Please have the following ready:

  REQUIRED:
  □ Paper list CSV (for literature screening) — upload when prompted
  □ Current draft (full or partial) — paste or fetch from Drive
  □ Reference list — export from Zotero as CSV
  □ Abstract and keyword list

  OPTIONAL:
  □ Methodology section (for methods-check)
  □ Target journal preference

The pipeline will pause at key checkpoints for your confirmation 
before proceeding to the next stage.

Ready to start? Type YES to begin.
```

## Execution Sequence

```
STAGE 1 → /literature-review
  Skills: paper-screener → literature-synthesizer → gap-spotter
  Agents: screener-agent (parallel) + synthesizer-agent (parallel) + gap-agent
  ⏸ CHECKPOINT: Review gap findings. Confirm contribution angle (A/B/C) before proceeding.

STAGE 2 → /methods-check
  Skills: methods-critic
  Agents: methods-agent (single)
  ⏸ CHECKPOINT: Review critical methodology issues. Confirm you want to proceed to editing.

STAGE 3 → /write-review (all sections)
  Skills: draft-editor → cite-verifier (section-level)
  Agents: editor-agent (parallel — 1 per section, max 4) + citation-agent (targeted)
  ⏸ CHECKPOINT: Review edited sections. Confirm all ⚠️ citation flags are resolved.

STAGE 4 → /pre-submission
  Skills: cite-verifier (full) → peer-reviewer → journal-matcher
  Agents: citation-agent (parallel) + reviewer-agent + journal-agent
  Final output: Full submission audit report
```

## Checkpoint Behavior
At each ⏸ CHECKPOINT, Claude will:
1. Present the results from the completed stage
2. Ask: "Do you want to [fix any issues / adjust any settings] before proceeding?"
3. Wait for your confirmation ("proceed" or "yes") before starting the next stage
4. Allow you to exit the pipeline at any checkpoint without losing previous results

## Pipeline Progress Tracker
```
ESG-RESEARCH-PRO PIPELINE PROGRESS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[✓] Stage 1: Literature Review     ← completed
[→] Stage 2: Methods Check         ← in progress
[ ] Stage 3: Draft Editing
[ ] Stage 4: Pre-Submission Audit
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

## Final Output Assembly (Main Claude)

```
FULL PIPELINE COMPLETE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

OVERALL PAPER STATUS REPORT

LITERATURE
Papers screened: [N] | Included: [N] | Gaps identified: [N]
Key contribution: [selected angle]

METHODOLOGY
Issues found: [N critical] [N moderate] [N minor]
Status: [Ready for data / Needs revision / Post-data — acknowledge limitations]

DRAFT QUALITY
Sections reviewed: [N] | Total edits: [N]
Citations flagged: [N] needing resolution

SUBMISSION READINESS
Citation audit: [X/N] clean
Peer review verdict: [recommendation]
Recommended journal: [journal name]
Fit score: [X/5]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
MASTER TO-DO LIST

BEFORE DATA COLLECTION:
□ [item]

BEFORE NEXT DRAFT:
□ [item]

BEFORE SUBMISSION:
□ [item]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
All reports saved to:
→ Google Drive: ESG-MSME-Paper/Pipeline-Report-[date]
→ Notion: Research Progress — [date]
```

## Partial Pipeline Mode
If you only want to run specific stages, type:
```
"/full-pipeline stages 1,3" — runs literature review + draft editing only
"/full-pipeline stages 2,4" — runs methods check + pre-submission only
"/full-pipeline stage 4"    — runs pre-submission audit only
```
