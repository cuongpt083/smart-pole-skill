# Prompt Gatekeeper Implementation Plan

## 1. Goals
- Turn `smart-pole-instructor` into a reliable gatekeeper signal for every prompt before it reaches an AI provider.
- Keep Smart-Pole coaching behavior backward-compatible while adding structured enforcement metadata.
- Provide orchestration hooks so application services can block/route prompts based on Smart-Pole verdicts.

## 2. Current Capability Snapshot
- Inputs: raw prompt text, optional notes; outputs: SP-flaws, SP-atoms, suggested Master Prompt.
- Missing items for enforcement: prompt identity, policy awareness, pass/fail indicators, structured JSON for automation.
- No centralized middleware to require skill execution; user can bypass the skill entirely.

## 3. Functional Requirements
1. **Policy Awareness**: Skill accepts `policyProfile` describing which SMART POLE categories are mandatory per use-case.
2. **Gate Verdict**: Skill responds with `gateStatus` (`pass`, `needs_context`, `block`) plus per-category completeness flags.
3. **Autofill Support**: Provide recommended atoms for each missing category to let UI or auto-agents patch prompts quickly.
4. **Traceability**: Include `promptId`, `initiator`, `timestamp`, `skillVersion` for audit and replay.
5. **Orchestration Hook**: The calling service must treat non-`pass` responses as blocking and surface missing context to the user or automation pipeline.

## 4. Architecture & Workflow
1. **Client / UX layer**: captures initial prompt; calls Gatekeeper API; if `needs_context`, shows inline checklist; if `block`, escalates or cancels.
2. **Gatekeeper API** (wrapper around smart-pole-instructor): enriches requests with metadata, forwards to skill, normalizes response schema.
3. **Policy Store**: simple config file or DB table mapping scenario → required categories + severity; loaded by Gatekeeper at runtime.
4. **Prompt Orchestrator**: consumes Gatekeeper verdicts, logs to telemetry (success, failure, override), only forwards prompts marked `pass` to model router.
5. **LLM Router**: unchanged except that inputs now always carry `masterPrompt` + context tags from Gatekeeper.

Sequence:
```
User Prompt → Gatekeeper API → smart-pole-instructor (policy, metadata)
  ↳ returns gateStatus, checklist, masterPrompt suggestions
Gatekeeper API → respond to client (pass or request fixes)
Once pass → Prompt Orchestrator → AI Provider
```

## 5. Delivery Plan
### Phase 1 – Discovery (Days 1-2)
- Audit current skill interface & outputs; document gaps vs requirements.
- Align stakeholders on enforcement policies per use-case (internal tools, customer-facing, experiments).
- Define JSON schema for `PromptGatekeeperResult` (metadata + verdict + checklist + suggestions).

### Phase 2 – Skill Enhancements (Days 3-6)
- Extend skill input contract: add policy profile, prompt metadata, preferred language, quick-evaluate flag.
- Implement completeness scoring: each SMART POLE category returns `{status, notes}`.
- Compute `gateStatus` rules (e.g., fail if any required category missing; block if security policy triggered).
- Add regression tests to ensure legacy coaching responses still render when policy not provided.

### Phase 3 – Gatekeeper API (Days 6-9)
- Build lightweight service or module that enforces "Smart-Pole before provider" invariant.
- Integrate policy store (YAML/DB) and caching; inject metadata (promptId, userId, channel).
- Provide REST/SDK interface for downstream consumers (web app, CLI, workflows).

### Phase 4 – Orchestrator Integration (Days 9-13)
- Insert Gatekeeper call into prompt pipeline; block provider invocation until `pass` received.
- Implement remediation UX: show missing categories, allow user edits, track attempts.
- Log telemetry (latency, block counts, overrides) for monitoring.

### Phase 5 – Validation & Rollout (Days 13-17)
- Unit + contract tests for new skill interface and API.
- Staging pilot with representative prompts; target added latency <300 ms.
- Address findings, finalize documentation, enable enforcement in production with gradual rollout switches.

## 6. Risks & Mitigations
- **Latency inflation**: cache policy profiles; keep skill lightweight; precompute hints when possible.
- **User friction**: provide autofill suggestions and save partially completed prompts.
- **Inconsistent policies**: maintain centralized policy definitions and automate linting/validation of config changes.

## 7. Next Actions
1. Draft `PromptGatekeeperResult` schema and review with platform team.
2. Prototype policy-aware smart-pole request/response locally.
3. Socialize orchestration changes with application owners to schedule integration windows.
