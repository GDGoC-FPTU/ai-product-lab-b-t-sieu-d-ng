Nguyễn Vũ Trọng - 2A202600960
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

Duongnt-2A202600547
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

DoDucTue_2A202600900
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


