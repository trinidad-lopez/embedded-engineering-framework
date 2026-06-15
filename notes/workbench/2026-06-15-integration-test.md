# 2026-06-15 - Workbench Integration Test

Status: reviewed

## Scope

First read-only/draft-only integration test between this framework repo and the personal AI workbench.

The workbench source code was not changed.

## Commands Used

```powershell
python .\paw.py sources doctor
python .\paw.py agent status --name embedded-engineering-framework
python .\paw.py agent probe --name embedded-engineering-framework --goal "Summarize framework readiness: identify structure, open loops, missing routing rules, and integration risks" --search "TO-DO" --search "Status: raw" --search "Next review" --search "active" --check git-status
python .\paw.py agent prepare-work --name embedded-engineering-framework --goal "Inbox triage test: review docs/inbox.md and notes/inbox. If there are no real inbox items, report empty-state behavior and next useful test data needed." --item embedded-engineering-framework:docs/inbox.md --item embedded-engineering-framework:notes/inbox/README.md --search "Status: raw" --search "Unprocessed Notes" --check git-status --stdout
python .\paw.py agent prepare-work --name embedded-engineering-framework --goal "Concept expansion test: identify one raw or incomplete concept that can be converted into a concept note using templates/concept-note.md." --item embedded-engineering-framework:docs/knowledge-base.md --item embedded-engineering-framework:templates/concept-note.md --search "TO-DO" --check git-status --stdout
python .\paw.py agent prepare-work --name embedded-engineering-framework --goal "Project scoping test: identify whether project ideas exist and whether templates/project-brief.md is enough to scope one." --item embedded-engineering-framework:docs/project-roadmap.md --item embedded-engineering-framework:docs/quick-projects.md --item embedded-engineering-framework:templates/project-brief.md --search "Project" --check git-status --stdout
python .\paw.py agent prepare-work --name embedded-engineering-framework --goal "Portfolio extraction test: find completed or nearly completed work that could become a portfolio entry, with evidence and next action." --item embedded-engineering-framework:docs/progress-tracker.md --item embedded-engineering-framework:docs/portfolio.md --item embedded-engineering-framework:templates/portfolio-entry.md --search "Completed" --search "Session 001" --search "Milestones" --check git-status --stdout
python .\paw.py guide "I want to triage notes in embedded-engineering-framework" --json
```

## Confirmed Readiness

- Source registry has `embedded-engineering-framework` as a Git-backed project source.
- Agent session `embedded-engineering-framework` exists.
- Session workspace exists under ignored workbench state.
- Workbench can probe the repo without source-registry errors.
- Workbench can see the repo-owned `docs/`, `notes/`, `projects/`, and `templates/` structure.
- Workbench can assemble deterministic prepare-work packets from explicit file selections and searches.
- Workbench kept source mutation disabled during the test.

## Framework Content Findings

- `docs/inbox.md` currently has no real unprocessed inbox items after the separator.
- `notes/inbox/` currently contains only its routing README.
- `docs/knowledge-base.md` has two incomplete concept entries:
  - `API vs ABI`
  - `Compile-time safety vs. Runtime flexibility`
- `docs/project-roadmap.md` and `docs/quick-projects.md` provide enough project ideas to scope a project brief, but no project has been selected into `projects/planned/` or `projects/active/` yet.
- `docs/progress-tracker.md` and `docs/portfolio.md` provide extraction templates and examples, but there is not enough real completed-project evidence yet for a portfolio entry.

## Workbench Integration Observations

- Generic `prepare-work` packets can truncate large docs such as `docs/knowledge-base.md`, `docs/project-roadmap.md`, `docs/progress-tracker.md`, and `docs/portfolio.md`.
- For real concept expansion, use a narrower query or split the target concept into its own note before expecting good draft context.
- For project scoping, the standalone `templates/project-brief.md` is easy for the workbench to inspect.
- Natural-language `paw guide "I want to triage notes in embedded-engineering-framework"` fell back to broad overview because model-assisted classification could not connect to Ollama.
- The deterministic guide fallback stayed safe, but it did not infer the active `embedded-engineering-framework` session from the request.

## Not Bugs Yet

These are worth watching, but should not trigger workbench code changes yet:

- Large-doc truncation in generic packets may be acceptable if the framework splits active work into smaller files.
- Natural-language guide routing may improve once model assist is available or once there is an active task/session context.
- Empty inbox and empty project folders limit the test value; the framework needs realistic sample notes before deeper workflow conclusions.

## Next Test Data Needed

Add or choose:

- one raw inbox note
- one raw concept note
- one project idea to scope
- one real or historical progress entry

## Recommended Next Test

Use `API vs ABI` as the first concept expansion candidate.

Expected promotion path:

```text
docs/knowledge-base.md TODO
  -> notes/concepts/api-vs-abi.md
  -> later summarize/link back into docs/knowledge-base.md
```

Use one roadmap item, such as `Circular Buffer (Ring Buffer)`, as the first project scoping candidate.

Expected promotion path:

```text
docs/project-roadmap.md
  -> projects/planned/circular-buffer/project-brief.md
```

