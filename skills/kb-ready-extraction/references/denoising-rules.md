# Denoising Rules: Cleaning Conversational Transcripts

Tài liệu này cung cấp bộ quy tắc làm sạch chi tiết (Denoising Heuristics) nhằm loại bỏ rác đàm thoại và các khiếm khuyết của công nghệ nhận dạng tiếng nói (ASR) trước khi cấu trúc hóa tri thức.

---

## 1. Danh sách các mẫu rác cần loại bỏ 100% (Zero Tolerance)

| Loại rác | Ví dụ thực tế trong Transcript | Hành động xử lý |
| :--- | :--- | :--- |
| **Chào hỏi / Mở đầu** | *"Alo alo cả nhà nghe rõ không?", "Chào các bạn đã đến với buổi học hôm nay..."* | ❌ Xóa bỏ hoàn toàn |
| **Kiểm tra kỹ thuật** | *"Em thấy slide của anh chưa?", "Đợi anh test mic tí nhé..."* | ❌ Xóa bỏ hoàn toàn |
| **Gọi tên tương tác cá nhân** | *"Bạn Lan trả lời câu này cho anh", "Anh thấy bạn Tuấn vừa comment..."* | ❌ Xóa bỏ hoàn toàn |
| **Thông báo hành chính** | *"Nhớ nộp bài tập trước 12h đêm nay", "Lớp mình nghỉ giải lao 10 phút nhé..."* | ❌ Xóa bỏ hoàn toàn |
| **Từ đệm nói tự do** | *"À", "ừm", "thì", "là", "mà", "các bạn nhé", "đúng không nào", "nói chung là..."* | ❌ Xóa bỏ khỏi câu |
| **Ảo giác lặp từ của ASR** | *"tôi tôi tôi sẽ sẽ đi vào vào vấn đề..."* | ❌ Xóa bỏ lặp từ |
| **Kết thúc đàm thoại** | *"Buổi hôm nay dừng ở đây", "Chúc các bạn ngủ ngon nhé..."* | ❌ Xóa bỏ hoàn toàn |

---

## 2. Quy tắc Giữ lại & Nâng tầm Tri thức (Preservation Rules)

1. **Thuật ngữ chuyên môn (Domain Jargon):**
   - Giữ nguyên vẹn các thuật ngữ kỹ thuật, từ viết tắt và khái niệm chuyên sâu (ví dụ: *AIDA, PAS, Top of Funnel, CPA, CTR, RoAS, Backlink, SEO Onpage...*).
   - Nếu ASR ghi sai chính tả thuật ngữ tiếng Anh (vd: *"ây đê a"* -> *"AIDA"*, *"xì trát te gi"* -> *"strategy"*), phải tự động hiệu chỉnh về đúng thuật ngữ chuẩn.

2. **Số liệu & Công thức (Formulas & Metrics):**
   - Giữ lại toàn bộ tỷ lệ phần trăm, ngân sách mẫu, công thức tính toán và mốc thời gian bài học đưa ra.

3. **Ví dụ thực tiễn (Real-world Examples & Analogies):**
   - Các ví dụ minh họa của giảng viên (vd: *Ví dụ bán mỹ phẩm, ví dụ trung tâm tiếng Anh, chuyện chạy ads thất bại...*) phải được bảo tồn và viết lại mạch lạc, đóng gói vào mục .

4. **Kinh nghiệm kiêng kỵ (Anti-patterns):**
   - Các cảnh báo về sai lầm thường gặp được đóng gói vào mục .

---

## 3. Chuyển đổi Văn phong (Tone & Style Transformation)

- **Từ Văn nói:** Ngập ngừng, ngắt quãng, xưng hô "mình - các bạn", câu cú lộn xộn.
- **Sang Văn viết:** Khách quan, trung tính, cấu trúc câu mạch lạc, tính học thuật và sư phạm cao, sử dụng chủ ngữ chung hoặc câu chủ động/bị động chuyên nghiệp.
