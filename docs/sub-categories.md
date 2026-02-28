# SP Sub-categories Reference / Tham Khảo Chi Tiết SP Sub-categories

**Bi-lingual Documentation (English / Tiếng Việt)**

This document provides detailed sub-dimensions for each of the 9 SMART POLE categories.

*Tài liệu này cung cấp các chiều con chi tiết cho mỗi trong 9 danh mục SMART POLE.*

---

## Quick Reference Table / Bảng Tham Khảo Nhanh

| Category | Sub-dimensions | Examples |
|----------|----------------|----------|
| **S (Style)** | Format, Tone, Persona, Persuasive Strategy, Verbosity | Markdown/JSON, Humorous/Formal, Doctor/Hacker |
| **M (Mastery)** | User Mastery, Target Mastery, Skill Context | Novice→Expert, ELI5/PhD, "Giỏi Toán nhưng mù IT" |
| **A (Aim)** | Primary Goal, Evaluation Criteria, Desired Outcome | Problem-solving, "Dưới 200 chữ", Action plan |
| **R (Resource)** | Financial, Tools/Equipment, Materials, Constraints | "2 triệu đồng", "Chỉ có điện thoại" |
| **T (Time)** | Deadlines, Duration, Temporal Context, Urgency | "5 phút nữa", "Mùa hè", "Cấp cứu y tế" |
| **P (People)** | Demographics, Psychographics, Values, Ideology | Tuổi/Nghề, Sở thích/Nỗi sợ, An toàn/Tự do |
| **O (Outline)** | Scope, Structure, Technical Specs, Focus Areas | "Bỏ qua backend", "Python 3.10" |
| **L (Locale)** | Geography, Industry, Legal, Cultural | Vietnam/EU, Banking, GDPR, Á Đông |
| **E (Example)** | Output Snippet, Analogy, Case Study, Narrative | "Viết theo đoạn này", "Như nước chảy trong ống" |

---

## Detailed Breakdown / Chi Tiết Từng Category

### S - Style (Phong Cách)

| Sub-dimension | Description | Examples |
|---------------|-------------|----------|
| **Format** | Output structure | Markdown, JSON, Table, Bullet points |
| **Tone** | Voice and mood | Humorous, Formal, Casual, Professional |
| **Persona** | Character AI plays | Doctor, Hacker, Noir Detective, Professor |
| **Persuasive Strategy** | Influence approach | Cialdini's 6 principles, AIDA model |
| **Verbosity** | Detail level | Concise (1 paragraph), Step-by-step (detailed) |

---

### M - Mastery (Trình Độ)

| Sub-dimension | Description | Examples |
|---------------|-------------|----------|
| **User Mastery** | Your own skill level | Novice, Intermediate, Expert |
| **Target Mastery** | Intended audience level | ELI5, PhD, Senior Developer |
| **Skill Context** | Specific strengths/gaps | "Giỏi Toán nhưng mù về lập trình" |
| **Skill Gap Detection** | Gap between domain and task expertise | "Senior Civil Engineer (domain) but zero Python experience (task)" |

> [!TIP]
> Always probe the **GAP** between domain mastery and task mastery. A "10-year Civil Engineer" learning Python needs engineering analogies for coding concepts — a totally different approach than teaching a CS student.

---

### A - Aim (Mục Tiêu)

| Sub-dimension | Description | Examples |
|---------------|-------------|----------|
| **Primary Goal** | What you want to achieve | Problem-solving, Brainstorming, Research |
| **Evaluation Criteria** ⚠️ | How to judge success (**MANDATORY**) | "Dưới 200 chữ", "Tiết kiệm điện nhất" |
| **Desired Outcome** | Expected deliverable | Action plan, Code, Menu, Report |

> [!WARNING]
> **Evaluation Criteria is not optional.** The original SMART POLE bot rejects broad goals like "build a checklist" without criteria. Always include HOW SUCCESS IS MEASURED (e.g., "checklist that passes internal audit review" is Aim; "checklist with 3 sections" is Outline).

---

### R - Resource (Nguồn Lực)

| Sub-dimension | Description | Examples |
|---------------|-------------|----------|
| **Financial** | Budget constraints | "2 triệu đồng", "Ngân sách vô hạn" |
| **Tools/Equipment** | Available tools | "Chỉ có điện thoại", "Có laptop + AI" |
| **Materials** | Data or ingredients | "Chỉ có trứng và cà chua" |
| **Constraints** | Limitations | "Không dùng thư viện bên thứ 3" |

---

### T - Time (Thời Gian)

