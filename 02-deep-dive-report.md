# Nguyễn Vũ Trọng - 2A202600960
# Đỗ Đức Tuệ - 2A202600900
# Trần Quang Thanh- 2A202600620
# Nguyễn Thái Dương - 2A202600547

# 🗳️ Quyết định lựa chọn của nhóm:
Nhóm quyết định chọn bài toán **"Tối ưu hóa thời gian phát hiện sự cố, điều phối cứu nạn và cứu hộ khi xảy ra thiên tai, hỏa hoạn tại các đại đô thị trung tâm thương mại."

## Lý do lựa chọn và loại bỏ các thẻ khác:
* **Card Vinhome/Vincome Retail:** Đây là bài toán có tính thực tiễn cao vì ảnh hưởng trực tiếp đến an toàn cư dân và hiệu quả vận hành đô thị. AI có thể hỗ trợ phát hiện sớm sự cố, tự động cảnh báo và tối ưu điều phối cứu hộ theo thời gian thực, giúp giảm thiểu thiệt hại về người và tài sản. Đồng thời, bài toán phù hợp với hệ sinh thái đô thị thông minh của Vinhome và có tiềm năng triển khai thực tế cao. 
* **Card Vinmec:** Rủi ro rất cao vì liên quan trực tiếp đến sức khỏe bệnh nhân. Sai sót từ AI có thể gây hậu quả nghiêm trọng và kéo theo vấn đề pháp lý, nên cần dữ liệu chuẩn hóa và bác sĩ kiểm duyệt trước khi triển khai thực tế.

# 🏗️ Phase 3 — DEEP-DIVE (Nhóm)

## 3.1. Current-State Workflow
Quy trình xử lý sự cố hết pin thực địa hiện tại của điều phối viên Xanh SM:

```text
┌──────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│ Bước 1       │     │ Bước 2       │     │ Bước 3       │     │ Bước 4       │
│ Nhận cuộc    │     │ Tra cứu định │     │ Tra cứu trạm │     │ Soạn văn bản │
│ gọi sự cố    │ ──→ │ vị GPS xe   │ ──→ │ sạc VinFast  │ ──→ │ hướng dẫn    │
│              │     │              │     │ còn trụ trống│     │ gửi tài xế   │
│ Ai: Dispatch │     │ Ai: Dispatch │     │ Ai: Dispatch │     │ Ai: Dispatch │
│ ⏱ 2 phút     │     │ ⏱ 2 phút     │     │ ⏱ 5 phút 🔴  │     │ ⏱ 5 phút 🔴  │
│ In: Điện thoại│     │ In: Biển số  │     │ In: Vị trí GPS│     │ In: Raw data │
│ Out: Log sự cố│     │ Out: Toạ độ  │     │ Out: Địa chỉ │     │ Out: SMS     │
└──────────────┘     └──────────────┘     └──────────────┘     └──────────────┘
                                                                      │
                                                                      ▼
                                                               ┌──────────────┐
                                                               │ Bước 5       │
                                                               │ Gọi xe cứu   │
                                                               │ hộ (nếu cần) │
                                                               │ Ai: Dispatch │
                                                               │ ⏱ 1 phút     │
                                                               └──────────────┘
🔴 = Bottlenecks
⏱ Tổng thời gian xử lý thủ công: 15 phút/lượt.
```

---

---

## 3.2. Problem Statement (6-field) — Vin Smart Future Standard

| Field | Nội dung |
|---|---|
| **1. Actor / Operator** | Trưởng ca trực PCCC, Nhân viên phòng điều khiển trung tâm (Control Room Operators), và Lực lượng Bảo vệ tuần tra tại các khu đô thị Vinhomes / TTTM Vincom. |
| **2. Current Workflow** | 1. Nhân viên trực an ninh giám sát hàng trăm màn hình camera 24/7 bằng mắt thường. 2. Nhận tín hiệu từ hệ thống cảm biến khói/nhiệt truyền thống (thường xuyên có báo cháy giả do bụi, côn trùng, khói thuốc). 3. Khi có chuông báo, nhân viên phải dùng bộ đàm điều động bảo vệ khu vực chạy đến tận nơi xác minh, mất từ 3-5 phút trước khi quyết định báo động tổng hay gọi 114.|
| **3. Bottleneck** | 

Bước 1: Quá tải thông tin (Blind spot): Mắt người không thể cùng lúc theo dõi hàng ngàn camera. Có thể bỏ sót tia lửa nhỏ hoặc dấu hiệu ngập lụt ở các khu vực khuất (hầm xe, phòng kỹ thuật) cho đến khi sự cố đã bùng phát lớn.

Bước 2: Khi có tín hiệu báo cháy giả nhiều, cư dân hoặc khách hàng sẽ giảm bớt sợ cảnh giác đến các tín hiệu phòng cháy chữa cháy, gây mất cảnh giác. 

Bước 3: Độ trễ trong xác minh: Mất quá nhiều thời gian để con người xác nhận là cháy thật hay báo động giả.

| **4. Business Impact** | 
• Chậm trễ 1 phút có thể khiến đám cháy lan rộng không thể kiểm soát, gây thiệt hại hàng chục đến hàng trăm tỷ đồng (thiệt hại cấu trúc tòa nhà, hầm để xe, tài sản cư dân/khách thuê).


