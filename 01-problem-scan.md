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
Phase 1
| # | Subsidiary | Lens                                          | Mô tả ngắn bài toán                                                                                                                                                                                                                                      |
| - | ---------- | --------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1 | Xanh SM    | Dispatch thủ công / bán rule-based            | Điều phối xe – khách dựa trên vị trí gần nhất + kinh nghiệm dispatcher, chưa tối ưu ETA/traffic theo thời gian thực → gây xe chạy vòng và tăng thời gian chờ. Ước tính thất thoát: **10–18% idle mileage**, **8–12% giảm hiệu suất fleet giờ cao điểm**. |
| 2 | Xanh SM    | Dự báo nhu cầu theo giờ/khu vực thủ công      | Ops team dùng dashboard + kinh nghiệm để điều xe theo “hot zone” thay vì forecast chuẩn hóa. Sai lệch cung–cầu gây **15–25% mismatch**, làm mất doanh thu giờ peak và tăng xe rỗng.                                                                      |
| 3 | Xanh SM    | Xử lý khiếu nại khách hàng thủ công           | CSKH phân loại complaint (trễ xe, thái độ, mất đồ) bằng đọc tay + nhập CRM → mất 3–8 phút/case. Với ~50k case/tháng → mất **2.500–6.000 giờ công/tháng**, giảm SLA và NPS ~10–20%.                                                                       |
| 4 | Xanh SM    | Quản lý tài xế & chấm điểm hiệu suất thủ công | Rating + KPI cơ bản, thiếu dữ liệu hành vi (phanh gấp, tốc độ, vòng chạy). Dẫn tới **5–12% giảm hiệu suất vận hành**, tăng rủi ro an toàn và bias trong đánh giá tài xế.                                                                                 |
| 5 | Xanh SM    | Điều phối xe rỗng & repositioning thủ công    | Tài xế tự quyết định di chuyển khi không có khách hoặc theo gợi ý đơn giản → không tối ưu supply redistribution. Gây **12–20% xe di chuyển không tạo doanh thu** trong giờ thấp điểm.                                                                    |


Phase 2

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán (1 câu): Tối ưu điều phối xe và tài xế theo thời   │
│ gian thực để giảm thời gian chờ và xe chạy rỗng.            │
│                                                             │
│ Công ty thành viên:              [X] Xanh SM                │
│                                                             │
│                                                             │
│ Ai đang đau (Actor)? Dispatcher / hệ thống điều phối        │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│ 1. Nhận yêu cầu khách                                       │
│ 2. Xem vị trí tài xế gần nhất (map)                         │
│ 3. Gán chuyến theo kinh nghiệm / rule đơn giản →            │
│ 4. Điều chỉnh nếu tài xế từ chối →                          │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2–3 (~30–90s/lượt)    │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Ranking tài xế theo   │
│ ETA + traffic + distance                                    │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ - Giảm pickup time: 8 min → 5 min                           │
│ - Giảm idle km: -10–15%                                     │
│                                                             │
│ Quick Architecture: [ ] No AI  [X] Rule  [ ] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán (1 câu): Dự đoán nhu cầu gọi xe theo khu vực để    │
│ tối ưu phân bổ tài xế theo giờ cao điểm.                    │
│                                                             │
│ Công ty thành viên:   [X] Xanh SM                           │
│                                                             │
│                                                             │
│ Ai đang đau (Actor)? Fleet planner / Ops manager            │
│                                                             │
│ Workflow thủ công hiện tại:                                 │
│ 1. Xem lịch sử chuyến theo ngày →                           │
│ 2. Ước lượng giờ cao điểm →                                 │
│ 3. Điều xe sang khu hot →                                   │
│ 4. Điều chỉnh theo cảm tính / kinh nghiệm                   │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 (~manual guess)     │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Forecast demand       │
│ theo time-slot + zone                                       │
│                                                             │
│ Metric:                                                     │
│ - giảm mismatch supply-demand 10–20%                        │
│ - tăng utilization fleet                                    │
│                                                             │
│ Quick Architecture: [ ] No AI  [X] Rule  [ ] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán (1 câu): Tự động phân loại và xử lý khiếu nại      │
│ khách hàng từ call center / chat.                           │
│                                                             │
│ Công ty thành viên: [ ] VinFast  [X] Xanh SM  [ ] Vinhomes  │
│                                      │
│                                                             │
│ Ai đang đau (Actor)? CSKH / Call center agent               │
│                                                             │
│ Workflow thủ công hiện tại:                                 │
│ 1. Nhận cuộc gọi/chat →                                     │
│ 2. Đọc nội dung →                                           │
│ 3. Tự phân loại loại complaint →                            │
│ 4. Gửi sang team liên quan →                                │
│ 5. Ghi CRM                                                  │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 3 (~30–120s/case)     │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Classification +      │
│ routing                                                     │
│                                                             │
│ Metric:                                                     │
│ - giảm handling time 40%                                    │
│ - tăng SLA compliance                                       │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [X] LLM  [ ] Agent │
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

