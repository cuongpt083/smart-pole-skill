# Gemini Gem Update Guide / Hướng Dẫn Cập Nhật Gemini Gem

**Bi-lingual Documentation (English / Tiếng Việt)**

This guide explains how to update your Gemini Gem with the latest SMART POLE framework changes.

---

## 📋 Summary of Changes / Tóm Tắt Thay Đổi

### Version 3.0 Updates:

1. **Task-Type Classification** - Dynamic Locale requirement
2. **Conditional Core Locale** - Locale becomes Core for consulting tasks  
3. **Weighted Scoring** - Dynamic max score (9.5/10.5/11.0)
4. **Overlap Handling** - Functional Gravity + One Atom One Slot
5. **Domain Detection** - Automatic domain question for advisory tasks

---

## 🔧 Steps to Update Gemini Gem

### Step 1: Access Gemini Gem Settings

1. Go to [Gemini](https://gemini.google.com)
2. Click on your Gem or create a new one
3. Navigate to **Custom Instructions** or **System Prompt**

### Step 2: Copy the New System Prompt

Copy the **entire content** of one of these files:

| Mode | File | Best For |
|------|------|----------|
| Instructor | `prompts/system_prompt.md` | Learning, iterating |
| Chat Enforcer | `prompts/system_prompt_enforcer.md` | Chat-agent workflows, automation |

### Step 3: Key Sections to Include

Make sure these sections are present:

#### A. Task-Type Classification
```
| Task Type | Keywords | Locale Requirement |
|-----------|----------|-------------------|
| Deterministic | solve, calculate | Optional (0.5) |
| Generative | write, create | Contextualizer (1.5) |
| Advisory | advise, recommend | 🔴 CORE (2.0) |
| Discovery | brainstorm, explore | 🔴 CORE (2.0) |
| Compliance | legal, policy | 🔴 CORE (2.0) |
```

#### B. Domain Question Template
```
📍 DOMAIN REQUIRED: This request involves [type]. Please specify:
1. Industry/Domain: What field? (Banking, Healthcare, E-commerce)
2. Region (if relevant): Which geographic region?
3. Regulatory context (if any): Any specific regulations?
```

#### C. Weighted Scoring
```
Max Score:
- Deterministic: 9.5 (Locale = 0.5)
- Generative: 10.5 (Locale = 1.5)
- Advisory/Discovery/Compliance: 11.0 (Locale = 2.0)

Threshold: ≥ 67% + All Core categories confirmed
```

---

## ✅ Verification Checklist

After updating your Gem, test with these prompts:

### Test 1: Deterministic Task (No domain question expected)
```
"Calculate the sum of 1 to 100"
```
✅ Should NOT ask for domain

### Test 2: Advisory Task (Domain question expected)
```
"Recommend a marketing strategy for my business"
```
✅ Should ask:
- What industry?
- Which region?
- Any regulations?

### Test 3: Discovery Task (Domain question expected)
```
"Brainstorm ideas for improving customer retention"
```
✅ Should ask for Industry/Domain first

---

## 🚨 Common Issues

### Issue 1: Gem doesn't ask for domain
**Solution**: Ensure Task-Type Classification section is included

### Issue 2: Locale not treated as Core
**Solution**: Ensure Locale Conditional Core Rule is present

### Issue 3: Wrong max score
**Solution**: Update to dynamic max score (9.5/10.5/11.0)

---

## 📁 Files to Reference

| File | Purpose |
|------|---------|
| `prompts/system_prompt_enforcer.md` | Full Chat Enforcer mode prompt |
| `docs/logic.md` | Framework logic explanation |
| `docs/sub-categories.md` | All sub-dimensions for 9 categories |
| `docs/overlap-rules.md` | Overlap handling rules |

---

## 🔄 Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | Initial | Basic 9 categories |
| 2.0 | - | Weighted scoring, Security guardrails |
| 3.0 | 2026-01-30 | Task-Type Classification, Conditional Core Locale, Overlap handling |