| Sub-dimension | Description | Examples |
|---------------|-------------|----------|
| **Deadlines** | Due dates | "5 phút nữa", "Cuối tuần này" |
| **Duration** | Time investment | "10 phút/ngày", "Bài tập 30 giây" |
| **Temporal Context** | Season/Era | "Mùa hè", "Thời kỳ suy thoái" |
| **Urgency** | Priority level | "Cấp cứu y tế", "Không gấp" |

---

### P - People (Con Người)

| Sub-dimension | Description | Examples |
|---------------|-------------|----------|
| **Demographics** | Basic attributes | Tuổi, Giới tính, Nghề nghiệp |
| **Psychographics** | Personality traits | Sở thích, Nỗi sợ, Khao khát |
| **Values** | Core priorities | An toàn, Tự do, Thành tựu, Tiết kiệm |
| **Ideology/Beliefs** | World views | Quan điểm chính trị, Tôn giáo, Triết lý |

---

### O - Outline (Khung Sườn)

| Sub-dimension | Description | Examples |
|---------------|-------------|----------|
| **Scope** | What to include/exclude | "Chỉ phần cứng, bỏ qua phần mềm" |
| **Structure** | Organization | "3 chương: Mở - Thân - Kết" |
| **Technical Specs** | Requirements | "Python 3.10", "Kích thước 10x20cm" |
| **Focus Areas** | Emphasis | "Nhấn mạnh bảo mật hơn tốc độ" |
| **Standards Compliance Format** | Professional standard formatting | "ISO/IEC 27001 audit layout", "GDPR report template" |

> [!IMPORTANT]
> When a user mentions professional standards (ISO, GDPR, PCI-DSS), clarify: is this a **content** requirement (→ Locale L3) or a **format** requirement (→ Outline)? See [Overlap Rules - Rule 5](overlap-rules.md#rule-5-professional-standards-disambiguation).

---

### L - Locale (Bối Cảnh)

| Sub-dimension | Description | Examples |
|---------------|-------------|----------|
| **Geography** | Location/Region | Vietnam, EU, Singapore, Tokyo |
| **Industry** | Business domain | Banking, Healthcare, E-commerce, Fintech |
| **Legal** | Regulatory framework | GDPR, PCI-DSS, Luật ATTT |
| **Cultural** | Social norms | Á Đông (trọng lễ nghĩa), Phương Tây (thẳng thắn) |

**Priority by Industry:**
| Industry | Priority Order |
|----------|----------------|
| Banking/Finance | Legal > Industry > Geography > Cultural |
| Healthcare | Legal > Industry > Cultural > Geography |
| E-commerce | Cultural > Geography > Industry > Legal |

---

### E - Example (Ví Dụ Mẫu)

| Sub-dimension | Description | Examples |
|---------------|-------------|----------|
| **Output Snippet** | Text to mimic | "Hãy viết theo phong cách đoạn văn này: [...]" |
| **Analogy/Metaphor** | Comparison | "Giải thích như Internet là hệ thống ống nước" |
| **Case Study** | Scenario reference | "Giống như case của công ty X khi đối mặt với..." |
| **Narrative** | Story context | "Hãy kể theo góc nhìn nhân viên mới" |

---

## Usage Tips / Mẹo Sử Dụng

1. **Not all sub-dimensions are required** - Focus on the most relevant ones for your task.
   
   *Không phải tất cả sub-dimensions đều bắt buộc - Tập trung vào những cái liên quan nhất.*

2. **Core categories (A, O) should always be addressed** - Without Aim and Outline, AI responses will be directionless.
   
   *Categories cốt lõi (A, O) nên luôn được cung cấp - Thiếu Aim và Outline, AI sẽ trả lời không có định hướng.*

3. **Use sub-dimensions as a checklist** when you get unsatisfying AI responses - often a missing sub-dimension is the culprit.
   
   *Sử dụng sub-dimensions như một checklist khi bạn nhận được câu trả lời không hài lòng.*

4. **Watch for conflicts** - If two sub-dimensions contradict each other (e.g., Style "Shakespearean" + Outline "ISO format"), resolve before proceeding. See [Overlap Rules - Rule 4](overlap-rules.md#rule-4-atom-conflict-detection).

   *Chú ý xung đột - Nếu hai sub-dimensions mâu thuẫn, giải quyết trước khi tiếp tục.*

5. **Probe Mastery gaps** - When a user states expertise, always check if it applies to the specific task or just their general domain.

   *Thăm dò khoảng cách Mastery - Khi người dùng nêu chuyên môn, luôn kiểm tra liệu nó áp dụng cho nhiệm vụ cụ thể hay chỉ lĩnh vực chung.*
