# Domains

Status: draft | active | stable  
Last updated: YYYY-MM-DD

---

## 1. Purpose

This file tracks all learning domains in the framework.

A domain is a long-term area of learning that has its own concepts, projects, resources, roadmap, and progress tracking.

This file is not the detailed plan for each domain. It is the index.

Detailed domain files live under:

- `domains/<domain-name>/domain.md`

---

## 2. Domain list

| Domain | Status | Current focus | Level | Path |
|---|---|---|---|---|
| Embedded Systems | active | <current focus> | <level> | `domains/embedded/domain.md` |
| AI / LLM Fundamentals | active | <current focus> | <level> | `domains/ai-llm/domain.md` |
| <Domain Name> | planned | <focus> | <level> | `domains/<domain>/domain.md` |

---

## 3. Active domains

### Embedded Systems

Status: active  
Path: `domains/embedded/domain.md`

Purpose:

<Short explanation of why this domain exists.>

Current focus:

- <focus>
- <focus>

Active projects:

- <project>
- <project>

---

### AI / LLM Fundamentals

Status: active  
Path: `domains/ai-llm/domain.md`

Purpose:

<Short explanation of why this domain exists.>

Current focus:

- <focus>
- <focus>

Active projects:

- <project>
- <project>

---

## 4. Planned domains

| Domain | Why it may become a domain | When to create |
|---|---|---|
| <domain> | <reason> | <condition> |

---

## 5. Paused domains

| Domain | Why paused | Revisit condition |
|---|---|---|
| <domain> | <reason> | <condition> |

---

## 6. Archived domains

| Domain | Why archived | Archive path |
|---|---|---|
| <domain> | <reason> | <path> |

---

## 7. Domain creation criteria

Create a new domain when most of these are true:

- it will be studied for more than a few weeks
- it has its own project roadmap
- it has its own core concepts
- it has its own resources
- it has its own progress evidence
- it would make another domain too messy if kept there

Do not create a new domain when:

- it is only one small concept
- it belongs clearly inside an existing domain
- it has no project or review plan
- it is only a temporary curiosity

---

## 8. Standard domain folder

Each domain should usually contain:

| File | Purpose |
|---|---|
| `domain.md` | Domain overview and navigation |
| `skill-tree.md` | Skills and levels |
| `roadmap.md` | Learning/project sequence |
| `projects.md` | Projects that prove progress |
| `resources.md` | Resources and references |
| `progress.md` | Progress tracking and reviews |
| `knowledge-base.md` | Stable reviewed knowledge |
| `review-questions.md` | Optional self-testing |
| `experiments.md` | Optional experiments |

---

## 9. Cross-domain projects

Some projects may belong to more than one domain.

Example:

| Project | Primary domain | Secondary domains |
|---|---|---|
| <project> | <domain> | <domain>, <domain> |

The project should live where it is easiest to maintain, but each related domain should link to it.

---

## 10. Domain review cadence

| Domain | Review cadence | Next review |
|---|---|---|
| Embedded Systems | weekly / biweekly / monthly | YYYY-MM-DD |
| AI / LLM Fundamentals | weekly / biweekly / monthly | YYYY-MM-DD |

---

## 11. AI review instructions

When reviewing this file, AI should:

- check whether the domain split still makes sense
- identify overloaded domains
- identify domains that should be merged
- identify topics that should become projects instead of domains
- check whether active domains have current projects and evidence
- avoid suggesting new domains without a clear reason