Trần Quang Thanh - 2A202600620
Phase 1
| # | Subsidiary | Lens                                          | Mô tả ngắn bài toán                                                                                                                                                                                                                                      |
| - | ---------- | --------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1 | Xanh SM    | Dispatch thủ công / bán rule-based            | Điều phối xe – khách dựa trên vị trí gần nhất + kinh nghiệm dispatcher, chưa tối ưu ETA/traffic theo thời gian thực → gây xe chạy vòng và tăng thời gian chờ. Ước tính thất thoát: **10–18% idle mileage**, **8–12% giảm hiệu suất fleet giờ cao điểm**. |
| 2 | Xanh SM    | Dự báo nhu cầu theo giờ/khu vực thủ công      | Ops team dùng dashboard + kinh nghiệm để điều xe theo “hot zone” thay vì forecast chuẩn hóa. Sai lệch cung–cầu gây **15–25% mismatch**, làm mất doanh thu giờ peak và tăng xe rỗng.                                                                      |
| 3 | Xanh SM    | Xử lý khiếu nại khách hàng thủ công           | CSKH phân loại complaint (trễ xe, thái độ, mất đồ) bằng đọc tay + nhập CRM → mất 3–8 phút/case. Với ~50k case/tháng → mất **2.500–6.000 giờ công/tháng**, giảm SLA và NPS ~10–20%.                                                                       |
| 4 | Xanh SM    | Quản lý tài xế & chấm điểm hiệu suất thủ công | Rating + KPI cơ bản, thiếu dữ liệu hành vi (phanh gấp, tốc độ, vòng chạy). Dẫn tới **5–12% giảm hiệu suất vận hành**, tăng rủi ro an toàn và bias trong đánh giá tài xế.                                                                                 |
| 5 | Xanh SM    | Điều phối xe rỗng & repositioning thủ công    | Tài xế tự quyết định di chuyển khi không có khách hoặc theo gợi ý đơn giản → không tối ưu supply redistribution. Gây **12–20% xe di chuyển không tạo doanh thu** trong giờ thấp điểm.                                                                    |


Phase 2

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán (1 câu): Tối ưu điều phối xe và tài xế theo thời   │
│ gian thực để giảm thời gian chờ và xe chạy rỗng.            │
│                                                             │
│ Công ty thành viên:              [X] Xanh SM                │
│                                                             │
│                                                             │
│ Ai đang đau (Actor)? Dispatcher / hệ thống điều phối        │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│ 1. Nhận yêu cầu khách                                       │
│ 2. Xem vị trí tài xế gần nhất (map)                         │
│ 3. Gán chuyến theo kinh nghiệm / rule đơn giản →            │
│ 4. Điều chỉnh nếu tài xế từ chối →                          │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2–3 (~30–90s/lượt)    │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Ranking tài xế theo   │
│ ETA + traffic + distance                                    │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ - Giảm pickup time: 8 min → 5 min                           │
│ - Giảm idle km: -10–15%                                     │
│                                                             │
│ Quick Architecture: [ ] No AI  [X] Rule  [ ] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán (1 câu): Dự đoán nhu cầu gọi xe theo khu vực để    │
│ tối ưu phân bổ tài xế theo giờ cao điểm.                    │
│                                                             │
│ Công ty thành viên:   [X] Xanh SM                           │
│                                                             │
│                                                             │
│ Ai đang đau (Actor)? Fleet planner / Ops manager            │
│                                                             │
│ Workflow thủ công hiện tại:                                 │
│ 1. Xem lịch sử chuyến theo ngày →                           │
│ 2. Ước lượng giờ cao điểm →                                 │
│ 3. Điều xe sang khu hot →                                   │
│ 4. Điều chỉnh theo cảm tính / kinh nghiệm                   │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 (~manual guess)     │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Forecast demand       │
│ theo time-slot + zone                                       │
│                                                             │
│ Metric:                                                     │
│ - giảm mismatch supply-demand 10–20%                        │
│ - tăng utilization fleet                                    │
│                                                             │
│ Quick Architecture: [ ] No AI  [X] Rule  [ ] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán (1 câu): Tự động phân loại và xử lý khiếu nại      │
│ khách hàng từ call center / chat.                           │
│                                                             │
│ Công ty thành viên: [ ] VinFast  [X] Xanh SM  [ ] Vinhomes  │
│                                      │
│                                                             │
│ Ai đang đau (Actor)? CSKH / Call center agent               │
│                                                             │
│ Workflow thủ công hiện tại:                                 │
│ 1. Nhận cuộc gọi/chat →                                     │
│ 2. Đọc nội dung →                                           │
│ 3. Tự phân loại loại complaint →                            │
│ 4. Gửi sang team liên quan →                                │
│ 5. Ghi CRM                                                  │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 3 (~30–120s/case)     │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Classification +      │
│ routing                                                     │
│                                                             │
│ Metric:                                                     │
│ - giảm handling time 40%                                    │
│ - tăng SLA compliance                                       │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [X] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