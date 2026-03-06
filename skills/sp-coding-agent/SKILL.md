---
name: sp-coding-agent
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
| **M** | Mastery | Developer expertise level — split into Domain vs Task (see below) | 🟡 Contextualizer |
| **A** | Aim | Definition of Done, acceptance criteria, success metric | 🔴 **CORE** |
| **R** | Resource | Allowed/forbidden deps, API quotas, team contacts, internal docs | 🟡 Contextualizer |
| **T** | Time | Deadline, urgency level (hotfix vs long-term), sprint constraints | 🟢 Accelerator |
| **P** | People | Team conventions, reviewer persona, implicit values & preferences | 🟡 Contextualizer |
| **O** | Outline | Authorized file scope, folder boundaries, what NOT to touch | 🔴 **CORE** |
| **L** | Locale | Runtime ecosystem, language/framework version, legal/infra constraints | 🟡/🔴 **CONDITIONAL** |
| **E** | Example | Reference code snippets, similar PRs, anti-pattern stories | 🟡/🟢 **CONDITIONAL** |

---

### Category Deep-Dives (SP-Flaw Prevention)

#### ⏱️ T — Time: Urgency Only, Not Quality

**T answers**: "How much time do I have?" — deadline, sprint slot, hotfix vs planned refactor.

> ⚠️ **T-Flaw (Category Overlap)**: Do NOT put acceptance criteria or content depth requirements inside T.
>
> - ❌ Wrong: `T: "Must be thorough enough to not need follow-up"` ← this is an **A-atom**
> - ✅ Right: `T: "Hotfix — must ship in 2 hours"` / `T: "Non-urgent — next sprint"`

Quality gates and success criteria belong in **Aim (A)** or **Outline (O)**, not Time.

---

#### 👥 P — People: Make Implicit Traits Explicit

**P answers**: "Who is involved and what are their hidden assumptions?"

Beyond team conventions, always surface:

- **Reviewer Persona**: Does the reviewer prioritize security over speed? Hate over-engineered abstractions?
- **Implicit Values**: Prefers functional style? Allergic to ORMs? Values minimal diffs?
- **Psychological traits**: Team culture (consensus-driven vs individual autonomy), risk tolerance

> ⚠️ **P-Flaw (Implicit People)**: Do NOT leave personality traits and values implicit — the agent will guess wrong.
>
> - ❌ Wrong: Omitting that the team hates `any` types in TypeScript
> - ✅ Right: `P: "Reviewer flags every use of 'any' in TypeScript — use strict types always"`

---

#### 🎓 M — Mastery: Always Split Domain vs Task

**M answers**: "What does the developer know — and in which dimension?"

Always decompose Mastery into **two parts**:

| Dimension | Meaning | Example |
|-----------|---------|---------|
| **M-Domain** | Expertise in tech stack / role | Senior React, Junior DevOps |
| **M-Task** | Experience with this specific task type | Never integrated Stripe before, First time with WebSocket |

> ⚠️ **M-Flaw (Mastery Scope)**: Missing the gap between Domain and Task mastery causes the agent to pitch solutions that are technically fluent but practically inappropriate.
>
> - ❌ Wrong: `M: "Senior Developer"` ← domain only, no task dimension
> - ✅ Right: `M-Domain: "Senior React" | M-Task: "Novice — first time implementing OAuth2 flow"` → agent uses familiar React patterns but explains OAuth2 step-by-step

---

#### 🧰 R — Resource: Tools + People + Data

**R answers**: "What weapons do I have — and what is forbidden?"

Resource includes **three dimensions**, not just software:

| Dimension | Examples |
|-----------|---------|
| **Tools** | Allowed libs/frameworks, CI/CD pipeline, dev environment |
| **People / Network** | Team members who can review, external consultants, on-call SMEs |
| **Data / Docs** | Internal wikis, API docs, log access (`/var/log/auth.log`), Sentry |

> ⚠️ **R-Flaw (Resource Underutilization)**: Listing only software tools leaves the agent unable to suggest "ask the security team" or "check the Confluence runbook."
>
> - ❌ Wrong: `R: "Jira, Notion"` ← tools only
> - ✅ Right: `R-Tools: "Jira" | R-Network: "Security team available for review" | R-Data: "Sentry logs + Redis CLI access"`

Also supply **Negative Atoms** (what is forbidden):
> `R-Forbidden: "No new npm deps without approval, no changes to DB schema"`

---

#### 📌 E — Example: The Anchor Atom

**E answers**: "What should the output look like — concretely?"

In coding context, a **Gold Standard E-atom** is a matched pair:

| E-atom Type | What it looks like |
|-------------|-------------------|
| **Code snippet** | Before/after code block showing the pattern to follow |
| **Similar PR** | Link or description of a past PR that solved a comparable bug |
| **Input/Output pair** | Expected test case: input state → expected behavior |
| **Anti-example (Story)** | "Last time we did X this way, it broke Y — avoid this pattern" |

> ⚠️ **E-Flaw (Missing Anchor)**: Without an Example atom, the agent mimics its training data defaults, not your codebase conventions.
>
> - ❌ Weak: `E: "Make it look clean"` ← too vague, gives agent no anchor
> - ✅ Gold: `E: "Follow the pattern in auth_service.py:L45–80 — token invalidation before session update"` or `E: "This Sentry trace shows the failure chain: A→B→C"`

Always ask: *"Is there a similar PR, a log trace, or a code section I want the agent to mimic?"*

---

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

Use this mapping to bridge generic SMART POLE task types in `references/logic.md` with coding-agent task types.

| Generic Task Type (`references/logic.md`) | Coding Task Type(s) | Default Interpretation |
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
4. **Gate Overlap**: Apply `One Atom, One Slot` from `references/overlap-rules.md`; no double-counted atoms.
5. **Gate Score**: Weighted readiness score is **>= 67%** of the applicable max score (per `references/logic.md` task-type weighting).

If any gate fails:

- Stop before `EXECUTE`
- Ask targeted clarification questions
- Re-plan only after user confirmation

## Worked Example: Bug Fix Context Extraction

**User request**: `"Fix the login bug — users can't login after password reset"`

| SP-cat | Atom | Why here, not elsewhere |
|--------|------|------------------------|
| **S** | `Auto-detect from .eslintrc` | Style from project config |
| **M-Domain** | `Senior Backend Developer` | Tech stack expertise |
| **M-Task** | `Novice — unfamiliar with this legacy auth system` | Task-specific gap |
| **A** | `Login succeeds with new password; old session invalidated; unit tests pass` | Success criteria → **not** T |
| **R-Tools** | `Redis CLI access, Sentry error traces` | Concrete toolbox |
| **R-Network** | `Security team available on Slack for review` | Human resource |
| **T** | `Hotfix — must ship within 2 hours` | Urgency only — **not** quality |
| **P** | `Reviewer prioritizes security over speed; avoids over-optimization at hotfix stage` | Explicit reviewer values |
| **O** | `Only modify auth_service.py and password_controller.py` | Scope boundary |
| **L** | `Python 3.11, Django 4.2, Redis 7` | Runtime ecosystem |
| **E** | `Sentry trace shows: PasswordReset→UpdateDB→[FAIL: session not invalidated]→Login` | Concrete anchor |

> 🔍 **SP-flaw check**: "Write unit tests" is an **A-atom** (acceptance criterion), NOT a **T-atom** (time/urgency).

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
