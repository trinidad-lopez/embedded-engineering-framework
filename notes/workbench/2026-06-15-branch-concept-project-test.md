# 2026-06-15 - Branch Concept And Project Test

Status: reviewed
Branch: `test/workbench-concept-project-2026-06-15`

## Scope

Test whether the framework can promote one incomplete knowledge-base item and one roadmap item into standalone repo-owned artifacts without editing the current knowledge base.

The workbench source code was not changed.

## Source Files Not Edited

- `docs/knowledge-base.md`
- `docs/project-roadmap.md`
- `docs/quick-projects.md`

## Artifacts Created

- `notes/concepts/api-vs-abi.md`
- `projects/planned/circular-buffer/project-brief.md`
- `docs/framework-operator-guide.md`

## Workbench Evidence Used

```powershell
python .\paw.py agent probe --name embedded-engineering-framework --goal "Start next framework integration test on branch without modifying current knowledge base" --search "API vs ABI" --search "Circular Buffer" --check git-status
python .\paw.py agent prepare-work --name embedded-engineering-framework --goal "Branch test: prepare context to create a standalone API vs ABI concept note without editing docs/knowledge-base.md" --item embedded-engineering-framework:templates/concept-note.md --item embedded-engineering-framework:docs/knowledge-base.md --search "API vs ABI" --search "Related skills" --check git-status --stdout
python .\paw.py agent prepare-work --name embedded-engineering-framework --goal "Branch test: prepare context to create a Circular Buffer planned project brief without editing roadmap docs" --item embedded-engineering-framework:templates/project-brief.md --item embedded-engineering-framework:docs/project-roadmap.md --item embedded-engineering-framework:docs/quick-projects.md --search "Circular Buffer" --search "Ring Buffer" --check git-status --stdout
```

## Findings

- The framework can promote a knowledge-base TODO into a standalone concept note without touching the knowledge base.
- The framework can promote a roadmap item into a planned project brief without touching roadmap docs.
- Standalone templates were useful because the workbench could inspect them without needing to parse `docs/templates.md`.
- Large source docs still produce truncated prepare-work packets, but targeted search terms were enough for this test.
- The operator guide recipes are runnable with current workbench commands.
- Broad search recipes can match command examples in the operator guide and prior workbench test reports.
- The operator guide itself can be truncated when inspected inside a generic prepare-work packet, so it should stay focused and link out instead of growing into a large manual.

## Next Review Questions

- Should `docs/knowledge-base.md` link to standalone concept notes instead of embedding every expanded concept?
- Should each planned project folder also include `sessions/`, `debugging/`, and `artifacts/` subfolders immediately, or only when the project becomes active?
- Should `projects/planned/circular-buffer/project-brief.md` be moved to `projects/active/` when implementation starts?
