# VN Compliance Baseline (Working Knowledge)

Purpose: practical drafting guardrails for Vietnam-focused business assistant tasks.

## 1) Health/Nutrition/Supplement Messaging
- Do not frame products as medicine or disease treatment.
- Avoid guaranteed outcomes ("chac chan khoi", "cam ket het benh").
- Use wellness/lifestyle framing unless verified approved claim text exists.
- Add channel-appropriate disclaimer when discussing health-support products.

## 2) MLM / Network Marketing Messaging
- Do not promise guaranteed income or fast wealth.
- Do not hide costs, effort, or attrition risks.
- Require balanced language: potential varies by effort, skills, market conditions.
- Include transparent assumptions when discussing results.

## 3) Evidence Discipline
- Every objective claim must map to one of:
  - approved internal claim library item
  - verified official document/source
  - downgraded non-assertive phrasing ("co the", "ho tro", "duoc thiet ke de")
- If no evidence exists, do not publish assertive claims.

## 4) Risk Scoring
Evaluate and output:
- `medical_risk`: low/medium/high
- `earnings_risk`: low/medium/high
- `platform_policy_risk`: low/medium/high
- `deception_risk`: low/medium/high

If any risk is `high`, block final persuasive copy and request rewrite constraints.

## 5) Mandatory Human Review Cases
- Any mention of serious disease, treatment, or diagnosis.
- Any explicit earnings projection, recruitment claims, or income comparisons.
- Any campaign targeting sensitive audiences.

## Notes
- This file is an operational baseline, not a legal determination.
- Keep legal references in your private compliance repository and map them to approved claim IDs.
