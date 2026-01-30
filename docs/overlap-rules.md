# Overlap Handling Rules / Quy Tắc Xử Lý Chồng Lấn

**Bi-lingual Documentation (English / Tiếng Việt)**

This document provides rules for handling information that could fit multiple SP categories.

*Tài liệu này cung cấp các quy tắc để xử lý thông tin có thể thuộc nhiều danh mục SP.*

---

## The Problem / Vấn Đề

When users provide context, some information can seem to fit multiple categories:
- "I'm an experienced engineer" - Is this **Mastery** or **People**?
- "I'm on a deserted island" - Is this **Locale** or **Resource**?

*Khi người dùng cung cấp ngữ cảnh, một số thông tin có thể thuộc nhiều category.*

---

## Rule 1: Functional Gravity Principle / Nguyên Tắc Trọng Lực Chức Năng

> **Classify information based on its PRIMARY INTENT, not its surface appearance.**
>
> *Phân loại thông tin dựa trên Ý ĐỒ CHÍNH, không phải vẻ bề ngoài.*

### Examples / Ví Dụ:

| Information | Context A → Category | Context B → Category |
|-------------|---------------------|---------------------|
| "Professional tone" | About writing style → **Style (S)** | About ISO standards → **Outline (O)** |
| "Banking industry" | Domain expertise → **Locale (L)** | Required certifications → **Resource (R)** |
| "5 years experience" | Skill level → **Mastery (M)** | Personal identity → **People (P)** |

---

## Rule 2: One Atom, One Slot / Một Atom, Một Ô

> **Each SP-atom counts for ONE category only. Never double-count.**
>
> *Mỗi SP-atom chỉ được tính điểm cho MỘT category. Không bao giờ đếm trùng.*

### Why This Matters / Tại Sao Quan Trọng:

Double-counting inflates the Readiness Score artificially, leading to:
- Premature Master Prompt generation
- False confidence in incomplete prompts
- Lower quality AI responses

*Đếm trùng sẽ thổi phồng điểm Readiness Score, dẫn đến prompt chưa đủ tốt.*

### Example Analysis / Ví Dụ Phân Tích:

**User input**: "Tôi là người mẹ đơn thân đang lo lắng, muốn tìm lộ trình học tiếng Anh không tốn kém"

| Atom | Category | Reasoning |
|------|----------|-----------|
| "người mẹ đơn thân" | **People (P)** - Demographics | Personal identity attribute |
| "lo lắng" | **People (P)** - Psychographics | Emotional state |
| "không tốn kém" | **Resource (R)** - Financial | Budget constraint |
| "lộ trình học tiếng Anh" | **Aim (A)** - Primary Goal | What user wants to achieve |

**Correct score**: P=2 atoms, R=1 atom, A=1 atom ✓

**Wrong (double-counting)**: Counting "người mẹ đơn thân" for both People AND Mastery ✗

---

## Rule 3: Common Confusing Pairs / Các Cặp Hay Nhầm Lẫn

### 1. People (P) vs Mastery (M)

| Information | Correct Category | Why |
|-------------|------------------|-----|
| "Tôi là kỹ sư 10 năm kinh nghiệm" | **Mastery (M)** | Measurable skill level |
| "Tôi là người thích sự rõ ràng" | **People (P)** | Personality trait, not skill |
| "PhD in Physics" | **Mastery (M)** | Educational achievement |
| "Tôi ghét sự mơ hồ" | **People (P)** | Personal preference/value |

**Rule of Thumb**: If it's *measurable* → Mastery. If it's *inherent trait* → People.

*Nếu có thể đo lường được → Mastery. Nếu là đặc điểm bẩm sinh → People.*

---

### 2. Locale (L) vs Resource (R)

| Information | Correct Category | Why |
|-------------|------------------|-----|
| "Tôi đang ở hòn đảo hoang" | **Locale (L)** | Geographic location |
| "Không có điện, không có nước" | **Resource (R)** | Consequence/constraint |
| "Văn phòng tại Việt Nam" | **Locale (L)** | Location identifier |
| "Không có ngân sách marketing" | **Resource (R)** | Financial constraint |

