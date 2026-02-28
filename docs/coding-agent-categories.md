# Coding Agent Categories — Detailed Reference

This document provides the detailed sub-dimensions, examples, and auto-detection strategies for each of the 9 SMART POLE categories when applied to **AI Coding Agents** (OpenAI Codex, Anthropic Claude Code, Google Gemini).

---

## S - Style (Code Standards & Architecture)

| Sub-dimension | Description | Examples | Auto-detect From |
|---------------|-------------|----------|------------------|
| **Naming Convention** | Variable/function/class naming | `snake_case`, `camelCase`, `PascalCase` | Existing code patterns |
| **Architecture Pattern** | Structural approach | Clean Architecture, MVC, Hexagonal, CQRS | `src/` folder structure |
| **Paradigm** | Programming style | OOP, Functional, Reactive, Procedural | Import patterns, class usage |
| **Formatting** | Code formatting rules | Black (88 char), Prettier, gofmt | `.prettierrc`, `pyproject.toml` |
| **Import Order** | Module import conventions | stdlib → 3rd party → local | `isort` config, `.eslintrc` |
| **Comment Style** | Documentation approach | JSDoc, Google docstrings, minimal | Existing docstrings |

### Common SP-Flaws in Style
- Missing: Agent uses its default style which may clash with project conventions
- If unfilled: Mixed naming conventions, inconsistent formatting, failed lint checks

---

## M - Mastery (Technical Level & Explanation Depth)

| Sub-dimension | Description | Examples |
|---------------|-------------|----------|
| **Reviewer Level** | Expected code reviewer expertise | Junior → explain everything, Senior → terse |
| **Stack Familiarity** | User's experience with specific tech | "Knows Python, new to FastAPI" |
| **Agent Verbosity** | How much the agent explains | Verbose comments, silent code, detailed PRs |
| **Skill Gap** | Domain mastery vs task mastery | "10yr backend dev, first time with WebSockets" |

### Common SP-Flaws in Mastery
- Missing: Agent produces code that's too simple (patronizing) or too complex (intimidating)
- If unfilled: Explanation level mismatches reviewer's actual needs

---

## A - Aim (Definition of Done)

| Sub-dimension | Description | Examples |
|---------------|-------------|----------|
| **Functional Goal** | What the code should DO | "Add pagination", "Fix timeout error" |
| **Acceptance Criteria** ⚠️ | **MANDATORY** — measurable success | "All tests green", "Latency < 200ms" |
| **Backward Compatibility** | Must existing consumers still work? | "v1 API must still respond" |
| **Quality Gate** | CI/CD requirements | "Coverage > 80%", "0 new lint warnings" |
| **Issue Reference** | Link to ticket/issue | `Fixes #342`, `JIRA-1234` |

> ⚠️ **Aim is ALWAYS Core.** Never start coding without at least one testable criterion.

---

## R - Resource (Environment Constraints)

| Sub-dimension | Description | Examples | Auto-detect From |
|---------------|-------------|----------|------------------|
| **Allowed Deps** | Packages that can be added | "Use Axios for HTTP", "stdlib only" | `package.json`, `requirements.txt` |
| **Forbidden Deps** | Packages NOT to use | "No lodash", "No ORM" | `AGENTS.md`, team norms |
| **API Access** | Available external services | "Internal user-service at :8081" | `.env`, `docker-compose.yml` |
| **Compute Limits** | Memory/CPU/timeout bounds | "Lambda 256MB, 30s timeout" | `serverless.yml`, `Dockerfile` |
| **Build System** | Build/task tools available | Gradle, webpack, make, turbo | `build.gradle`, `Makefile` |

---

## T - Time (Urgency & Temporal Context)

| Sub-dimension | Description | Examples |
|---------------|-------------|----------|
| **Urgency Level** | Speed-quality tradeoff | P0 Hotfix (ship now) vs Feature (plan first) |
| **Sprint Context** | Team velocity context | "End of sprint" vs "Sprint planning" |
| **Migration Timeline** | Transition strategy | Incremental (dual-write) vs Big Bang |
| **Tech Debt Tolerance** | Accept shortcuts? | "Add TODO" vs "Solve properly" |

