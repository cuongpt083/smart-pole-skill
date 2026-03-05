# SMART POLE Skill: The Ultimate Context Engine
**Bi-lingual Documentation (English / Tiếng Việt)**

From generic "average" answers to "surgical precision" results.
*Từ những câu trả lời "trung bình" lột xác thành kết quả "chính xác tuyệt đối".*

---

## 🌟 Introduction / Giới Thiệu
**English**:
The **SMART POLE** framework is a systematic approach to Prompt Engineering designed to eliminate "Hallucinations" and "Generic Blob" responses. By breaking down a request into 9 distinct atoms of context, it forces Large Language Models (LLMs) to lock into a specific probability path, ensuring the output matches exactly what you envisioned.

**Tiếng Việt**:
Framework **SMART POLE** là phương pháp tiếp cận có hệ thống đối với Prompt Engineering, được thiết kế để loại bỏ hiện tượng "ảo giác" (hallucinations) và các câu trả lời chung chung vô hồn. Bằng cách chia nhỏ yêu cầu của bạn thành 9 "nguyên tử" (atoms) ngữ cảnh riêng biệt, nó buộc các mô hình ngôn ngữ lớn (LLM) phải đi theo đúng hướng, đảm bảo kết quả đầu ra khớp hoàn toàn với mong muốn của bạn.

---

## 🧩 The 9 Categories / 9 Yếu Tố Cốt Lõi
To master this framework, you need to understand the acronym **SMART POLE**:
*Để làm chủ framework này, bạn cần hiểu rõ 9 chữ cái trong **SMART POLE**:*

| Letter | Category | Meaning (Ý nghĩa) | Example Atom (Ví dụ) |
| :---: | :--- | :--- | :--- |
| **S** | **Style** | The Persona/Mask of the AI. <br> *Lớp vỏ/Persona của AI.* | "Witty Instructor", "Concise JSON" |
| **M** | **Mastery** | The **User's** level of understanding. <br> *Trình độ hiểu biết của **Người dùng**.* | "Explain like I'm 5", "Senior Architect" |
| **A** | **Aim** | The Goal & Scorecard. <br> *Mục tiêu & Tiêu chí đánh giá.* | "Debug usage memory" + "Explain root cause" |
| **R** | **Resource** | Tools, Budget, Data. <br> *Công cụ, Ngân sách, Dữ liệu.* | "Use PostgreSQL", "Budget $0" |
| **T** | **Time** | Deadlines, Duration. <br> *Hạn chót, Thời lượng.* | "Deadline: Friday", "read in 2 mins" |
| **P** | **People** | Values, Audience, Beliefs. <br> *Giá trị, Khán giả, Niềm tin* | "Value efficiency over cost", "Audience: Moms" |
| **O** | **Outline** | Structure & Scope. <br> *Cấu trúc & Phạm vi.* | "3 Sections", "Ignore backend code" |
| **L** | **Locale** | Domain, Industry, Context. <br> *Lĩnh vực, Ngành nghề, Ngữ cảnh.* | "SaaS Industry", "GDPR Compliant" |
| **E** | **Example** | Snippets to emulate. <br> *Đoạn mẫu (Snippet).* | "Use this JSON schema: {...}" |

---

## 🛠️ The Origin / Nguồn Gốc Xây Dựng
**English**:
This Skill was created through a rigourus **Reverse Engineering** process of the famous `SMART_POLE_helper` bot on Poe.
- **Methodology**: Black-box analysis, Chain of Thought (CoT) extraction, and A/B benchmarking.
- **Accuracy**: >95% replication of the original bot's logic, including its internal "Think-Tag-Analyze" loop.
- **Optimization**: We enhanced the framework by strictly separating "Mastery" (User level) from "Style" (AI Persona), a nuance often overlooked.

**Tiếng Việt**:
Skill này được xây dựng thông qua quy trình **Reverse Engineering** (Dịch ngược) nghiêm ngặt từ con bot nổi tiếng `SMART_POLE_helper` trên Poe.
- **Phương pháp**: Phân tích hộp đen, trích xuất chuỗi suy luận (Chain of Thought), và benchmark A/B.
- **Độ chính xác**: Tái tạo >95% logic của bot gốc, bao gồm cả vòng lặp "Suy nghĩ - Gắn thẻ - Phân tích" bên trong.
- **Tối ưu hóa**: Chúng tôi đã nâng cấp framework bằng cách tách biệt rõ ràng giữa "Mastery" (Trình độ người dùng) và "Style" (Persona của AI), một chi tiết tinh tế thường bị bỏ qua.