**Rule of Thumb**: Location itself → Locale. Consequences of location → Resource.

*Vị trí → Locale. Hệ quả của vị trí → Resource.*

---

### 3. Style (S) vs Example (E)

| Information | Correct Category | Why |
|-------------|------------------|-----|
| "Viết như Shakespeare" | **Style (S)** | Persona name (general) |
| "Viết theo đoạn văn này: '[actual text]'" | **Example (E)** | Actual snippet to mimic |
| "Giọng hài hước, nhẹ nhàng" | **Style (S)** | Tone description |
| "Dùng cấu trúc JSON như: {key: value}" | **Example (E)** | Structural template |

**Rule of Thumb**: Name/description → Style. Actual text/template → Example.

*Tên/mô tả → Style. Văn bản/mẫu thực tế → Example.*

---

### 4. Outline (O) vs Aim (A)

| Information | Correct Category | Why |
|-------------|------------------|-----|
| "Tôi muốn 3 chương" | **Outline (O)** | Structure specification |
| "Tôi muốn thuyết phục sếp" | **Aim (A)** | Ultimate goal |
| "Độ dài dưới 500 từ" | **Outline (O)** | Scope constraint |
| "Mục tiêu là tiết kiệm 30% chi phí" | **Aim (A)** | Success criteria |

**Rule of Thumb**: "What to include/structure" → Outline. "Why and how to judge success" → Aim.

*"Bao gồm gì/cấu trúc" → Outline. "Tại sao và đánh giá thành công" → Aim.*

---

## Gray Zones / Vùng Xám

These are especially tricky cases. When in doubt, **ask for clarification**:

| Ambiguous Info | Could Be... | Ask This |
|----------------|-------------|----------|
| "Professional" | Style or Outline? | "Do you mean formal writing style, or industry-standard compliance?" |
| "Industry expertise" | Locale or Mastery? | "Are you referring to the domain context or your skill level?" |
| "5 minutes" | Time or Resource? | "Is this a deadline or an available time budget?" |

---

## Implementation Checklist / Checklist Triển Khai

When analyzing a user prompt:

1. ☐ Break down into smallest "atoms"
2. ☐ For each atom, identify PRIMARY intent
3. ☐ Assign to ONE category only
4. ☐ Do NOT double-count
5. ☐ If ambiguous, apply Functional Gravity
6. ☐ If still unclear, ask user for clarification

---

## Examples in Practice / Ví Dụ Thực Tế

### Example 1: Job Application Email

**User**: "Help me write an email to apply for a senior developer position at a fintech startup in Singapore. I have 8 years experience and I value work-life balance."

| Atom | Category |
|------|----------|
| "email" | Outline (O) - Format |
| "apply for senior developer position" | Aim (A) - Primary Goal |
| "fintech startup" | Locale (L) - Industry |
| "Singapore" | Locale (L) - Geography |
| "8 years experience" | Mastery (M) - User level |
| "work-life balance" | People (P) - Values |

**Score**: A=1, O=1, L=2, M=1, P=1 → Total: 6 atoms, 5 categories addressed.

---

### Example 2: Recipe Request

**User**: "Tôi cần công thức nấu phở cho gia đình 4 người. Tôi lo lắng vì chưa bao giờ nấu món này. Ngân sách 100k, chỉ có nồi thường."

| Atom | Category |
|------|----------|
| "công thức nấu phở" | Aim (A) - Primary Goal |
| "gia đình 4 người" | Outline (O) - Scope |
| "lo lắng" | People (P) - Psychographics |
| "chưa bao giờ nấu món này" | Mastery (M) - User level |
| "Ngân sách 100k" | Resource (R) - Financial |
| "chỉ có nồi thường" | Resource (R) - Tools |

**Score**: A=1, O=1, P=1, M=1, R=2 → Total: 6 atoms, 5 categories addressed.
