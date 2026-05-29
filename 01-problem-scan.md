# 🔍 Phase 1 — SCAN
### 📝 List bài toán của tôi:
| # | Subsidiary (VinFast/Xanh SM...) | Lens                                   | Mô tả ngắn bài toán |
|---|---------------------------------|----------------------------------------|---------------------|
| 1 | VinFast                         | Predictive Maintenance / IoT AI        | Dữ liệu cảm biến xe điện hiện chủ yếu dùng để monitoring cơ bản, chưa tối ưu cho dự đoán hỏng hóc. Việc bảo trì còn phụ thuộc vào lịch định kỳ hoặc tài xế báo lỗi, dẫn đến downtime đột xuất, backlog xưởng dịch vụ và tăng warranty cost. Có thể xây AI anomaly detection + failure prediction từ CAN Bus/Battery telemetry để giảm downtime và tối ưu lịch bảo trì. |
| 2 | Xanh SM                         | Fleet Optimization / Demand Forecasting| Điều phối tài xế và phân bổ xe theo thời gian thực chưa tối ưu trong giờ cao điểm. Nhiều xe idle sai khu vực trong khi khu vực khác thiếu supply, làm tăng ETA, tỷ lệ hủy chuyến và empty-trip distance. Có thể dùng AI demand forecasting + reinforcement learning để repositioning tài xế theo heatmap nhu cầu.|
| 3 | Vinhomes                        | Smart Building / Energy AI             | Các khu đô thị lớn vận hành nhiều hệ thống điện, nước, HVAC và an ninh nhưng vẫn phụ thuộc nhiều vào rule-based system và giám sát thủ công. Điện năng tiêu thụ ở khu tiện ích và tòa nhà có thể bị lãng phí do không tối ưu theo occupancy thực tế. AI có thể dự đoán usage pattern để tối ưu điện năng, điều hòa và bảo trì thiết bị.|
| 4 | Vinmec                          | Healthcare Operations AI               | Quy trình tiếp nhận bệnh nhân, phân luồng khám và xử lý hồ sơ y tế vẫn tiêu tốn nhiều manpower. Bác sĩ và nhân viên phải xử lý lượng lớn dữ liệu phi cấu trúc (triệu chứng, bệnh án, kết quả xét nghiệm). Có thể triển khai AI medical assistant để tự động tóm tắt hồ sơ, hỗ trợ triage và giảm thời gian xử lý hành chính.|
| 5 | Vinhomes / Vincom Retail        | Risk & Cost                            | Quy trình ứng phó thiên tai, hỏa hoạn hiện tại phụ thuộc vào thiết bị cơ học tĩnh và điều phối thủ công, dẫn đến nhiều điểm nghẽn nghiêm trọng: đầu báo khói truyền thống chỉ kích hoạt khi khói chạm trần (chậm 3-5 phút) và dễ báo động giả; loa phát thanh tĩnh và bảng chỉ dẫn cố định không cập nhật được diễn biến đám cháy gây nguy cơ điều hướng cư dân vào vùng khói độc; thông báo cào bằng diện rộng gây hoảng loạn; và việc bảo trì thiết bị PCCC theo lịch định kỳ dễ bỏ sót hỏng hóc đột xuất. Khi sự cố xảy ra, việc thiếu dữ liệu thời gian thực và phương án diễn tập dựa trên giả định chủ quan khiến đội an ninh hoảng loạn, rò rỉ hiệu suất cứu nạn và gây thiệt hại lớn về người và tài sản.Giải pháp AI gộp chung: Xây dựng Hệ thống trung tâm điều hành khẩn cấp thông minh (AI Emergency Response Suite) tích hợp đa mô hình:1. Edge-AI Video Analytics (YOLO): Nhận diện tia lửa/làn khói nhỏ qua CCTV ngay từ giây thứ 3 tại hầm xe/hành lang để kích hoạt cảnh báo sớm.2. Graph Neural Networks (GNN): Mô hình hóa tòa nhà thành đồ thị động, liên tục quét các nút bị chặn để tính toán và chỉ dẫn "Lộ trình thoát hiểm sạch khói" theo thời gian thực.3. GenAI Emergency Broadcasting: Tự động kết nối vị trí đám cháy với sơ đồ căn hộ để soạn/phát tin nhắn cảnh báo cá nhân hóa (ví dụ: hướng dẫn cư dân tầng 15 đi lối thang bộ phía Tây để tránh nguồn cháy ở tầng 12) qua App cư dân.4. Predictive Maintenance & Digital Twin: Phân tích dữ liệu cảm biến IoT để phát hiện sớm lỗi tụt áp, rò rỉ của hệ thống bơm/đầu phun Sprinkler, đồng thời giả lập hành vi đám đông trên bản sao số để tối ưu phương án bố trí lực lượng cứu hộ.|


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
│ QUICK PROBLEM CARD #03                                      │
│                                                             │
│ Bài toán (1 câu): Tối ưu hóa thời gian phát hiện sự cố,     │
│ điều phối cứu nạn và sơ tán cư dân tự động khi xảy ra thiên │
│ tai, hỏa hoạn tại các đại đô thị và trung tâm thương mại.  │
│                                                             │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [X] Vinhomes  │
│                     [ ] Vinmec   [X] Khác: Vincom Retail    │
│                                                             │
│ Ai đang đau (Actor)? Ban Quản lý (BQL), Đội An ninh/Cứu hộ, │
│ và Cư dân/Khách mua sắm tại tòa nhà.                        │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Đầu báo khói vật lý kích hoạt hoặc Bảo vệ phát hiện    │
│      khói/cháy qua tuần tra trực tiếp.                      │
│   ──> 2. Đội An ninh xác minh thủ công tại hiện trường để    │
│          loại trừ báo động giả.                             │
│   ──> 3. BQL bấm nút kích hoạt hệ thống chuông báo cháy toàn │
│          tòa nhà và phát loa thông báo diện rộng.           │
│   ──> 4. Đội Cứu hộ hướng dẫn cư dân di tản theo các biển   │
│          chỉ dẫn tĩnh và kiểm tra thủ công trạng thái IoT.  │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 1 & Bước 4            │
│ (⏱ 3 - 5 phút/lượt phát hiện; 15 - 20 phút/lượt điều phối)  │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                       │
│ - Bước 1: Edge-AI tự động nhận diện khói/lửa từ giây thứ 3. │
│ - Bước 3 & 4: GNN & GenAI tự động tính toán lộ trình thoát  │
│   hiểm sạch khói và phát tin nhắn điều hướng cá nhân hóa.   │
│ - Hỗ trợ liên tục: Predictive Maintenance quét lỗi IoT PCCC.│
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ - Giảm thời gian phát hiện đám cháy từ 3-5 phút ──> dưới 3s.│
│ - Tăng độ chính xác định vị nguồn cháy/ngập đạt trên 98%.  │
│ - Giảm 50% thời gian di tản cư dân nhờ luồng điều hướng động.│
│ - Đảm bảo tỷ lệ sẵn sàng của thiết bị IoT PCCC đạt 100%.    │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [X] LLM  [X] Agent │
│ *Ghi chú kĩ thuật: Kết hợp Edge-AI (YOLO), GNN và LLM Agent │
└─────────────────────────────────────────────────────────────┘
