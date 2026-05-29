
# 🔍 Phase 1 — SCAN (Cá nhân, 20 min)

### 📝 List bài toán của tôi:
| # | Subsidiary (VinFast/Xanh SM...) | Lens            | Mô tả ngắn bài toán |
|---|----------------------------------|----------------|---------------------|
| 1 | Vinfast                         | Stakeholder Pain| Chủ xe phàn nàn lịch bảo dưỡng chưa tối ưu do xe bị gọi bảo dưỡng theo mốc cố định thay vì tình trạng thực tế của xe.|
| 2 | XanhSM                          | Stakeholder Pain| Tài xế phàn nàn hệ thống gợi ý điểm đón khách chưa chính xác tại chung cư, trung tâm thương mại hoặc khu đông người.  |
| 3 | Vinmec                          | Time-consuming  | Bác sĩ phải nhập hồ sơ bệnh án thủ công, tốn nhiều thời gian paperwork hơn cho việc khám và tư vấn bệnh nhân.|
| 4 | Vinmec                          | AI-upgrade      | Hệ thống chatbot/đặt lịch hiện chưa hỗ trợ tốt việc phân loại chuyên khoa từ mô tả triệu chứng của khách hàng.|
| 5 | XanhSM                          | AI-upgrade      | Hệ thống điều phối chuyến hiện chưa tối ưu theo dữ liệu giao thông và nhu cầu thời gian thực, làm tăng thời gian chờ của khách hàng.|

---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)


```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                    │
│                                                             │
│ Bài toán (1 câu): Chủ xe phàn nàn lịch bảo dưỡng chưa tối ưu do xe bị gọi bảo dưỡng theo mốc cố định thay vì tình trạng thực tế của xe.|
│ Công ty thành viên: VinFast                                 │
│                                                             │
│ Ai đang đau (Actor)? Chủ xe VinFast, kỹ thuật viên bảo dưỡng, trung tâm service │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Xe đạt mốc km/thời gian                                │
│ ──> 2. Hệ thống gửi nhắc bảo dưỡng                          │
│ ──> 3. Chủ xe mang xe đến trung tâm                         │
│ ──> 4. KTV kiểm tra thủ công tình trạng xe                  │
│                                                             │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? 
    Kiểm tra tình trạng xe thủ công (⏱ 20-40 phút/lượt)      │
│ AI có thể nhảy vào hỗ trợ ở bước nào? 
    Phân tích dữ liệu sensor/log xe để dự đoán lỗi và đề xuất │
│   thời điểm bảo dưỡng phù hợp.                              │
│                                                             │
│ Đo thành công bằng gì (Metric có số)? ______________________ │
│   - Giảm 30% số lượt bảo dưỡng không cần thiết │
│ - Giảm thời gian kiểm tra xe từ 40 min → dưới 15 min │
│ - Tăng độ hài lòng khách hàng (CSAT) thêm 15% │
│                                                             │
│ Quick Architecture: LLM   │
└─────────────────────────────────────────────────────────────┘
```

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                     │
│                                                             │
│ Bài toán (1 câu): Bác sĩ Vinmec mất quá nhiều thời gian nhập hồ sơ bệnh án │
│ thủ công thay vì tập trung khám và tư vấn bệnh nhân. │
│ Công ty thành viên: Vinmec                                │
│                                                             │
│ Ai đang đau (Actor)? Bác sĩ, điều dưỡng, bệnh nhân         │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Bệnh nhân mô tả triệu chứng 
│ ──> 2. Bác sĩ khám và trao đổi 
│ ──> 3. Bác sĩ nhập hồ sơ bệnh án thủ công 
│ ──> 4. Điều dưỡng kiểm tra và lưu EMR 
│                   
│ Bước nào tốn thời gian/lỗi nhất? 
│ Bước 3: Nhập hồ sơ bệnh án thủ công 
│ (⏱ 10–20 phút/lượt khám) 
│ 
│ AI có thể nhảy vào hỗ trợ ở bước nào? 
│ Speech-to-text + AI Medical Scribe tự động tạo EMR summary 
│ từ cuộc hội thoại bác sĩ và bệnh nhân.
    
    Sử dụng form sẵn để tăng tốc độ điền 
│ 
│ Đo thành công bằng gì (Metric có số)? 
│ - Giảm thời gian paperwork từ 20 min → dưới 5 min 
│ - Tăng số lượt khám/ngày của bác sĩ thêm 20% 
│ - Giảm lỗi nhập liệu hồ sơ bệnh án 40% 
│ 
│ Quick Architecture: Rule; LLM 
└─────────────────────────────────────────────────────────────┘
```

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #4                                     │
│                                                             │
│ Bài toán (1 câu): Hệ thống chatbot/đặt lịch hiện chưa hỗ trợ tốt việc phân loại chuyên khoa từ mô tả triệu chứng của khách hàng.|
│ Công ty thành viên: Vinmec   
│                                                             │
│ Ai đang đau (Actor)? Bệnh nhân, nhân viên CSKH, bộ phận điều phối khám │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Khách mô tả triệu chứng qua chatbot/hotline 
│ ──> 2. CSKH đọc và phân tích thủ công
│ ──> 3. Điều phối chuyên khoa phù hợp 
│ ──> 4. Nếu sai chuyên khoa → đổi lịch khám 
│
│ Bước nào tốn thời gian/lỗi nhất? 
│ Bước 2–3: Phân tích triệu chứng và điều phối chuyên khoa 
│ (⏱ 5–15 phút/lượt) 
│ 
│ AI có thể nhảy vào hỗ trợ ở bước nào? 
│ NLP/LLM phân tích triệu chứng và gợi ý chuyên khoa phù hợp 
│ theo mức độ ưu tiên. 
│ 
│ Đo thành công bằng gì (Metric có số)? 
│ - Giảm 50% số ca phân sai chuyên khoa 
│ - Giảm thời gian đặt lịch từ 10 min → dưới 2 min
│ - Tăng tỷ lệ khách đặt lịch thành công thêm 20% 
│ 
│ Quick Architecture: LLM 
└─────────────────────────────────────────────────────────────┘
```