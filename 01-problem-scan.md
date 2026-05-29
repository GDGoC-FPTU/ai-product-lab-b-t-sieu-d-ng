# 🔍 Phase 1 — SCAN
### 📝 List bài toán của tôi:
| # | Subsidiary (VinFast/Xanh SM...) | Lens                                   | Mô tả ngắn bài toán |
|---|---------------------------------|----------------------------------------|---------------------|
| 1 | VinFast                         | Predictive Maintenance / IoT AI        | Dữ liệu cảm biến xe điện hiện chủ yếu dùng để monitoring cơ bản, chưa tối ưu cho dự đoán hỏng hóc. Việc bảo trì còn phụ thuộc vào lịch định kỳ hoặc tài xế báo lỗi, dẫn đến downtime đột xuất, backlog xưởng dịch vụ và tăng warranty cost. Có thể xây AI anomaly detection + failure prediction từ CAN Bus/Battery telemetry để giảm downtime và tối ưu lịch bảo trì. |
| 2 | Xanh SM                         | Fleet Optimization / Demand Forecasting| Điều phối tài xế và phân bổ xe theo thời gian thực chưa tối ưu trong giờ cao điểm. Nhiều xe idle sai khu vực trong khi khu vực khác thiếu supply, làm tăng ETA, tỷ lệ hủy chuyến và empty-trip distance. Có thể dùng AI demand forecasting + reinforcement learning để repositioning tài xế theo heatmap nhu cầu.|
| 3 | Vinhomes                        | Smart Building / Energy AI             | Các khu đô thị lớn vận hành nhiều hệ thống điện, nước, HVAC và an ninh nhưng vẫn phụ thuộc nhiều vào rule-based system và giám sát thủ công. Điện năng tiêu thụ ở khu tiện ích và tòa nhà có thể bị lãng phí do không tối ưu theo occupancy thực tế. AI có thể dự đoán usage pattern để tối ưu điện năng, điều hòa và bảo trì thiết bị.|
| 4 | Vinmec                          | Healthcare Operations AI               | Quy trình tiếp nhận bệnh nhân, phân luồng khám và xử lý hồ sơ y tế vẫn tiêu tốn nhiều manpower. Bác sĩ và nhân viên phải xử lý lượng lớn dữ liệu phi cấu trúc (triệu chứng, bệnh án, kết quả xét nghiệm). Có thể triển khai AI medical assistant để tự động tóm tắt hồ sơ, hỗ trợ triage và giảm thời gian xử lý hành chính.|
| 5 | VinCommerce                     | Retail Supply Chain AI                 | Forecast hàng hóa tại siêu thị còn phụ thuộc nhiều vào kinh nghiệm và rule truyền thống, dẫn đến overstock hoặc out-of-stock ở từng khu vực. Đặc biệt với hàng tươi sống, việc dự đoán sai gây thất thoát lớn do hủy hàng và giảm trải nghiệm khách hàng. AI forecasting có thể tối ưu tồn kho theo mùa vụ, thời tiết và hành vi mua hàng địa phương.|


# 🃏 Phase 2 — QUICK-ASSESS
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán (1 câu):                                           │
│ Xe điện bị downtime đột xuất do chưa dự đoán sớm lỗi pin,   │
│ motor hoặc hệ thống điện.                                   │
│                                                             │
│ Công ty thành viên:                                         │
│ [x] VinFast  [ ] Xanh SM  [ ] Vinhomes                      │
│ [ ] Vinmec   [ ] Khác (Ghi rõ)________                      │
│                                                             │
│ Ai đang đau (Actor)?                                        │
│ Fleet Operations, kỹ thuật viên bảo trì, customer support   │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│ 1. Xe phát sinh lỗi                                         │
│    ──> 2. Tài xế báo lỗi/manual check                       │
│    ──> 3. Kỹ thuật viên kiểm tra                            │
│    ──> 4. Đặt lịch sửa + thay linh kiện                     │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                            │
│ Phát hiện lỗi & chẩn đoán nguyên nhân                       │
│ (⏱ 30–90 phút/lượt)                                        │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                       │
│ Phân tích telemetry/CAN Bus để anomaly detection và         │
│ predictive maintenance trước khi xe hỏng thực sự            │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ - Giảm downtime xe từ 3h → dưới 1.5h/tháng                  │
│ - Giảm 20% warranty inspection thủ công                     │
│ - Tăng fleet utilization thêm 8–10%                         │
│                                                             │
│ Quick Architecture:                                         │
│ [ ] No AI  [ ] Rule  [ ] LLM  [x] Agent                     │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán (1 câu):                                           │
│ Điều phối tài xế chưa tối ưu khiến nhiều xe chạy rỗng và    │
│ khách phải chờ lâu giờ cao điểm.                            │
│                                                             │
│ Công ty thành viên:                                         │
│ [ ] VinFast  [x] Xanh SM  [ ] Vinhomes                      │
│ [ ] Vinmec   [ ] Khác (Ghi rõ)________                      │
│                                                             │
│ Ai đang đau (Actor)?                                        │
│ Driver Operations, dispatcher team, khách hàng              │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│ 1. Theo dõi nhu cầu chuyến theo khu vực                     │
│    ──> 2. Điều phối tài xế bằng rule cố định                │
│    ──> 3. Driver tự di chuyển tìm khách                     │
│    ──> 4. Dispatcher xử lý surge/thừa thiếu xe              │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                            │
│ Reposition tài xế theo thời gian thực                       │
│ (⏱ 5–15 phút/lần điều phối)                                │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                       │
│ Forecast demand + gợi ý reposition driver theo heatmap      │ 
│ realtime bằng reinforcement learning                        │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ - Giảm empty-trip distance 15%                              │
│ - Giảm ETA trung bình từ 8 phút → dưới 5 phút               │
│ - Tăng completed trips thêm 10%                             │
│                                                             │
│ Quick Architecture:                                         │
│ [ ] No AI  [ ] Rule  [ ] LLM  [x] Agent                     │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán (1 câu):                                           │
│ Nhân viên y tế mất nhiều thời gian nhập liệu và đọc hồ sơ   │
│ bệnh án thủ công trước khi khám bệnh.                       │
│                                                             │
│ Công ty thành viên:                                         │
│ [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes                      │
│ [x] Vinmec   [ ] Khác (Ghi rõ)________                      │
│                                                             │
│ Ai đang đau (Actor)?                                        │
│ Bác sĩ, điều dưỡng, nhân viên tiếp nhận                     │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│ 1. Tiếp nhận bệnh nhân                                      │
│    ──> 2. Nhập triệu chứng thủ công                         │
│    ──> 3. Đọc lịch sử bệnh án                               │
│    ──> 4. Chuyển bác sĩ đánh giá                            │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                            │
│ Đọc + tổng hợp hồ sơ bệnh án                                │
│ (⏱ 10–20 phút/bệnh nhân)                                   │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                       │
│ Speech-to-text + LLM tóm tắt bệnh án và auto-triage         │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ - Giảm thời gian xử lý hồ sơ từ 15 phút → dưới 5 phút       │
│ - Giảm 40% thao tác nhập liệu thủ công                      │
│ - Tăng số bệnh nhân xử lý mỗi ca thêm 15–20%                │
│                                                             │
│ Quick Architecture:                                         │
│ [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent                     │
└─────────────────────────────────────────────────────────────┘
