# User Guide - Build Custom GPTs and Gemini Gems with VN Chat Enforcer

This guide shows how to use the manifest package for business helpers in Vietnam:
- sales helper
- traditional marketing helper
- online marketing helper
- MLM/network marketing helper
- TikTok/Facebook/YouTube content helper
- health/nutrition/supplement coaching helper

## 1) What to Load
Use these files from this package:
- `skill/SKILL.md` (main behavior and hard-stop gates)
- `knowledge/VN_COMPLIANCE_BASELINE.md`
- `knowledge/CLAIM_TAXONOMY_VN.md`
- `knowledge/CHANNEL_TEMPLATES_VN.md`
- `docs/OPERATING_GUIDE.md` (for your internal QA flow)

## 2) Build a Custom GPT (ChatGPT)
1. Open GPT builder in ChatGPT.
2. Set the system instruction using the body of `skill/SKILL.md`.
3. Add knowledge files:
- `VN_COMPLIANCE_BASELINE.md`
- `CLAIM_TAXONOMY_VN.md`
- `CHANNEL_TEMPLATES_VN.md`
4. Add clear description:
- "VN compliance-first business assistant for marketing/sales content. Not medical/legal advice."
5. Add starter prompts, for example:
- "Create a TikTok script for nutrition coaching in Vietnam with compliant wording."
- "Rewrite this MLM recruitment post to remove risky claims."
- "Generate Facebook content for supplement education with proper disclosure."

## 3) Build a Gemini Gem
1. Open Gemini Gem creation/edit page.
2. Paste `skill/SKILL.md` into Gem instructions.
3. Attach the 3 knowledge files as references.
4. Save Gem metadata to reflect scope:
- VN business assistant
- compliance-aware drafting
- no coding-agent execution
5. Add test prompts (same as above) before production use.

## 4) Recommended Agent Configuration
- Language: Vietnamese-first, English optional.
- Tone: practical, conservative, no overpromising.
- Output style: short actionable sections.
- Always include:
1. risk level
2. claim class (safe/restricted/blocked)
3. disclosure snippet
4. safe rewrite option if blocked

## 5) Daily Operator Workflow
1. User gives campaign request.
2. Agent classifies task + risk.
3. Agent asks missing SMART POLE atoms.
4. Agent applies VN compliance and claim classifier.
5. If blocked claims found: refuse and rewrite safely.
6. If all gates pass: produce draft + `<master_prompt>`.
7. Human reviewer approves before publishing.

## 6) Prompt Pattern for Best Results
Ask users to provide:
- business type and target audience
- product category (especially health/supplement)
- channel (TikTok/Facebook/YouTube)
- goal (lead gen, conversion, education, retention)
- forbidden terms/claims
- evidence source or approved claim list (if available)

Example intake prompt:
`Hay tao noi dung cho [kenh] trong linh vuc [linh vuc], doi tuong [doi tuong], muc tieu [muc tieu], tranh cac cum tu [cam], uu tien thong diep [uu tien].`

## 7) Red-Flag Inputs (Should Trigger Block or Escalation)
- disease cure/treatment claims
- guaranteed weight-loss timelines
- guaranteed income claims for MLM/network marketing
- fake urgency/scarcity ("only today guaranteed result")
- vulnerable audience exploitation

## 8) Minimum QA Before Publish
Check every output:
1. No blocked claims
2. Correct disclosure exists
3. No guaranteed outcomes
4. Tone is ethical and non-deceptive
5. Human approval recorded

## 9) Versioning and Change Control
- Keep manifest versions in your private repo.
- Track policy updates in commit messages:
- `policy: ...`
- `risk: ...`
- `template: ...`
- Re-test with your red-team prompt set after each update.

## 10) Important Boundary
This assistant is drafting support only.
- Not legal advice
- Not medical diagnosis/treatment advice
- Final publishing should be approved by your internal compliance owner