• Nguy cơ đe dọa tính mạng của hàng ngàn cư dân/khách hàng.


• Khủng hoảng truyền thông nghiêm trọng, ảnh hưởng trực tiếp đến uy tín và SLA về an ninh, an toàn của thương hiệu Vingroup.|

| **5. Success Metric** | 
• 100% các sự cố có dấu hiệu khói/lửa/nước ngập bất thường được AI Vision phát hiện và gửi cảnh báo về trung tâm dưới 5 giây.

• Giảm 95% các trường hợp báo động giả (false alarms) cần phải cử người đi xác minh.
• AI Voice/Chatbot tự động tiếp nhận và phân loại 100% các cuộc gọi/tin nhắn báo cáo khẩn cấp từ cư dân để lọc ra vị trí chính xác của sự cố dưới 10 giây.

| **6. Operational Boundary** | 
• AI được phép làm: Phân tích luồng camera liên tục; Cắt hình ảnh/video sự cố gửi ngay lên màn hình lớn của phòng điều khiển; Tự động kích hoạt chuông cảnh báo nội bộ cho nhân viên an ninh; Tổng hợp thông tin từ cuộc gọi cư dân để xác định tọa độ sự cố.


• TUYỆT ĐỐI không được làm: Không tự động kích hoạt hệ thống xả nước (sprinkler) hay bọt chữa cháy; Không tự động ngắt hệ thống điện toàn tòa nhà; Không tự ý phát loa sơ tán tổng hoặc tự động gọi 114 mà không có sự kiểm duyệt.
---

## 3.3. Future-State Flow & AI Fit

* **AI Fit:** 
Thành phần AI	| Vai trò | 	AI Fit
Edge AI Camera Detection	| Phát hiện khói, lửa, ngập nước realtime từ camera edge | 	Cần AI Computer Vision do dữ liệu hình ảnh phức tạp và cần phản ứng realtime
AI Incident Classification| 	Phân loại mức độ sự cố và lọc false alarm | 	AI phù hợp hơn rule-based vì dữ liệu sự cố đa dạng và khó viết rule cố định
Spatial AI + Dynamic Dijkstra | 	Tính toán lộ trình thoát hiểm sạch khói | 	AI hỗ trợ tối ưu đường đi động khi hành lang bị chặn hoặc thang máy ngắt hoạt động
AI Emergency Broadcast System  | Tự động gửi hướng dẫn sơ tán đến điện thoại cư dân và loa nội bộ tòa nhà  |  NLP/LLM giúp tạo thông báo khẩn cấp động theo tình huống realtime thay vì dùng kịch bản ghi âm cố định
Information Extraction AI| 	Tự động trích xuất vị trí, tầng, loại sự cố, mức độ khẩn cấp | 	AI giảm thời gian nhập liệu và tăng tốc dispatch
Human-in-the-loop Approval| 	Trưởng ca xác nhận trước khi kích hoạt PCCC | 	Giữ con người ở decision point quan trọng để giảm rủi ro AI hallucination hoặc false positive

Key Dynamic Inputs

** Hệ thống liên tục cập nhật các điều kiện realtime để tính toán lộ trình thoát hiểm:

***Hành lang bị chặn
***Khu vực có mật độ khói cao
***Thang máy ngắt hoạt động
***Cửa thoát hiểm không khả dụng
***Khu vực nguy hiểm
***Mật độ cư dân theo tầng

Spatial AI sử dụng thuật toán Dynamic Dijkstra để liên tục tái tính toán “lộ trình thoát hiểm sạch khói” theo trạng thái tòa nhà realtime.

---

# 🏁 Phase 5 — EVALUATE (Nhóm, 20 min)

### AI Readiness Checklist:
1. [ ] Chúng tôi có sẵn dữ liệu mẫu/logs sạch để test?
2. [x] Rủi ro khi AI sai có nằm trong tầm kiểm soát (qua HITL hoặc Fallback)?
3. [ ] Stakeholders sẵn sàng thay đổi quy trình làm việc cũ?

### Quyết định cuối cùng của Ban Giám Đốc Vin Smart Future:
[ ] **GO (Bắt đầu xây dựng Prototype):** Bắt đầu phát triển với scope hẹp.
[x] **NOT YET (Cần tích lũy thêm dữ liệu/xác lập baseline):** Trì hoãn để chuẩn bị thêm.
[ ] **NO-GO (Không khả thi / Rule-based tốt hơn):** Hủy bỏ dự án AI này.

**Justification (Lý giải quyết định dựa trên bằng chứng kỹ thuật và chi phí):**
  *Dự án có tiềm năng ứng dụng cao trong hệ sinh thái đô thị thông minh của Vingroup, đặc biệt ở khả năng phát hiện sớm sự cố và tối ưu điều phối cứu hộ theo thời gian thực. Tuy nhiên, hiện tại nhóm chưa có đủ dữ liệu mẫu/logs sạch để huấn luyện và đánh giá độ chính xác của AI. Ngoài ra, chi phí triển khai hạ tầng camera, cảm biến IoT và hệ thống xử lý real-time còn cao, trong khi chưa có baseline rõ ràng để so sánh hiệu quả với rule-based system.*
