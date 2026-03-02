# Guardrails - Traditional Medicine Reasoning (Business-Only)

This file enforces non-medical usage of extracted traditional medicine logic.

## Hard Boundary
- Use only for mindset, behavior, troubleshooting, and decision framing.
- Never convert reasoning into medical claims.

## Block Conditions
Block and rewrite if output contains:
1. cure/treatment/prevention claim language
2. certainty language (`chac chan`, `cam ket ket qua`)
3. implied medical authority without verified context
4. fear-based manipulation
5. guaranteed income claims

## Safe Language Policy
- Use conditional and coaching language:
  - `co the`
  - `goi y`
  - `tham khao`
  - `thu nghiem theo tung buoc`
- Emphasize individual variability and context.

## Output Modes
### troubleshoot_mode
- focus: separate root causes from symptoms
- output: hypothesis list, priority test sequence, next best action

### mindset_opening_mode
- focus: reduce cognitive resistance and binary thinking
- output: reframe, perspective shift, low-risk trial action

### behavior_change_mode
- focus: small commitments and sustainable habits
- output: 3-step micro plan, friction removal, review checkpoint

## Compliance Footer (Always Available)
`Noi dung mang tinh giao duc va huong dan hanh vi, khong phai tu van y khoa hoac cam ket ket qua kinh doanh.`
