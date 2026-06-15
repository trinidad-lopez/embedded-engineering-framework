# Embedded Engineer Growth Framework

A structured, project-driven training and thinking system for developing professional-level embedded software engineering skills.

This repository started as an embedded engineering growth framework, but it is also meant to become a practical home for project ideas, learning notes, debugging records, and technical thinking that should not disappear into scattered scratch files.

The core idea:

> Capture loosely, refine deliberately, and connect every useful note to a skill, project, question, or decision.

It should be usable directly by a human, and also easy for tools like Codex or the personal AI workbench to inspect without needing hidden context.

---

## Purpose

After transitioning from academic projects into professional embedded development, it became clear that systematic skill development was necessary to close knowledge gaps and build deep engineering competence.

This framework was created to:

- Track real engineering growth
- Structure embedded learning progression
- Document debugging experience
- Convert technical work into portfolio-ready case studies
- Focus on measurable capability rather than time-based goals
- Capture rough notes before they are forgotten
- Turn vague project ideas into actionable plans
- Keep learning questions visible until they are resolved

---

## Repository Structure

- **Docs Map** - Start at [docs/README.md](docs/README.md) to find the right place for notes, projects, concepts, and reviews.
- **Fast Inbox** - [docs/inbox.md](docs/inbox.md) is the fastest capture point for rough notes, questions, and ideas that are not organized yet.
- **Notes Folder** - [notes/](notes/) stores larger raw notes, reviewed concept notes, project ideas, and workbench-session notes as separate files.
- **Projects Folder** - [projects/](projects/) stores project briefs, active project logs, completed project records, and project artifacts.
- **Templates** - [templates/](templates/) contains standalone reusable templates; [docs/templates.md](docs/templates.md) summarizes them.
- **Skill Tree** - Defines staged progression from programming foundations to advanced embedded systems.
- **Project Roadmap** - Practical projects aligned with each skill stage.
- **Progress Tracker** - Tracks completed milestones, projects, and engineering sessions.
- **Debugging Playbook** - Documents real debugging cases and systematic troubleshooting.
- **Portfolio** - Converts completed projects into professional case studies.
- **Framework Guide** - Explains how the system is used.
- **Workbench Integration** - [docs/workbench-integration.md](docs/workbench-integration.md) explains how the personal AI workbench should inspect and test this repo.

The `docs/` directory contains the operating guide and index documents. The `notes/`, `projects/`, and `templates/` directories contain the durable working artifacts.

---

## Philosophy

This framework is:

- Progress-based, not time-based
- Project-driven, not theory-driven
- Focused on debugging and reliability
- Architecture-oriented
- Built around measurable engineering outcomes
- Capture-first, so rough notes have somewhere safe to land
- Review-driven, so notes eventually become knowledge, tasks, or decisions

Progress is measured by:

- Systems built
- Drivers implemented
- Bugs solved
- Architecture designed
- Reliability improved
- Concepts clarified
- Questions closed or made actionable

---

## Daily Use

Use the repository as a lightweight loop:

1. Capture rough thoughts in [docs/inbox.md](docs/inbox.md).
2. Use `notes/inbox/` when the captured item needs its own file.
3. Refine useful notes into the knowledge base, project roadmap, debugging playbook, progress tracker, or a project folder.
4. Keep active project work under `projects/active/` when it becomes more than a checklist item.
5. Link each refined note to a skill, project, question, or next action.
6. Periodically review open questions and stale ideas.

This keeps the system useful even when you only have a few minutes.

## Workbench Use

The personal AI workbench should treat this repository as the source of truth and use ignored local workbench state only for temporary sessions, drafts, outputs, and integration tests.

Initial workbench tasks to test:

1. Probe the repo and summarize open loops.
2. Triage `docs/inbox.md` and `notes/inbox/`.
3. Convert a raw note into a concept note.
4. Convert a project idea into a scoped project brief.
5. Extract portfolio candidates from progress and completed project records.

See [docs/workbench-integration.md](docs/workbench-integration.md) for the test workflow.

---

## Current Focus Areas

- Firmware architecture refinement
- Communication protocol design
- Real-time behavior analysis
- Debugging methodology
- Build systems and toolchain mastery
- Personal knowledge organization
- Project and learning planning

---

## Long-Term Objective

Reach advanced-level embedded systems capability suitable for:

- Aerospace systems
- Safety-critical firmware
- Flight control systems
- Distributed embedded architectures
- Bootloaders and firmware update systems

The broader objective is to build a durable personal engineering knowledge system that can support embedded work, general technical learning, project planning, and AI-assisted review.

---

## Author

Embedded Software Engineer  
Background in electronics engineering, STM32 driver development, DMA-based systems, protocol layers, and flight control software integration.

---

This repository represents ongoing professional development and continuous refinement.
