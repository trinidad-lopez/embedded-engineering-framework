# Domain: AI / LLM

Status: active  
Started: 2026-06-23  
Current focus: transformer fundamentals, tiny LLM implementation, attention, tokens, training, and inference mechanics
Current level: beginner  
Review cadence: weekly or as-needed

---

## 1. Purpose

This domain exists to build a real understanding of LLMs, transformers, training, inference, runtime constraints, and model adaptation.

The goal is not only to use AI tools, but to understand the fundamentals well enough to reason about model behavior, context windows, KV cache, LoRA/QLoRA, quantization, routing, and workbench architecture decisions.

This domain supports both learning and the development of a personal AI workbench.

---

## 2. Scope

This domain includes:

- tokens and tokenization
- embeddings
- tensors and tensor shapes
- transformer architecture
- attention
- Q/K/V
- attention heads
- causal masking
- prefill and decode
- KV cache
- context windows
- prompt structure
- next-token prediction
- loss and training loop fundamentals
- small educational language models
- LoRA and QLoRA basics
- quantization basics
- sparsity, pruning, and MoE basics
- evaluation of model behavior
- AI-assisted workflow design
- model routing and calibration for the workbench

This domain does not include yet:

- training a production-scale LLM
- distributed training infrastructure
- advanced GPU kernel optimization
- full research-level transformer variants
- large-scale dataset curation
- production model serving at scale
- AI product design unrelated to technical understanding

---

## 3. Why this matters

Personal reasons:

- If I'm going to use AI as a tool, I want to understand it and control it.
- I want to depend as little as possible on companies products, specially if they are subscription based.

Project/career reasons:

- It can open career opportunities as Ai is use in more sectors.
- It supports future work with agents, coding tools, and model assisted engineering workflows.

---

## 4. Domain files

| File | Purpose |
|---|---|
| `domain.md` | Index and current domain definition |
| `skill-tree.md` | Skills, levels, and capability map |
| `roadmap.md` | Learning/project sequence |
| `projects.md` | Projects that prove progress |
| `resources.md` | Books, papers, courses, repos, videos |
| `progress.md` | Current state and review history |
| `knowledge-base.md` | Stable concepts and refined notes |
| `review-questions.md` | Questionnaires used to test understanding |
| `experiments.md` | Small experiments used to test concepts |

---

## 5. Current active work

| Item | Type | Status | Link |
|---|---|---|---|
| LLM fundamentals notes | note | active | knowledge-base.md |
| LLM questionnaire review | note | active | review-questions.md |
| Tiny transformer / LLM fundamentals lab | project | planned | llm-fundamentals-lab/ |
| Workbench model routing and context architecture | project | active | personal-ai-workbench.git |

---

## 6. Current strengths

- Good systems-level intuition around LLM workflows.
- Clear interest in understanding fundamentals instead of memorizing corrections.
- Strong connection between LLM internals and workbench architecture.
- Good awareness that KV cache is not durable semantic memory.
- Good motivation to learn by implementing a tiny model.

---

## 7. Current weaknesses

- Transformer internals still need reinforcement.
- Q/K/V and attention heads need deeper understanding.
- Tensor shapes and internal representations need hands-on practice.
- GQA/MQA, KV heads, and cache size mechanics need review.
- Quantization, sparsity, pruning, and MoE need clearer separation.
- Training concepts should be connected to small experiments before scaling.

---

## 8. Current next actions

- [ ] Create or refine projects/active/llm-fundamentals-lab/project-brief.md
- [ ] Build a tiny character-level or token-level language model
- [ ] Implement tokenization, embeddings, attention, transformer block, loss, and generation
- [ ] Add a small KV cache experiment
- [ ] Write concept notes for tensors, embeddings, Q/K/V, attention heads, and KV cache
- [ ] Use questionnaires to test understanding after each learning phase
- [ ] Connect lessons back to the workbench architecture

---

## 9. Review questions

Questions that should guide feedback:

- What am I misunderstanding?
- What prerequisite knowledge is missing?
- Are my projects proving the right skills?
- Am I collecting useful evidence of progress?
- What should I do next?

---

## 10. AI feedback instructions

When reviewing this domain, AI should:

- identify conceptual gaps
- check if projects actually prove the claimed skills
- suggest next steps based on current level
- avoid assuming mastery because a topic is listed
- distinguish between notes, projects, and evidence
- keep feedback practical and staged

AI should not:

- dump advanced topics without a learning path
- assume missing topics are unknown
- treat this domain as complete just because files exist