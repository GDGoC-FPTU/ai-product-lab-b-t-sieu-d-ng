Nguyễn Vũ Trọng - 2A202600960
# 📝 Phase 6 — REFLECTION (Cá nhân)
Reflection — Nhật ký tương tác với AI trong buổi học

Trong buổi học hôm nay, tôi sử dụng AI để brainstorm ý tưởng cho bài toán tối ưu hóa thời gian phát hiện sự cố, điều phối cứu nạn và cứu hộ tại các đại đô thị và trung tâm thương mại khi xảy ra thiên tai hoặc hỏa hoạn.

AI giúp tôi:

Gợi ý các pain point trong quy trình cứu hộ như phát hiện cháy chậm, điều phối lực lượng chưa tối ưu hoặc thiếu cảnh báo realtime.
Đề xuất workflow xử lý sự cố và các metric đo hiệu quả như thời gian phản ứng hay thời gian sơ tán.
Phân biệt khi nào nên dùng rule-based system và khi nào nên dùng AI/LLM.

Tuy nhiên, AI đôi lúc đề xuất solution quá phức tạp như dùng Agentic AI cho toàn bộ hệ thống cứu hộ, trong khi nhiều tình huống thực tế chỉ cần rule-based alert và camera detection là đủ nhanh và ổn định hơn.

Sau đó, tôi điều chỉnh prompt bằng cách yêu cầu AI đóng vai trò CFO và Trưởng phòng Vận hành để phản biện tính khả thi và chi phí triển khai. Điều này giúp câu trả lời thực tế hơn và tập trung vào hiệu quả vận hành thay vì chỉ “thêm AI cho hiện đại”.

Qua buổi học, tôi nhận ra AI rất hữu ích để brainstorm và phản biện ý tưởng, nhưng người dùng vẫn cần đánh giá tính thực tế, chi phí và độ an toàn trước khi áp dụng vào hệ thống thực tế.

Duongnt-2A202600547
# 📝 Phase 6 — REFLECTION
Nhật ký chiêm nghiệm về việc tương tác với AI (ChatGPT, Gemini, Claude...) trong suốt buổi học.
Vị trí: AI Engineer (Thought-Partnering Session)
Nhìn lại toàn bộ buổi làm việc vừa qua với hệ thống AI, tôi nhận ra một điều cốt lõi: AI chỉ thực sự thông minh khi chúng ta biết cách đặt câu hỏi và đặt ranh giới. Từ một công cụ tra cứu thông thường, AI đã trở thành một "Thought-partner" (bạn đồng hành tư vấn) sắc bén, giúp tôi mổ xẻ các bài toán vận hành phức tạp trong hệ sinh thái Vingroup (Vinfast, Xanh SM, Vinhomes, Vinmec).

Dưới đây là những ghi chép trung thực nhất về hành trình "co-pilot" này.
1. AI Đã Giúp Gì? (The Power of Co-Creation)
Trong buổi học, tôi đã đặt AI vào vai trò một Chuyên gia tư vấn giải pháp kiêm Kỹ sư hệ thống. Tôi không bắt AI viết những đoạn code mẫu chung chung, mà ép nó phải tham gia vào quá trình cấu trúc tư duy (Frameworking).
- Brainstorm quy trình & Khơi thông Pain Point: AI đã hỗ trợ tôi quét nhanh qua các mảng vận hành của Vingroup. Điển hình là việc bóc tách các điểm nghẽn y tế tại Vinmec (rò rỉ hiệu suất phòng mổ, đối soát bảo hiểm) và chuyển dịch kịch bản ứng phó hỏa hoạn tại Vinhomes từ "kinh nghiệm thủ công" sang "hệ thống AI Agent chủ động".
- Cấu trúc hóa thông tin (Framing): AI đã giúp tôi chuẩn hóa các ý tưởng rời rạc thành các định dạng chuẩn trong quản trị dự án như List bài toán (Subsidiary/Lens/Mô tả), điền cấu trúc chuyên sâu Problem Statement (6-field) và đóng gói thành mô hình Quick Problem Card tiện lợi.
- Thiết kế kiến trúc dòng chảy (Future-State Flow): AI đóng vai trò như một Software Architect khi cùng tôi phân định rõ ràng các ranh giới: bước nào LLM xử lý (AI Step), bước nào con người cần can thiệp (Human Step - HITL) và thiết kế hệ thống dự phòng (Fallback) khi mất kết nối.
2. AI Đã Sai Gì? (The Hallucination & Complexity Trap)
Dù đưa ra các ý tưởng rất nhanh, AI vẫn bộc lộ những điểm yếu chí mạng của một "trí tuệ nhân tạo" nếu không có sự giám sát của con người:
- Bẫy giải pháp quá phức tạp (Over-engineering): Ở những lượt prompt đầu tiên về kịch bản thiên tai/hỏa hoạn, AI có xu hướng "vơ đũa cả nắm" khi nhồi nhét quá nhiều công nghệ nặng nề (Computer Vision, Graph Neural Networks, LLM Agent) vào từng phần nhỏ lẻ, chia thành 5 bài toán rời rạc. Điều này làm phân tán nguồn lực và không thực tế về mặt hạ tầng dữ liệu.
- Ảo tưởng về bối cảnh (Contextual Hallucination): Khi yêu cầu mô tả bài toán theo phong cách thực tế (bằng rule/kinh nghiệm truyền thống), AI đôi khi bị "lậm" sang việc mô tả các công nghệ quá lý tưởng, quên mất cốt lõi của đề bài là phải chỉ ra nỗi đau của sự thủ công và rò rỉ hiệu suất trước khi đưa ra giải pháp.
3. Sửa Đổi Ra Sao? (The Art of Prompt Engineering)
Để "nắn" AI đi đúng hướng và ép nó trả về kết quả chính xác theo ý đồ của mình, tôi đã áp dụng 3 kỹ thuật điều chỉnh Prompt:
- Kỹ thuật Gộp và Gom cụm (Context Consolidation): Khi thấy AI chia nhỏ giải pháp hỏa hoạn thành 5 phần rời rạc, tôi đã dùng lệnh: "Không chia thành 5 phần mà gộp chung nó lại thành 1 bài toán tổng thể". Điều này ép AI phải nhìn nhận hệ thống dưới dạng một Suite giải pháp đa mô hình (Multi-agent), có tính liên kết chặt chẽ thay vì các tính năng AI đơn lẻ.
- Thiết lập Ranh giới vận hành (Operational Boundary): Tôi chủ động ép AI phải định nghĩa rõ trường thông tin: AI TUYỆT ĐỐI KHÔNG ĐƯỢC LÀM GÌ. Bước này giúp tôi kiểm soát được rủi ro của mô hình AI, đảm bảo quyền quyết định tối cao luôn thuộc về con người (Human-in-the-loop) trong các tình huống khẩn cấp.

Bài học rút ra
AI là một người cộng sự có biên độ sáng tạo vô hạn nhưng biên độ logic có giới hạn. Nó giống như một dòng nước lũ, nếu không có "đê điều" (là các câu lệnh Prompt có cấu trúc, các ràng buộc Boundary và các mẫu Few-shot), nó sẽ tràn lan và tạo ra những kết quả mơ hồ. Nhưng khi được định hướng đúng, nó sẽ trở thành một nguồn trợ lực khổng lồ giúp tăng tốc tư duy của người kỹ sư gấp nhiều lần.