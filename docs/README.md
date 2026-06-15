# Documentation Map

This file is the routing table for the framework. Start here when deciding where a note, project idea, learning question, or work session belongs.

## Capture First

- [inbox.md](inbox.md): rough notes, questions, project sparks, concepts you do not understand yet, and unprocessed Notepad++-style fragments.
- [templates.md](templates.md): copyable structures for turning rough notes into durable entries.

The inbox is allowed to be messy. The rest of the repo should become clearer over time.

## Core System

- [framework-guide.md](framework-guide.md): how to use the framework and run review cycles.
- [skill-tree.md](skill-tree.md): staged embedded engineering skill map.
- [progress-tracker.md](progress-tracker.md): work sessions, milestones, and visible progress.
- [knowledge-base.md](knowledge-base.md): concept explanations and technical notes.
- [project-roadmap.md](project-roadmap.md): larger project ideas and staged learning projects.
- [quick-projects.md](quick-projects.md): small experiments for fast learning loops.
- [debugging-playbook.md](debugging-playbook.md): debugging process, cases, and failure patterns.
- [portfolio.md](portfolio.md): polished project writeups and interview-ready case studies.
- [books.md](books.md): long-term reference material.

## Where Things Belong

| If you have... | Put it first in... | Later refine into... |
| --- | --- | --- |
| A random note or question | `inbox.md` | `knowledge-base.md`, `progress-tracker.md`, or a project file |
| A concept you do not understand | `inbox.md` | `knowledge-base.md` |
| A project idea | `inbox.md` | `project-roadmap.md` or `quick-projects.md` |
| A bug or troubleshooting story | `debugging-playbook.md` | `portfolio.md` if it becomes a strong case study |
| A completed work session | `progress-tracker.md` | `portfolio.md` for major outcomes |
| A book/resource note | `inbox.md` | `books.md` or `knowledge-base.md` |

## Agent/Workbench Use

This repo should be easy for an assistant or deterministic tool to inspect:

- Keep current status and open loops visible in `progress-tracker.md`.
- Keep rough, untrusted notes in `inbox.md` until reviewed.
- Prefer small linked entries over one giant document when a topic becomes complex.
- Do not require private context to understand the repository state.

Useful future workbench tasks:

- summarize inbox items
- suggest where each note belongs
- turn a rough concept into a knowledge-base entry
- turn a project spark into a scoped quick project
- find stale questions or unresolved blockers
- extract portfolio candidates from progress sessions
