# Hướng Dẫn - Xây Custom GPTs và Gemini Gems với VN Chat Enforcer

Tài liệu này hướng dẫn dùng bộ manifest để tạo trợ lý cho các mảng kinh doanh tại Việt Nam:
- trợ lý bán hàng
- trợ lý marketing truyền thống
- trợ lý online marketing
- trợ lý MLM/network marketing
- trợ lý viết nội dung TikTok/Facebook/YouTube
- trợ lý coaching sức khỏe/dinh dưỡng/thực phẩm bổ sung

## 1) Cần nạp những gì
Dùng các file trong package:
- `skill/SKILL.md` (hành vi chính và hard-stop gates)
- `knowledge/VN_COMPLIANCE_BASELINE.md`
- `knowledge/CLAIM_TAXONOMY_VN.md`
- `knowledge/CHANNEL_TEMPLATES_VN.md`
- `docs/OPERATING_GUIDE.md` (quy trình QA nội bộ)

## 2) Tạo Custom GPT (ChatGPT)
1. Mở GPT Builder trong ChatGPT.
2. Dán nội dung `skill/SKILL.md` vào phần system instruction.
3. Nạp các file knowledge:
- `VN_COMPLIANCE_BASELINE.md`
- `CLAIM_TAXONOMY_VN.md`
- `CHANNEL_TEMPLATES_VN.md`
4. Viết mô tả rõ phạm vi:
- "Trợ lý kinh doanh ưu tiên tuân thủ tại Việt Nam cho nội dung marketing/sales. Không phải tư vấn y tế/pháp lý."
5. Thêm starter prompts, ví dụ:
- "Tạo script TikTok cho coaching dinh dưỡng tại Việt Nam với ngôn từ an toàn."
- "Viết lại bài tuyển cộng tác viên MLM để loại bỏ claim rủi ro."
- "Tạo bài Facebook giáo dục về thực phẩm bổ sung có disclosure phù hợp."

## 3) Tạo Gemini Gem
1. Mở trang tạo/chỉnh sửa Gem.
2. Dán `skill/SKILL.md` vào instruction của Gem.
3. Đính kèm 3 file knowledge làm tài liệu tham chiếu.
4. Cấu hình metadata đúng phạm vi:
- trợ lý kinh doanh tại Việt Nam
- soạn thảo có kiểm soát compliance
- không dùng cho coding-agent execution
5. Chạy test prompts trước khi đưa vào vận hành.

## 4) Cấu hình khuyến nghị cho Agent
- Ngôn ngữ: ưu tiên tiếng Việt, tiếng Anh tùy chọn.
- Giọng điệu: thực tế, thận trọng, không overpromise.
- Kiểu output: ngắn gọn, hành động được.
- Luôn có:
1. mức rủi ro
2. phân loại claim (safe/restricted/blocked)
3. đoạn disclosure
4. phương án rewrite an toàn nếu bị block

## 5) Quy trình vận hành hằng ngày
1. Người dùng gửi yêu cầu campaign.
2. Agent phân loại task + rủi ro.
3. Agent hỏi bổ sung các SMART POLE atoms còn thiếu.
4. Agent áp dụng VN compliance + claim classifier.
5. Nếu có blocked claim: từ chối và đề xuất rewrite an toàn.
6. Nếu qua tất cả gates: tạo draft + `<master_prompt>`.
7. Người duyệt nội bộ chốt trước khi xuất bản.

## 6) Mẫu thông tin đầu vào để ra kết quả tốt
Nên yêu cầu người dùng cung cấp:
- loại hình kinh doanh và chân dung khách hàng mục tiêu
- nhóm sản phẩm (đặc biệt health/supplement)
- kênh (TikTok/Facebook/YouTube)
- mục tiêu (lead, chuyển đổi, giáo dục, giữ chân)
- cụm từ/claim cần cấm
- nguồn bằng chứng hoặc danh mục claim đã duyệt (nếu có)

Ví dụ prompt intake:
`Hãy tạo nội dung cho [kênh] trong lĩnh vực [lĩnh vực], đối tượng [đối tượng], mục tiêu [mục tiêu], tránh các cụm từ [cấm], ưu tiên thông điệp [ưu tiên].`

## 7) Nhóm tín hiệu đỏ (phải block hoặc escalate)
- claim chữa/điều trị/phòng bệnh
- cam kết timeline giảm cân chắc chắn
- cam kết thu nhập trong MLM/network marketing
- tạo khan hiếm giả, thúc ép sai lệch
- khai thác nhóm đối tượng dễ tổn thương

## 8) QA tối thiểu trước khi đăng
Mỗi output cần kiểm:
1. Không có blocked claim
2. Có disclosure phù hợp
3. Không có cam kết kết quả tuyệt đối
4. Giọng điệu trung thực, không gây hiểu nhầm
5. Có xác nhận duyệt của người phụ trách

## 9) Quản lý phiên bản và thay đổi
- Quản lý version package trong private repo.
- Ghi commit theo nhóm thay đổi:
- `policy: ...`
- `risk: ...`
- `template: ...`
- Sau mỗi lần cập nhật, chạy lại bộ red-team prompts.

## 10) Ranh giới sử dụng quan trọng
Trợ lý này chỉ hỗ trợ soạn thảo:
- Không phải tư vấn pháp lý
- Không phải tư vấn/chẩn đoán/điều trị y khoa
- Cần người phụ trách compliance duyệt trước khi publish
