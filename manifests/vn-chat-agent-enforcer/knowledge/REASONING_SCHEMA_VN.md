# Reasoning Schema (VN) - Traditional Medicine Logic to Business Use

Use this schema for every extracted unit.

## Reasoning Atom Schema

```yaml
atom_id: string
principle_name: string
source_reference: string
source_type: ebook|article|note
core_logic: string
reasoning_pattern: root-cause|balance|cycle|stage|feedback-loop|constraint
business_use_case:
  - troubleshoot
  - mindset_opening
  - behavior_change
safe_business_translation: string
customer_objection_targets:
  - trust
  - cost
  - effort
  - time
  - fear_of_failure
recommended_prompt_fragment: string
prohibited_interpretations:
  - string
risk_flags:
  medical_claim_risk: low|medium|high
  deception_risk: low|medium|high
confidence_level: low|medium|high
review_status: draft|approved|blocked
reviewer_note: string
```

## Mapping Rules
1. Translate abstract logic into neutral coaching/business language.
2. Keep wording conditional (`co the`, `thu nghiem`, `tung buoc`).
3. Avoid all treatment/cure implications.
4. Include at least one prohibited interpretation per atom.

## Example Atom

```yaml
atom_id: TM-R-001
principle_name: Root before symptom
source_reference: ebook_x_chapter_3
source_type: ebook
core_logic: Surface instability usually reflects deeper structural imbalance.
reasoning_pattern: root-cause
business_use_case:
  - troubleshoot
  - mindset_opening
safe_business_translation: Solve process bottlenecks first, then optimize messaging.
customer_objection_targets:
  - effort
  - fear_of_failure
recommended_prompt_fragment: Help me separate root blockers from surface objections before writing sales copy.
prohibited_interpretations:
  - Do not map this to disease diagnosis or treatment direction.
risk_flags:
  medical_claim_risk: low
  deception_risk: low
confidence_level: medium
review_status: approved
reviewer_note: Safe for coaching and troubleshooting framing.
```
