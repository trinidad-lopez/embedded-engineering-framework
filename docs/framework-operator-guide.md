# Framework Operator Guide

This guide is the technical-user operating manual for using this repository with the personal AI workbench.

The workbench does not need to infer this framework automatically. Use the framework explicitly when you want durable notes, project planning, learning records, debugging cases, or portfolio extraction.

## Operating Principle

Use the framework repo as the source of truth.

Use the workbench for:

- context gathering
- search
- draft preparation
- note triage
- concept expansion
- project scoping
- portfolio candidate discovery

Do not treat generated workbench output as reviewed knowledge until it is promoted into this repo.

## One-Time Setup Check

Run this from the workbench repo:

```powershell
python .\paw.py sources doctor
python .\paw.py agent status --name embedded-engineering-framework
```

Expected:

- source `embedded-engineering-framework` is OK and Git-backed
- session `embedded-engineering-framework` points to this repo
- session workspace exists under ignored workbench state

If the session is missing, initialize it from the workbench repo:

```powershell
python .\paw.py agent init --name embedded-engineering-framework --repo C:\Users\jtlopez\Documents\embedded-engineering-framework --source embedded-engineering-framework --check git-status --context-budget 6000 --force
python .\paw.py agent workspace init --name embedded-engineering-framework --register-notes
```

## Safety Defaults

For framework work, prefer read-only or draft-only commands first:

- `agent probe`
- `agent prepare-work`
- `agent search`
- `agent inspect`

Use Git branches for experiments:

```powershell
git switch -c test/<short-test-name>
```

Only merge reviewed artifacts back into the main branch.

## Status Check

Use this when starting a framework session:

```powershell
python .\paw.py agent probe --name embedded-engineering-framework --goal "Framework status check: summarize repo state, open loops, and likely next actions" --search "TO-DO" --search "Status: raw" --search "Next review" --check git-status
```

Expected output:

- Git state
- source registry state
- open TODOs or raw notes
- no source mutation

Search caveat:

- Search results may include command examples from this guide or previous workbench test reports.
- Treat those as command echoes, not real open notes.
- For precise work, rely on explicit `--item` selections plus narrow searches.

## Inbox Triage

Use this to triage rough notes:

```powershell
python .\paw.py agent prepare-work --name embedded-engineering-framework --goal "Inbox triage: review docs/inbox.md and notes/inbox. Suggest destinations and next review actions without deleting anything." --item embedded-engineering-framework:docs/inbox.md --item embedded-engineering-framework:notes/inbox/README.md --search "Status: raw" --search "Unprocessed Notes" --check git-status --stdout
```

Promote results into:

- `notes/concepts/`
- `notes/project-ideas/`
- `projects/planned/`
- `docs/debugging-playbook.md`
- `docs/progress-tracker.md`

If the inbox is empty, record that as a valid result. Do not invent notes.

## Concept Expansion

Use this when a concept is raw or incomplete:

```powershell
python .\paw.py agent prepare-work --name embedded-engineering-framework --goal "Concept expansion: prepare a standalone concept note for <concept-name> without editing docs/knowledge-base.md." --item embedded-engineering-framework:templates/concept-note.md --item embedded-engineering-framework:docs/knowledge-base.md --search "<concept-name>" --check git-status --stdout
```

Then create or review:

```text
notes/concepts/<concept-slug>.md
```

Promotion rule:

- Write the detailed concept in `notes/concepts/`.
- Later link or summarize it from `docs/knowledge-base.md` after review.
- Do not force every concept into the large knowledge-base document.

Example candidate:

```text
API vs ABI
```

## Project Scoping

Use this when a project idea is ready to become actionable:

```powershell
python .\paw.py agent prepare-work --name embedded-engineering-framework --goal "Project scoping: prepare a project brief for <project-name> without editing roadmap docs." --item embedded-engineering-framework:templates/project-brief.md --item embedded-engineering-framework:docs/project-roadmap.md --item embedded-engineering-framework:docs/quick-projects.md --search "<project-name>" --check git-status --stdout
```

Then create or review:

```text
projects/planned/<project-slug>/project-brief.md
```

Promotion rule:

- Keep roadmap docs as maps.
- Put actionable project briefs under `projects/planned/`.
- Move the folder to `projects/active/` when implementation starts.

Example candidate:

```text
Circular Buffer
```

## Session Logging

Use this after meaningful work:

```text
templates/session-log.md
```

For small work, record the session in `docs/progress-tracker.md`.

For active projects, prefer:

```text
projects/active/<project-slug>/sessions/YYYY-MM-DD-session.md
```

## Portfolio Extraction

Use this when a project has real evidence:

```powershell
python .\paw.py agent prepare-work --name embedded-engineering-framework --goal "Portfolio extraction: find completed or nearly completed work that could become a portfolio entry, with evidence and next action." --item embedded-engineering-framework:docs/progress-tracker.md --item embedded-engineering-framework:docs/portfolio.md --item embedded-engineering-framework:templates/portfolio-entry.md --search "Completed" --search "Milestones" --check git-status --stdout
```

Only promote a portfolio entry when there is evidence:

- project brief
- session logs
- validation result
- debugging record
- artifact link

## Using The Host Model Tunnel

The model tunnel can help with drafting, but deterministic context comes first.

Use the workbench to prepare context, then use model-assisted drafting only after the target and output path are clear.

Recommended order:

1. `agent probe`
2. `agent prepare-work`
3. human review of target and destination
4. optional model draft through the configured tunnel
5. save reviewed output into this repo

Do not rely on model-assisted guide routing as the only way to select the framework. Explicit session commands are more predictable.

## Current Friction

Known friction:

- large documents can be truncated in generic prepare-work packets
- natural-language guide may not infer this framework session
- broad searches can match command examples inside operator guides and workbench test reports
- empty inboxes and missing project evidence limit test value

Workaround:

- use explicit `--item` and `--search`
- prefer narrow search terms such as exact headings or project names
- keep active notes and projects in small files
- use branches for experiments

## Future Workbench Command Shape

These commands do not exist yet. They describe the desired user experience.

```powershell
paw framework status
paw framework triage-inbox
paw framework expand-concept "API vs ABI" --draft
paw framework scope-project "Circular Buffer" --draft
paw framework extract-portfolio-candidates
```

The important design rule is opt-in behavior:

- projects should not be forced to use this framework
- a session or project setting should enable framework workflows
- commands should remain draft-first and source-safe
