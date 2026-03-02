---
name: smart-pole-coding-agent
description: Use when a coding task is vague or under-specified. Extracts missing context across 9 code-native categories before the agent executes file changes. Designed for OpenAI Codex, Anthropic Claude Code, and Google Gemini Code Assist.
---

# SMART POLE Coding Agent Skill

This Skill implements the **SMART POLE** framework adapted for **AI Coding Agents**. Unlike the chatbot versions (Instructor/Enforcer), this skill operates on **codebases** — scanning project files, extracting context automatically, and ensuring the agent has enough information before writing code.

## When to Use This Skill

- A user gives a vague coding task ("fix the login bug", "add pagination")
- Before an agent starts multi-file code changes
- When a task involves unfamiliar parts of a codebase
- Migration or refactoring tasks where scope control is critical

## How It Works

1. **ORIENT**: Agent scans project root (`README.md`, `AGENTS.md`, `package.json`, `Dockerfile`, etc.)
2. **CLASSIFY**: Determine task type (Bug Fix / Feature / Refactor / Migration / Infra)
3. **EXTRACT**: Map request to 9 code-native SP-categories
4. **DETECT FLAWS**: Identify missing context, overlaps, and conflicts; ask user if critical
5. **PLAN**: Create implementation plan with file-level scope
6. **EXECUTE**: Apply file changes within approved scope
7. **VERIFY**: Run tests, lint, type-check; self-heal on failures

## The 9 Code-Native Categories

| Abbrev | Category | Code Meaning | Priority |
| --- | --- | --- | --- |
| **S** | Style | Code standards, linting, architecture pattern | 🟢 Auto-detect |
| **M** | Mastery | Reviewer expertise, explanation depth | 🟡 Contextualizer |
| **A** | Aim | Definition of Done, acceptance criteria | 🔴 **CORE** |
| **R** | Resource | Allowed/forbidden deps, API access, compute limits | 🟡 Contextualizer |
| **T** | Time | Hotfix vs refactor, urgency level | 🟢 Accelerator |
| **P** | People | Team conventions, reviewer preferences | 🟡 Contextualizer |
| **O** | Outline | Authorized file scope, what NOT to touch | 🔴 **CORE** |
| **L** | Locale | Runtime ecosystem, language/framework version | 🟡/🔴 **CONDITIONAL** |
| **E** | Example | Reference code patterns, anti-patterns | 🟡/🟢 **CONDITIONAL** |

### Auto-Extraction Sources

| Source File | SP-Categories Extracted |
|-------------|------------------------|
| `.eslintrc` / `ruff.toml` | **S** (Style) |
| `package.json` / `pyproject.toml` | **R** (Resource), **L** (Locale) |
| `Dockerfile` / `docker-compose.yml` | **L** (Locale), **R** (Resource) |
| `AGENTS.md` / `SKILL.md` | **P** (People), **S** (Style) |
| CI/CD configs (`.github/workflows/`) | **R** (Resource), **A** (Aim quality gates) |

## Coding Task Classification

| Task Type | Primary SP-cats | Agent Behavior |
|-----------|----------------|----------------|
| Bug Fix | A, E, O | Minimal change + regression test |
| Feature | A, O, R | Plan → implement → test |
| Refactor | O, E, P | Preserve behavior, improve structure |
| Migration | L, R, T | Incremental, backward compatible |
| Infra | L, R, A | Infrastructure as Code, idempotent |

## Task Taxonomy Mapping (Generic → Coding)

Use this mapping to bridge generic SMART POLE task types in `docs/logic.md` with coding-agent task types.

| Generic Task Type (`docs/logic.md`) | Coding Task Type(s) | Default Interpretation |
|-----------|----------------|----------------|
| Deterministic | Bug Fix, Refactor | Behavior is constrained; prioritize reproducibility and regression tests |
| Generative | Feature | New capability; prioritize clear DoD and explicit scope boundaries |
| Advisory | Refactor, Migration, Infra | Architecture/process guidance; convert advice into testable acceptance criteria before coding |
| Discovery | Feature (spike), Migration (assessment) | Exploration is allowed, but execution stays minimal and reversible |
| Compliance | Infra, Migration, Bug Fix | Regulatory/security constraints are first-class acceptance criteria |

## Execution Gates (Hard Stops)

Do not execute code changes until all hard-stop gates pass:

1. **Gate A (Aim)**: At least one testable acceptance criterion exists.
2. **Gate O (Outline)**: Authorized scope is explicit (or defaults to minimal scope) and forbidden scope is respected.
3. **Gate Conflict**: All `SP-conflict` items are resolved by user decision.
4. **Gate Overlap**: Apply `One Atom, One Slot` from `docs/overlap-rules.md`; no double-counted atoms.
5. **Gate Score**: Weighted readiness score is **>= 67%** of the applicable max score (per `docs/logic.md` task-type weighting).

If any gate fails:
- Stop before `EXECUTE`
- Ask targeted clarification questions
- Re-plan only after user confirmation

## Key Differences from Chatbot Versions

| Aspect | Instructor/Enforcer | Coding Agent |
|--------|-------------------|--------------|
| Output | Master Prompt text | Working code + passing tests |
| Reasoning visibility | Prompt-analysis oriented | Concise decisions tied to files/tests (no explicit CoT requirement) |
| Verification | User reviews prompt | Agent runs tests automatically |
| Context | Conversation only | Codebase + configs + file system |
| Self-healing | N/A | Auto-fix on test failure (max 3 attempts) |

## Optional: Integration with Other Skills
This skill works best as a **pre-flight layer** in any coding agent workflow, ensuring sufficient context before execution begins. Pair with project-specific `AGENTS.md` or workflow files.
