# Schema Specification: KB-Ready Markdown Format

Tài liệu này định nghĩa chi tiết đặc tả kỹ thuật (Schema Specification) cho tài liệu Markdown chuẩn **KB-Ready**, đảm bảo tương thích 100% với các bộ phân tách văn bản (Text Splitters), Vector Databases, Open-Notebook, Obsidian và Logseq.

---

## 1. YAML Frontmatter Specification

YAML Frontmatter nằm ở đầu mỗi file, được bao bọc bởi hai dòng phân cách `---`.

| Trường (Field) | Kiểu dữ liệu | Bắt buộc | Mô tả & Ví dụ |
| :--- | :--- | :---: | :--- |
| `title` | String | ✅ Có | Tiêu đề rõ ràng, mô tả đúng nội dung cốt lõi của bài học/tài liệu. |
| `course` | String | ✅ Có | Tên khóa học, danh mục lớn, hoặc tên cuốn sách. |
| `module` | String | 🟡 Tùy chọn | Chuyên đề / Học phần con nếu có. Nếu không có để trống `""`. |
| `instructor`| String | 🟡 Tùy chọn | Tên giảng viên / tác giả. Nếu không rõ ghi `"Không rõ"`. |
| `difficulty`| Enum | ✅ Có | Mức độ phức tạp: `"Cơ bản"` \| `"Trung cấp"` \| `"Nâng cao"`. |
| `target_audience`| String | 🟡 Tùy chọn | Đối tượng hưởng lợi lớn nhất (vd: *Freelancer, Marketer, Chủ doanh nghiệp*). |
| `tags` | List of Strings | ✅ Có | Danh sách 3-6 từ khóa chủ đề (dùng cho Obsidian tags và Vector filtering). |
| `summary` | String | ✅ Có | Tóm tắt cô đọng trong 2-3 câu về bản chất và giá trị của tài liệu. |

---

## 2. Cấu trúc Thân bài (Document Body Hierarchy)

Cấu trúc phân cấp Heading tuân thủ nghiêm ngặt chuẩn Markdown Semantic:

### 2.1 H1 Title (`# {Tên bài học}`)
- Xuất hiện đúng 1 lần sau khối YAML Frontmatter.
- Khớp với trường `title` trong Frontmatter.

### 2.2 H2 Key Takeaways (`## 💡 Tóm Tắt Cốt Lõi (Key Takeaways)`)
- Chứa 3-5 gạch đầu dòng bullet points.
- Mỗi ý là một đúc kết then chốt, cô đọng nhất.
- Dùng cho tính năng Source Summary và Flashcard Generation.

### 2.3 H2 Detailed Content (`## 📖 Nội Dung Chi Tiết`)
- Chứa các phân mục lớn sử dụng thẻ **H3** (`### 1. ...`, `### 2. ...`).
- Triển khai logic chặt chẽ, sử dụng bullet points và in đậm thuật ngữ quan trọng.

### 2.4 Callouts & Blockquotes
- **Case Study / Ví dụ thực tế:**
  ```markdown
  > **Ví dụ / Case Study:** [Chi tiết ví dụ thực tế]
  ```
- **Anti-Patterns / Cảnh báo sai lầm:**
  ```markdown
  > ⚠️ **Lỗi Sai Thường Gặp (Anti-Pattern):** [Chi tiết sai lầm cần tránh]
  ```

### 2.5 H2 Q&A for Search (`## ❓ Câu Hỏi & Trả Lời Trọng Tâm (Q&A for Search)`)
- Chứa 3-5 cặp Hỏi - Đáp theo định dạng:
  ```markdown
  - **Hỏi:** [Câu hỏi tự nhiên mang tính tìm kiếm cao]
    - **Đáp:** [Câu trả lời đầy đủ, độc lập, súc tích]
  ```

---

## 3. Quy chuẩn Định dạng Tối ưu cho RAG (RAG Chunking Rules)

1. **Heading Isolation:** Không lồng quá sâu (chỉ dùng `#`, `##`, `###`). Không dùng `####` hay `#####` vì làm nát cấu trúc chunking.
2. **Atomic Length:** Kích thước tài liệu lý tưởng từ **400 đến 1.800 từ**. Nếu một bài giảng dài hơn 3.000 từ, nên cân nhắc tách thành Phần 1 & Phần 2.
3. **No Trailing Noise:** Tuyệt đối không để lại các câu mang tính hội thoại ở cuối bài (như *"Hẹn gặp lại các bạn ở buổi sau"*, *"Cảm ơn mọi người đã lắng nghe"*).