### Urgency Impact on Agent Behavior
| Urgency | Agent Approach |
|---------|---------------|
| **Hotfix** | Minimal change, skip refactoring, add regression test |
| **Feature** | Full planning cycle, comprehensive tests |
| **Refactor** | Behavior-preserving, extensive test validation |

---

## P - People (Stakeholder Preferences)

| Sub-dimension | Description | Examples |
|---------------|-------------|----------|
| **Code Reviewer** | Individual reviewer preferences | "Lead prefers composition over inheritance" |
| **Team Conventions** | Shared team practices | "Conventional commits", "PR must have description" |
| **End Users** | Who uses the feature | "Mobile users on slow connections" |
| **Downstream Consumers** | Services depending on this code | "Analytics pipeline reads this table" |
| **Commit Style** | Git commit message format | `feat(scope): description`, `[TYPE] #ticket description` |

---

## O - Outline (Scope & Structure Control)

| Sub-dimension | Description | Examples |
|---------------|-------------|----------|
| **Authorized Scope** | Files/dirs to modify | `src/services/user/`, `tests/unit/` |
| **Forbidden Scope** | Files/dirs NOT to touch | `src/models/`, `migrations/`, `package-lock.json` |
| **File Naming** | New file conventions | `*.service.ts`, `test_*.py`, `*.spec.js` |
| **Change Magnitude** | Size of change | "One function" vs "Entire module" |
| **Test Scope** | Types of tests required | Unit only, integration, E2E, performance |

> ⚠️ **Outline is ALWAYS Core.** If not specified, default to MINIMAL scope — change as few files as possible.

---

## L - Locale (Ecosystem & Runtime Environment)

| Sub-dimension | Description | Examples | Auto-detect From |
|---------------|-------------|----------|------------------|
| **Language Version** | Programming language version | Python 3.12, Node 20, Java 21 | `.python-version`, `.nvmrc` |
| **Framework Version** | Framework + version | Next.js 14, Spring Boot 3.2 | `package.json`, `pom.xml` |
| **Runtime Target** | Where code runs | AWS Lambda, K8s, Vercel Edge | `Dockerfile`, `serverless.yml` |
| **OS/Platform** | Operating system | Ubuntu 22.04, Alpine, macOS | `Dockerfile FROM` |
| **Repo Structure** | Monorepo vs polyrepo | Nx workspace, Turborepo, single repo | Root config files |
| **Legacy Context** | Age/state of codebase | "5 years old, no type hints" | Code analysis |

### Locale Becomes CORE When:
- Migration tasks (changing language/framework version)
- Cross-platform code (must work on multiple OSes)
- Infrastructure changes (deployment target matters)

---

## E - Example (Reference Code & Patterns)

| Sub-dimension | Description | Examples |
|---------------|-------------|----------|
| **Pattern to Follow** | Existing code to emulate | "Follow `src/services/orderService.ts` pattern" |
| **Anti-Pattern** | Code to avoid | "Don't use the singleton from `legacy/config.py`" |
| **Test Fixture** | Test setup/data patterns | "Use factories from `tests/factories/`" |
| **Similar Implementation** | Related existing feature | "Works like the search endpoint" |
| **Sample I/O** | Expected inputs/outputs | `Input: {"name": "Alice"}, Output: {"id": 1, "name": "Alice"}` |

### Example Becomes CRITICAL (Weight 1.5) When:
- Bug fix (need reproduction steps / failing test)
- Algorithm implementation (need sample input/output)
- API endpoint (need request/response examples)

---

## Usage Tips for Coding Agents

1. **Auto-detect first, ask second**: Parse project configs before asking the user for context. Most S, L, and R atoms can be inferred.

2. **CORE categories are non-negotiable**: Never write code without Aim (A) and Outline (O) being at least Adequate quality.

3. **Default to minimal scope**: When Outline is vague, change as few files as possible. It's better to under-modify than over-modify.

4. **Tests are part of Aim**: "Definition of Done" always includes test verification. If no test framework exists, suggest adding one.

5. **Reference existing patterns**: Before creating new patterns, search the codebase for similar implementations. Consistency beats novelty.

6. **Respect the Forbidden scope**: Outline's Forbidden Scope is a hard boundary. Even if the "better" fix requires touching a forbidden file, report this constraint to the user and ask for explicit permission.
