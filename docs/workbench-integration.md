# Workbench Integration

This document defines how to test and use this framework with the personal AI workbench.

The repository remains the source of truth. The workbench is the active interface for inspection, note expansion, review, and temporary outputs.

## Current Integration Goal

Make the framework easy for the workbench to answer:

- What is open?
- What needs review?
- What notes are stale?
- What projects are active or ready to scope?
- What concepts need expansion?
- What completed work can become portfolio material?

## Source Ownership

Tracked in this repo:

- framework docs
- reviewed notes
- project briefs
- debugging cases
- progress and milestones
- portfolio drafts
- templates

Ignored workbench state:

- temporary workbench notes
- generated context packets
- model or assistant drafts
- task artifacts
- integration test outputs

Promote material from ignored workbench state into this repo only after review.

## Expected Workbench Setup

The workbench should have:

- a source entry named `embedded-engineering-framework`
- an agent session named `embedded-engineering-framework`
- a session workspace for temporary notes, drafts, and outputs

Useful checks:

```powershell
python .\paw.py sources doctor
python .\paw.py agent probe --name embedded-engineering-framework --goal "Summarize framework readiness" --check git-status
```

For daily command recipes, use [framework-operator-guide.md](framework-operator-guide.md).

## First Integration Test

Run these as read-only or draft-only tests first.

### 1. Repo Readiness Probe

Goal:

```text
Summarize the current framework structure, open loops, and missing routing rules.
```

Expected result:

- workbench sees the repo as Git-backed
- workbench can identify `docs/`, `notes/`, `projects/`, and `templates/`
- no source files are modified

### 2. Inbox Triage

Goal:

```text
Review docs/inbox.md and notes/inbox/. Suggest where each item should go.
```

Expected result:

- each item gets a destination
- uncertain items stay in inbox with a next review action
- no item is silently deleted

### 3. Concept Expansion

Goal:

```text
Turn one raw concept note into a reviewed concept note using templates/concept-note.md.
```

Expected result:

- output can be promoted to `notes/concepts/`
- the concept links to a related skill or project
- open questions remain explicit

### 4. Project Scoping

Goal:

```text
Turn one project idea into a project brief using templates/project-brief.md.
```

Expected result:

- output can be promoted to `projects/planned/`
- minimum useful version is clear
- validation criteria are concrete

### 5. Portfolio Extraction

Goal:

```text
Find completed or nearly completed work that could become a portfolio entry.
```

Expected result:

- candidates are listed with evidence
- sensitive or proprietary material is excluded
- next action is either draft, gather evidence, or reject

## Readiness Checklist

The framework is ready for daily workbench use when:

- [ ] new notes have an obvious capture path
- [ ] large notes can live as separate files
- [ ] project ideas can become project briefs
- [ ] active projects have a place for session logs and artifacts
- [ ] debugging cases have a reusable template
- [ ] portfolio extraction has a repeatable path
- [ ] workbench temporary outputs are not confused with repo-owned truth
- [ ] the workbench can probe the repo without path or source-registry errors

## Integration Gaps To Watch

During testing, record gaps in `notes/workbench/`.

Look for:

- unclear note routing
- duplicated templates
- missing project status fields
- stale inbox items
- notes that should be split into separate files
- workbench commands that require too much manual path knowledge
- outputs that are useful but hard to promote into the repo

## Open Source Tooling

The repo should stay plain Markdown and Git-first. Tools such as Foam or Obsidian can be useful as optional editors because they work over Markdown files and links, but the framework should not depend on one proprietary note database.

Useful compatibility rules:

- prefer normal Markdown links when possible
- keep filenames readable and stable
- avoid tool-specific block references for source-of-truth content
- keep templates as plain Markdown files
- keep Git history meaningful
