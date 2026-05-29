# 🔍 Phase 1 — SCAN

### 📝 List bài toán của tôi:

| #   | Subsidiary (VinFast/Xanh SM...) | Lens               | Mô tả ngắn bài toán                                                        |
| --- | ------------------------------- | ------------------ | -------------------------------------------------------------------------- |
| 1   | Vinfast                         | lặp lại            | Nhân viên Cskh phải trả lời nhiều câu hỏi giống nhau trong cùng 1 ngày     |
| 2   | VinBus                          | Pain từ người khác | Điểm đón khách chưa chính xác giờ cao điểm                                 |
| 3   | Vinhomes                        | Tốn thời gian      | Cư dân phản ánh bằng giấy viết tay về bất cập của tòa nhà                  |
| 4   | Vinmec                          | AI-upgrade         | Tổng đài đặt lịch khám chưa thể tự động tư vấn theo triệu chứng bệnh nhân. |
| 5   | Vinpearl                        | AI-upgrade         | Chatbot CSKH trả lời còn rập khuôn và chưa hỗ trợ cá nhân hóa booking.     |

---

# 🃏 Phase 2 — QUICK-ASSESS: 3 Quick Problem Cards (Cá nhân)

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán (1 câu):                                           │
│ Nhân viên CSKH VinFast phải trả lời lặp lại hàng trăm câu   │
│ hỏi giống nhau mỗi ngày, gây chậm phản hồi và tốn nhân lực. │
│                                                             │
│ Công ty thành viên: [x] VinFast                             │
│                     [ ] Xanh SM  [ ] Vinhomes               │
│                     [ ] Vinmec   [ ] Khác                   │
│                                                             │
│ Ai đang đau (Actor)?                                        │
│ Nhân viên CSKH, Team lead CSKH, khách hàng chờ phản hồi.    │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Khách gửi câu hỏi qua app/Facebook/hotline             │
│      ──> 2. CSKH đọc nội dung                               │
│      ──> 3. Tìm câu trả lời trong guideline/document        │
│      ──> 4. Soạn lại câu trả lời                            │
│      ──> 5. Gửi khách hàng                                  │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                            │
│ Bước 3-4: tìm đúng thông tin và soạn phản hồi               │
│ (⏱ 5-10 phút/lượt)                                          │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                       │
│ AI tự phân loại intent + đề xuất câu trả lời draft          │
│ ngay sau khi khách gửi câu hỏi.                             │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ - Giảm thời gian phản hồi trung bình từ 8 phút → dưới 2 phút│
│ - 60% ticket được AI draft mà không cần sửa nhiều           │
│ - Giảm 30% workload cho CSKH level 1                        │
│                                                             │
│ Quick Architecture:                                         │
│ [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent                     │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán (1 câu):                                           │
│ Tổng đài Vinmec chưa thể tự động tư vấn sơ bộ và điều hướng │
│ đặt lịch khám theo triệu chứng bệnh nhân.                   │
│                                                             │
│ Công ty thành viên:                                         │
│ [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes                      │
│ [x] Vinmec   [ ] Khác                                       │
│                                                             │
│ Ai đang đau (Actor)?                                        │
│ Tổng đài viên, bệnh nhân, bộ phận điều phối khám.           │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Bệnh nhân gọi hotline                                  │
│      ──> 2. Tổng đài hỏi triệu chứng cơ bản                 │
│      ──> 3. Chuyển máy/chọn chuyên khoa phù hợp             │
│      ──> 4. Kiểm tra lịch bác sĩ                            │
│      ──> 5. Đặt lịch khám                                   │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                            │
│ Bước 2-3: xác định chuyên khoa phù hợp                      │
│(⏱ 7-15 phút/lượt)                                          │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                       │
│ AI hỏi triệu chứng dạng conversational + suggest            │
│ chuyên khoa + mức độ ưu tiên khám.                          │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ - Giảm thời gian xử lý cuộc gọi từ 12 phút → dưới 5 phút    │
│ - 70% ca phổ biến được AI pre-screen trước khi gặp người    │
│ - Giảm 25% cuộc gọi chuyển sai chuyên khoa                  │
│                                                             │
│ Quick Architecture:                                         │
│ [ ] No AI  [ ] Rule  [x] LLM  [x] Agent                     │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán (1 câu):                                           │
│ Chatbot Vinpearl hiện trả lời quá rập khuôn và chưa cá nhân │
│ hóa tư vấn booking theo nhu cầu khách hàng.                 │
│                                                             │
│ Công ty thành viên:                                         │
│ [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes                      │
│ [ ] Vinmec   [x] Khác (Vinpearl)                            │
│                                                             │
│ Ai đang đau (Actor)?                                        │
│ Khách hàng đặt phòng, đội sales online, CSKH booking.       │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Khách chat hỏi resort/package                          │
│      ──> 2. Chatbot trả lời template chung                  │
│      ──> 3. Khách phải hỏi lại nhiều lần                    │
│      ──> 4. Chuyển sang nhân viên tư vấn                    │
│      ──> 5. Nhân viên đề xuất combo phù hợp                 │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                            │
│ Bước 2-4: chatbot không hiểu context khách                  │
│ (⏱ mất 10-20 phút mới chốt được nhu cầu)                    │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                       │
│ AI conversational agent hỏi nhu cầu du lịch, ngân sách,     │
│ số người và tự gợi ý package phù hợp.                       │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ - Tăng conversion chat → booking từ 8% → 15%                │
│ - Giảm 40% số cuộc chat cần chuyển người thật               │
│ - Tăng CSAT chatbot từ 3.2 → 4.2/5                          │
│                                                             │
│ Quick Architecture:                                         │
│ [ ] No AI  [ ] Rule  [x] LLM  [x] Agent                     │
└─────────────────────────────────────────────────────────────┘



