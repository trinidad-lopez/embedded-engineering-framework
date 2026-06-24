# Framework Scope

Status: draft
Last updated: 2026-06-23

---

## 1. Purpose

This framework exists to organize long-term technical learning, projects, notes, experiments, resources, reviews, and evidence of progress.

It started from embedded engineering growth, but it is intended to support multiple technical learning domains, including embedded systems, AI/LLM fundamentals, workbench development, control systems, networking, and future areas of study.

The framework should help me:

* capture ideas before they are lost
* turn scattered notes into structured knowledge
* connect learning with concrete projects
* track progress across different domains
* review weak areas without losing context
* make future AI feedback easier and better grounded
* avoid mixing raw notes, refined knowledge, and project evidence
* build a reusable personal learning and project management system

---

## 2. What belongs in this framework

This repo should contain:

* learning domains
* skill trees
* learning roadmaps
* project briefs
* project tracking files
* reviewed knowledge notes
* raw and refined notes
* experiments
* debugging records
* resource lists
* progress reviews
* portfolio candidates
* reusable templates
* AI review instructions
* workbench/operator integration notes

---

## 3. What does not belong here

This repo should not become:

* a dump of unreviewed random notes
* a replacement for every project repository
* a storage place for large generated codebases
* a storage place for private credentials, tokens, or secrets
* a storage place for large binaries or datasets
* a collection of resources with no learning or project plan
* a place where all domains are mixed into one giant document

Raw notes can be captured here, but they should eventually be routed, reviewed, refined, or archived.

---

## 4. Main structure

| Folder       | Purpose                                                                   |
| ------------ | ------------------------------------------------------------------------- |
| `docs/`      | Framework-level instructions, scope, navigation, and operating rules      |
| `domains/`   | Domain-specific learning systems                                          |
| `projects/`  | Active and archived projects                                              |
| `notes/`     | Raw, processed, and refined notes                                         |
| `templates/` | Reusable templates for domains, projects, notes, reviews, and experiments |
| `reviews/`   | Periodic reviews and AI feedback outputs                                  |
| `resources/` | Optional cross-domain resources or references                             |

---

## 5. Folder responsibilities

### `docs/`

Contains framework-level documents.

This folder should answer:

* What is the framework for?
* How is it organized?
* What domains exist?
* How should notes be routed?
* How should AI review the repository?
* How does the workbench interact with the framework?

Examples:

* `framework-scope.md`
* `domains.md`
* `framework-guide.md`
* `inbox.md`
* `templates.md`
* `workbench-integration.md`
* `framework-operator-guide.md`

---

### `domains/`

Contains one folder per long-term learning domain.

A domain is a broad area of study that has its own concepts, projects, resources, roadmap, and progress tracking.

Examples:

* `domains/embedded/`
* `domains/ai-llm/`

Each domain should usually contain:

* `domain.md`
* `skill-tree.md`
* `roadmap.md` or `project-roadmap.md`
* `projects.md`
* `resources.md` or domain-specific resource files
* `progress.md`
* `knowledge-base.md`

Optional files:

* `review-questions.md`
* `experiments.md`
* `debugging-playbook.md`
* `portfolio-candidates.md`

---

### `projects/`

Contains concrete projects.

A project should produce evidence. It should not only be a vague topic of interest.

A project should answer:

* What am I building or investigating?
* Why does this project matter?
* Which domain does it support?
* What skills does it prove?
* What is the success condition?
* What artifacts should exist when it is done?

Projects may belong to one or more domains.

---

### `notes/`

Contains notes at different levels of maturity.

Suggested note stages:

| Stage     | Meaning                            |
| --------- | ---------------------------------- |
| raw       | Captured quickly, not reviewed     |
| processed | Cleaned up and organized           |
| refined   | Reviewed and useful as reference   |
| archived  | Kept for history, no longer active |

Notes should not all become permanent knowledge. Some notes are only temporary thinking artifacts.

---

### `templates/`

Contains reusable structures for common document types.

Templates should make it easier to start new domains, projects, notes, reviews, and experiments without inventing the structure every time.

---

## 6. Domain rule

Create a new domain when most of these are true:

* it will be studied for more than a few weeks
* it has its own core concepts
* it has its own projects
* it has its own resources
* it needs its own progress tracking
* it would make another domain too messy if kept there
* it can produce evidence of progress

Do not create a new domain when:

* it is only one small concept
* it belongs clearly inside an existing domain
* it has no project, roadmap, or review plan
* it is only a temporary curiosity

---

## 7. Project rule

A project is a concrete effort that produces evidence.

A project can be:

* learning-focused
* implementation-focused
* experiment-focused
* portfolio-focused
* research-focused
* debugging-focused

Every project should have a `project-brief.md` or equivalent project control file.

A project should define:

* purpose
* domain alignment
* learning goals
* success criteria
* active tasks
* evidence to collect
* review questions
* current status

---

## 8. Knowledge rule

The framework should distinguish between:

| Type                 | Meaning                                     |
| -------------------- | ------------------------------------------- |
| raw note             | Initial capture, may be messy or incomplete |
| concept note         | Focused explanation of one concept          |
| knowledge-base entry | Reviewed, stable reference                  |
| project artifact     | Evidence from actual work                   |
| review               | Assessment of progress or weakness          |
| resource             | External material used for learning         |

A concept is not considered mastered just because it appears in a note or skill tree.

---

## 9. AI feedback rule

AI review should be grounded in files, evidence, and the current state of the framework.

AI should:

* cite or reference relevant files when possible
* distinguish between plans, notes, and proven progress
* avoid assuming mastery from topic names
* identify weak areas
* suggest staged next actions
* preserve the user’s stated goals and constraints
* avoid overwhelming information dumps
* prefer small concrete improvements over large rewrites

AI should not:

* assume missing information means the user does not know it
* assume written information means mastery
* treat drafts as final decisions
* mix domain-specific guidance into framework-level documents without reason

---

## 10. Evolution rule

The framework should evolve gradually.

Prefer:

* small structural improvements
* stable naming
* clear file boundaries
* linked files instead of giant documents
* migration notes when moving files
* preserving useful existing content

Avoid:

* large rewrites without need
* moving everything at once
* duplicating the same information in many places
* creating too many templates before they are needed

---

## 11. Current direction

The current evolution is:

* keep embedded systems as the first mature domain
* move embedded-specific content under `domains/embedded/`
* keep framework-level rules under `docs/`
* add AI/LLM fundamentals as a new domain
* track the tiny transformer / LLM fundamentals project as an active project
* keep using project briefs, progress logs, reviews, and evidence as the main feedback loop

---

## 12. Review questions

When reviewing this framework, ask:

* Is `docs/` still framework-level?
* Are domain-specific files under the correct domain?
* Are projects connected to domains?
* Are notes being refined or just accumulating?
* Are templates helping or adding friction?
* Is there enough evidence to support claimed progress?
* Can AI understand the current state without hidden context?
