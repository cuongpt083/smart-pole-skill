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
4. **DETECT FLAWS**: Identify missing context; ask user if critical
5. **PLAN**: Create implementation plan with file-level scope
6. **EXECUTE**: Code changes with interleaved thinking
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

## Key Differences from Chatbot Versions

| Aspect | Instructor/Enforcer | Coding Agent |
|--------|-------------------|--------------|
| Output | Master Prompt text | Working code + passing tests |
| CoT | Single thinking block | Interleaved thinking between tool calls |
| Verification | User reviews prompt | Agent runs tests automatically |
| Context | Conversation only | Codebase + configs + file system |
| Self-healing | N/A | Auto-fix on test failure (max 3 attempts) |

## Optional: Integration with Other Skills
This skill works best as **Step 0** in any coding agent workflow, ensuring sufficient context before execution begins. Pair with project-specific `AGENTS.md` or workflow files.