---

## ⚡ Quick Start / Bắt Đầu Nhanh
**English**:
1. **Pick a mode**:
   - **Instructor** (learn + iterate): `skills/smart-pole-instructor/`.
   - **Chat Enforcer** (custom chat-agent workflow): `skills/smart-pole-chat-enforcer/`.
   - **Coding Agent** (code tasks): `skills/smart-pole-coding-agent/`.
2. **Load the prompt** into your tool's system/custom instructions.
3. **Start with a vague request** and let SMART POLE ask for missing atoms.
4. **Platform notes**: See `docs/compatibility.md` for tool-specific loading tips.

**Tiếng Việt**:
1. **Chọn chế độ**:
   - **Instructor** (học + tinh chỉnh): `skills/smart-pole-instructor/`.
   - **Chat Enforcer** (workflow cho chat-agent): `skills/smart-pole-chat-enforcer/`.
   - **Coding Agent** (tác vụ lập trình): `skills/smart-pole-coding-agent/`.
2. **Nạp prompt** vào phần system/custom instructions của công cụ.
3. **Bắt đầu bằng yêu cầu mơ hồ** và để SMART POLE hỏi thêm các atom còn thiếu.
4. **Ghi chú nền tảng**: Xem `docs/compatibility.md` để biết cách nạp cho từng công cụ.

---

## 📦 Skill Package Layout
- `skills/smart-pole-instructor/`: Instructor skill (`SKILL.md` + `agents/openai.yaml`)
- `skills/smart-pole-chat-enforcer/`: Chat Enforcer skill (`SKILL.md` + `agents/openai.yaml`)
- `skills/smart-pole-coding-agent/`: Coding Agent skill (`SKILL.md` + `agents/openai.yaml`)

---

## 🚀 How to Use / Hướng Dẫn Sử Dụng
This project provides three modes of operation. Choose the one that fits your workflow.
*Dự án cung cấp 3 chế độ hoạt động. Hãy chọn chế độ phù hợp với workflow của bạn.*

### 1. Standard Mode (Conversational) / Chế độ Tiêu chuẩn (Hội thoại)
- **File**: `SKILL.md`
- **Focus**: Education & Guidance.
- **Best for**: Beginners who want to learn prompt engineering or manually refine a prompt.
- **Usage**: Load the skill and chat naturally. The AI will act as a teacher.
- *Phù hợp cho*: Người mới bắt đầu muốn học cách viết prompt hoặc tinh chỉnh thủ công. AI sẽ đóng vai giáo viên hướng dẫn.*

### 2. Chat Enforcer Mode (Workflow) / Chế độ Chat Enforcer (Quy trình)
- **File**: `skills/smart-pole-chat-enforcer/SKILL.md`
- **Focus**: Automation & Strictness.
- **Best for**: Custom chat-agent workflows (Custom GPTs, Gemini Gems) or "Gatekeeper" steps before downstream execution.
- **Usage**: The AI will **NOT** output the result until it detects a perfect prompt. It ends with a machine-readable XML block:
    ```xml
    <master_prompt> ... </master_prompt>
    ```
- *Phù hợp cho*: Workflow chat-agent (Custom GPT, Gemini Gem). AI sẽ **KHÔNG** nhả kết quả cho đến khi prompt hoàn hảo. Nó sẽ kết thúc bằng block XML để máy có thể đọc.*

### 3. Coding Agent Mode (v4.0 — NEW) / Chế độ Coding Agent
- **File**: `skills/smart-pole-coding-agent/SKILL.md`
- **Focus**: AI Coding Agents (OpenAI Codex, Anthropic Claude Code, Google Gemini Code Assist).
- **Best for**: Coding tasks where the agent operates on a codebase — editing files, running tests, using terminal.
- **Usage**: Load the skill into your coding agent. It will auto-extract context from project configs and apply a strict 7-step execution workflow: `ORIENT → CLASSIFY → EXTRACT → DETECT FLAWS → PLAN → EXECUTE → VERIFY`.
- **Important**: The 8-step flow with an explicit `REPORT` step is reserved for custom chat agents (e.g., Custom GPTs, Gemini Gems), not coding-agent execution mode.
- **Docs**: See [Coding Agent Categories](docs/coding-agent-categories.md) for detailed code-native category reference.
- *Phù hợp cho*: Các tác vụ lập trình khi agent thao tác trên codebase — sửa file, chạy test, dùng terminal. Agent sẽ tự động trích xuất ngữ cảnh từ cấu hình dự án.*

### ✨ Chat Enforcer v2.0 Enhancements (New!)
The Chat Enforcer mode has been upgraded with the following features:

| Feature | Description |
|---|---|
| **Weighted Readiness Score** | A dynamic scoring system (10.5-11.0 points) with category weights. Core categories (A, O) = 2.0 points each. **Locale becomes Core (2.0) for domain-sensitive requests** (legal, finance, healthcare). |
| **Iterative Loop** | The AI is **forbidden** from generating a Master Prompt in its first response. It MUST ask clarifying questions first. |
| **Question Protocol** | All questions are numbered and the user is explicitly asked to answer them before proceeding. No more "assumed" atoms. |
| **Overlap Handling** | Built-in rules for handling ambiguous information: Functional Gravity Principle + One Atom One Slot. See [Overlap Rules](docs/overlap-rules.md). |
| **Domain Detection** | Automatic detection of domain-sensitive requests. Warning displayed if Locale is missing for legal/finance/healthcare contexts. |
| **Security Guardrails** | Built-in defenses against **Prompt Injection** and **Prompt Poisoning** attacks. The AI will detect and reject malicious patterns. |

> [!TIP]
> This ensures a thorough brainstorming session between you and the AI, leading to a higher quality Master Prompt.

---

## 💻 For Developers: "VIBE Coding"
**English**:
Use the Enforcer Mode as a "Gatekeeper" before your coding agent.
*Example Workflow*:
1. **Input**: "Write a python script for DB." (Vague!)
2. **SMART POLE**: "I need more info. Which DB? (Resource), What complexity? (Mastery), Speed or readable? (People/Values)."
3. **User**: "Postgres, Senior level, Speed."
4. **SMART POLE**: Outputs `<master_prompt> ... </master_prompt>`.
5. **Coding Agent**: Takes the `<master_prompt>` and writes flawless code because the context is complete.

**Tiếng Việt**:
Sử dụng Enforcer Mode như một "Người gác cổng" trước khi chuyển cho AI viết code.
*Ví dụ Workflow*:
1. **Input**: "Viết script python cho DB." (Quá sơ sài!)
2. **SMART POLE**: "Tôi cần thêm thông tin. DB nào? (Resource), Trình độ nào? (Mastery), Ưu tiên tốc độ hay dễ đọc? (People)."
3. **User**: "Postgres, trình độ Senior, ưu tiên Tốc độ."
4. **SMART POLE**: Xuất ra `<master_prompt> ... </master_prompt>`.
5. **Coder Agent**: Nhận `<master_prompt>` và viết code hoàn hảo vì ngữ cảnh đã đầy đủ.

---

## 📚 Documentation / Tài Liệu
- [Logic Breakdown (Chi tiết Logic)](docs/logic.md)
- [SP Sub-categories Reference (Chi tiết Sub-categories)](docs/sub-categories.md)
- [Overlap Handling Rules (Quy tắc Xử lý Chồng lấn)](docs/overlap-rules.md)
- [Gemini Gem Update Guide (Hướng dẫn Gemini)](docs/gemini-gem-guide.md) **NEW**
- [System Prompt (Conversational)](prompts/system_prompt.md)
- [System Prompt (Chat Enforcer)](prompts/system_prompt_enforcer.md)

---

## ❤️ Special Thanks & Appreciation / Lời Tri Ân

**English**:
This project is built upon the **SMART POLE** framework, a product of the vision and dedication of **Mr. Nam Vihelm (Nguyễn Đình Nam)**. Nam Vihelm is a renowned Vietnamese inventor (founder of VP9 and Vihelm), recognized globally for his innovation during the COVID-19 pandemic. We express our deepest gratitude to him for sharing this systematic framework with the global Prompt Engineering community, enabling us to move from "prompting by feeling" to "Scientific Prompt Engineering."

**Tiếng Việt**:
Dự án này được xây dựng dựa trên framework **SMART POLE**, thành quả từ tầm nhìn và sự cống hiến của anh **Nguyễn Đình Nam (Nam Vihelm)**. Anh Nam Vihelm là một nhà sáng chế nổi tiếng người Việt (người sáng lập VP9 và Vihelm), được biết đến trên toàn cầu với các phát minh đột phá. Chúng tôi xin gửi lời tri ân sâu sắc nhất tới anh vì đã chia sẻ hệ thống tư duy bài bản này tới cộng đồng Prompt Engineering, giúp chúng ta chuyển từ việc "prompt theo cảm tính" sang "Kỹ nghệ Prompt Khoa học".

> [!NOTE]
> Connect with the author: [Nam Vihelm on Facebook](https://www.facebook.com/nam.vihelm)
