# Literary Adjudication Packet Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build and run a shared two-pass literary-criticism packet for Claude Code and a fresh Sol/high judge, then compare their verdicts without treating model agreement as proof.

**Architecture:** A noncanonical review directory contains one operational prompt, one evidence dossier with a section for every prior agent, and separate verdict targets. Each judge must write a blind manuscript-first pass before reading canon or reports, then adjudicate the dossier against the live text.

**Tech Stack:** Markdown, repository-local chapter files, Codex collaboration agents, shell-based structural verification.

## Global Constraints

- Do not edit `drafts/chapters/`, `docs/story/`, or `docs/work/revision-ledger.md`.
- Do not read `archive/`, git history, or suspended review material.
- Do not cap the number of accepted issues.
- Treat agent reports as allegations and the live manuscript as primary evidence.
- Presence of a clue does not establish narrative sufficiency.

---

### Task 1: Create the shared judge prompt

**Files:**
- Create: `reviews/2026-08-08-literary-adjudication/CLAUDE_CODE_PROMPT.md`
- Create: `reviews/2026-08-08-literary-adjudication/README.md`

**Interfaces:**
- Consumes: live manuscript paths and active canon paths from `AGENTS.md`.
- Produces: a self-contained protocol usable by Claude Code and Sol/high.

- [ ] Write a mandatory two-pass reading order.
- [ ] Add salience, timing, embodiment, and post-hoc-rationalization tests.
- [ ] Require a blind verdict artifact before canon/report access.
- [ ] Define the final verdict schema and output path.
- [ ] Add prohibitions on edits, archives, report-voting, and issue-count caps.

### Task 2: Create the agent evidence dossier

**Files:**
- Create: `reviews/2026-08-08-literary-adjudication/agent-dossier.md`

**Interfaces:**
- Consumes: all prior agent reports preserved in the current session.
- Produces: one labeled section per calibration, character, global, and prior-judge report.

- [ ] State that the dossier is secondary evidence, not ground truth.
- [ ] Include all three calibration reports.
- [ ] Include every character and minor-character audit.
- [ ] Include all four global audits.
- [ ] Include the previous Sol verdict separately as a prior ruling.
- [ ] Preserve disagreements instead of harmonizing them.

### Task 3: Verify packet isolation and coverage

**Files:**
- Verify: `reviews/2026-08-08-literary-adjudication/*.md`
- Verify unchanged: `drafts/chapters/`, `docs/story/`, `docs/work/revision-ledger.md`

**Interfaces:**
- Consumes: packet files from Tasks 1 and 2.
- Produces: evidence that every named report is represented and active story files are unchanged.

- [ ] Count and list dossier section headings.
- [ ] Search the prompt for required anti-rationalization rules.
- [ ] Run `git diff --exit-code -- drafts/chapters docs/story docs/work/revision-ledger.md`.
- [ ] Record any mismatch before launching judges.

### Task 4: Run a fresh Sol/high literary judge

**Files:**
- Read: `reviews/2026-08-08-literary-adjudication/CLAUDE_CODE_PROMPT.md`
- Read after blind pass: `reviews/2026-08-08-literary-adjudication/agent-dossier.md`
- Create: `reviews/2026-08-08-literary-adjudication/sol-literary-verdict.md`

**Interfaces:**
- Consumes: the same protocol and evidence available to Claude Code.
- Produces: a standalone Sol literary verdict with blind-pass and adjudication sections.

- [ ] Spawn a context-free `gpt-5.6-sol` agent with `high` reasoning.
- [ ] Require it to read the manuscript before canon and dossier.
- [ ] Review its returned verdict for required sections and evidence.
- [ ] Save the verdict without editing story or canon.

### Task 5: Run Claude Code and compare verdicts

**Files:**
- Create externally: `reviews/2026-08-08-literary-adjudication/claude-verdict.md`
- Read: both verdict files and the live manuscript.

**Interfaces:**
- Consumes: `claude-verdict.md` and `sol-literary-verdict.md`.
- Produces: a final disagreement matrix in conversation before any revision issue is opened.

- [ ] Give the author the exact Claude Code invocation prompt.
- [ ] Wait until Claude writes `claude-verdict.md`.
- [ ] Compare agreements, disagreements, canon conflicts, and unsupported claims.
- [ ] Verify high-risk claims directly in the manuscript.
- [ ] Ask the author for final decisions before opening revision issues.
