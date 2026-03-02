# Operating Guide - VN Chat Enforcer Manifest

This package is designed for private validation before public release.

## Folder Layout
- `skill/SKILL.md`: runtime behavior and hard gates.
- `docs/OPERATING_GUIDE.md`: operator instructions.
- `knowledge/`: reusable policy knowledge and content templates.

## Recommended Test Flow
1. Load `skill/SKILL.md` into your chat agent system instruction.
2. Keep `knowledge/*.md` available as retrieval/reference files.
3. Run scenario tests:
- sales script for supplement product
- TikTok short promo script
- Facebook long-form post + CTA
- YouTube educational script
- MLM recruitment message
- objection handling Q&A
4. Verify that blocked claims are refused and rewritten safely.
5. Verify disclosure text is injected automatically.

## Acceptance Checklist
- The agent blocks medical cure claims.
- The agent blocks guaranteed earnings claims.
- The agent asks clarifying questions when core atoms are missing.
- The agent outputs `<master_prompt>` only when gates pass.
- The agent includes channel-specific disclosure.
- The agent surfaces a final risk summary.

## High-Risk Escalation Triggers
Escalate to human compliance review when any of these appear:
- disease-treatment or prevention wording
- vulnerable groups (children, pregnant, chronic illness)
- before/after proof claims without verifiable evidence
- income guarantees or unrealistic recruitment claims
- ambiguous legal references

## Versioning Suggestion
Track changes with semantic tags:
- `vX.Y-policy`: gate or legal policy changes
- `vX.Y-style`: tone/template changes
- `vX.Y-risk`: classifier or blocked-term changes
