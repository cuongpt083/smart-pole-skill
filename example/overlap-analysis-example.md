# Overlap Analysis Example / Ví Dụ Phân Tích Chồng Lấn

This example demonstrates how to apply the Overlap Handling Rules when analyzing a user prompt.

*Ví dụ này minh họa cách áp dụng Quy Tắc Xử Lý Chồng Lấn khi phân tích prompt của người dùng.*

---

## Scenario / Kịch Bản

**User Request:**
> "Tôi là một senior developer với 8 năm kinh nghiệm, hiện đang làm việc tại một startup fintech ở Singapore. Tôi lo lắng về deadline cuối tuần này. Hãy giúp tôi viết code Python để xử lý giao dịch thanh toán, tuân thủ PCI-DSS, output dạng JSON. Tham khảo cấu trúc như: { "transaction_id": "...", "status": "..." }"

---

## Step 1: Break Into Atoms / Chia Nhỏ Thành Atoms

| # | Raw Information |
|---|-----------------|
| 1 | "senior developer" |
| 2 | "8 năm kinh nghiệm" |
| 3 | "startup fintech" |
| 4 | "Singapore" |
| 5 | "lo lắng" |
| 6 | "deadline cuối tuần này" |
| 7 | "viết code Python" |
| 8 | "xử lý giao dịch thanh toán" |
| 9 | "tuân thủ PCI-DSS" |
| 10 | "output dạng JSON" |
| 11 | `{ "transaction_id": "...", "status": "..." }` |

---

## Step 2: Apply Functional Gravity / Áp Dụng Trọng Lực Chức Năng

For each atom, determine its PRIMARY intent:

| Atom | Could Be... | Primary Intent → Category |
|------|-------------|--------------------------|
| "senior developer" | People or Mastery? | **Mastery (M)** - Skill level, not personality |
| "8 năm kinh nghiệm" | People or Mastery? | **Mastery (M)** - Reinforces skill level |
| "startup fintech" | Locale or Resource? | **Locale (L)** - Industry domain |
| "Singapore" | Locale | **Locale (L)** - Geography |
| "lo lắng" | People | **People (P)** - Psychographics (emotional state) |
| "deadline cuối tuần này" | Time or Resource? | **Time (T)** - Deadline constraint |
| "viết code Python" | Outline or Aim? | **Outline (O)** - Technical spec |
| "xử lý giao dịch thanh toán" | Aim | **Aim (A)** - Primary goal |
| "tuân thủ PCI-DSS" | Locale or Outline? | **Locale (L)** - Legal/regulatory requirement |
| "output dạng JSON" | Style or Outline? | **Style (S)** - Format specification |
| `{ "transaction_id":... }` | Style or Example? | **Example (E)** - Actual snippet to mimic |

---

## Step 3: Apply One Atom, One Slot / Áp Dụng Một Atom, Một Ô

### Tricky Cases Analysis:

#### Case 1: "senior developer" + "8 năm kinh nghiệm"
- Both indicate skill level
- Both count for **Mastery (M)** 
- ✅ Correct: M gets 2 atoms (no double-counting with People)

#### Case 2: "startup fintech" + "Singapore"
- Both are Locale sub-dimensions
- "fintech" = Industry (L1)
- "Singapore" = Geography (L2)
- ✅ Correct: Both count for **Locale (L)**

#### Case 3: "tuân thủ PCI-DSS"
- Could be Outline (requirement) OR Locale (legal framework)
- Primary intent: **Regulatory context** → **Locale (L)**
- ✅ Assigned to Locale (L3 - Legal)

#### Case 4: "output dạng JSON"
- Could be Style (format) OR Example (structure)
- No actual snippet provided yet → **Style (S)**
- The `{...}` snippet is separate → **Example (E)**

---

## Step 4: Final Categorization / Phân Loại Cuối Cùng

| Category | Atoms | Count |
|----------|-------|-------|
| **S (Style)** | "output dạng JSON" | 1 |
| **M (Mastery)** | "senior developer", "8 năm kinh nghiệm" | 2 |
| **A (Aim)** | "xử lý giao dịch thanh toán" | 1 |
| **R (Resource)** | *(none provided)* | 0 |
| **T (Time)** | "deadline cuối tuần này" | 1 |
| **P (People)** | "lo lắng" | 1 |
| **O (Outline)** | "viết code Python" | 1 |
| **L (Locale)** | "startup fintech", "Singapore", "PCI-DSS" | 3 |
| **E (Example)** | `{"transaction_id":...}` | 1 |

---

## Step 5: Calculate Weighted Score / Tính Điểm Có Trọng Số

| Category | Weight | Present? | Score |
|----------|--------|----------|-------|
| A (Aim) | 2.0 | ✅ | 2.0 |
| O (Outline) | 2.0 | ✅ | 2.0 |
| L (Locale) | 1.5 | ✅ | 1.5 |
| P (People) | 1.5 | ✅ | 1.5 |
| M (Mastery) | 1.0 | ✅ | 1.0 |
| R (Resource) | 1.0 | ❌ | 0.0 |
| T (Time) | 0.5 | ✅ | 0.5 |
| S (Style) | 0.5 | ✅ | 0.5 |
| E (Example) | 0.5 | ✅ | 0.5 |

**Total Score: 9.5/10.5 (90%)** ✅ Above threshold!

---

## Step 6: Identify Missing Information / Xác Định Thông Tin Còn Thiếu

Only **Resource (R)** is missing. Questions to ask:
1. "Có constraints nào về thư viện/framework không? (ví dụ: không dùng Django?)"
2. "Có database hoặc API nào đã có sẵn không?"

---

## Conclusion / Kết Luận

This prompt is **READY** for Master Prompt generation because:
- Score: 90% (above 67% threshold)
- Both Core categories (A, O) are present
- Most important Locale dimensions (Industry, Geography, Legal) are covered

*Prompt này SẴN SÀNG để tạo Master Prompt vì đạt các tiêu chí trên.*

---

## Common Mistakes to Avoid / Các Lỗi Thường Gặp

❌ **Wrong**: Counting "senior developer" for both People AND Mastery
❌ **Wrong**: Counting "PCI-DSS" for both Locale AND Outline  
❌ **Wrong**: Counting "JSON" for both Style AND Example

✅ **Correct**: Apply Functional Gravity → One Atom, One Slot
