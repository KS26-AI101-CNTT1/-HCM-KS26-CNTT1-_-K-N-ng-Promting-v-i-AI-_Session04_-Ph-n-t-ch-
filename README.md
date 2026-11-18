Đề bài / Yêu cầu

So sánh Trade-off các giải pháp ra lệnh cho Kỹ thuật Prompting Nâng cao (Logic & Chuỗi)

1. Mục tiêu bài tập 

Rèn luyện tư duy phản biện. Sinh viên đề xuất 2 giải pháp viết prompt khác nhau cho chủ đề Kỹ thuật Prompting Nâng cao (Logic & Chuỗi) và so sánh xem phương án nào tối ưu nhất.

2. Bối cảnh & yêu cầu bài toán

Bài toán yêu cầu thực hiện tối ưu hóa quy trình Chain-of-Thought, Prompt Chaining, xử lý đứt gãy.

3. Quy tắc nghiệp vụ

Đưa ra Giải pháp 1 (đơn giản, ngắn gọn) và Giải pháp 2 (chi tiết, có nhiều ràng buộc).

4. Ràng buộc & bẫy dữ liệu

Lập bảng so sánh tiêu chí để đánh giá ưu nhược điểm rõ ràng.

5. Yêu cầu bài làm chi tiết

Bước 1: Đề xuất 2 prompt mẫu

Viết rõ 2 prompt tương ứng với 2 phương án giải quyết.

Bước 1: 2 Prompt mẫu

Giải pháp 1 (Đơn giản):

"Đọc phản hồi và suy nghĩ từng bước: (1) Tóm tắt lỗi, (2) Phân loại Thấp/Cao, (3) Viết câu xin lỗi. Nếu dữ liệu sai thì báo lỗi. Input: [Dữ liệu]"

Giải pháp 2 (Chi tiết, ràng buộc):

"1. Nếu <input> rỗng/rác: Dừng và chỉ xuất {"status": "ERROR"}.

2. Nếu hợp lệ, suy luận trong <thinking>: Tóm tắt lỗi -> Gán HIGH (nếu mất tiền) hoặc LOW -> Viết phản hồi <30 từ.

3. Chỉ xuất JSON: {"status": "OK", "error": "...", "level": "...", "reply": "..."}. <input>[Dữ liệu]</input>"

Bước 2: Lập bảng so sánh Trade-off

Lập bảng so sánh tiêu chí.

Tiêu chí	Giải pháp 1 (Đơn giản)	Giải pháp 2 (Chi tiết)

Độ dễ hiểu	Cao	Trung bình

Tốn token	Ít	Nhiều hơn

Chặn lỗi biên	Trung bình	Cực tốt

Bước 2: Bảng so sánh Trade-off

Tiêu chí	Giải pháp 1 (Đơn giản)	Giải pháp 2 (Chi tiết)

Độ dễ hiểu	Cao	Trung Bình

Tốn token	Ít	Nhiều hơn

Chặn lỗi biên	Trung bình (Dễ bịa thông tin)	Cực tốt (Ngắt luồng ngay lập tức)

Tính ổn định chuỗi	Thấp (Khó tự động hóa)	Cao (Chuẩn JSON, không đứt gãy)

Bước 3: Lựa chọn và chạy thử

Chọn phương án tối ưu nhất, giải thích lý do chọn và chạy thử lấy kết quả.

Bước 3: Lựa chọn & Chạy thử

Chọn: Giải pháp 2.

Lý do: Đảm bảo đầu ra chuẩn JSON để nối chuỗi bước sau và chặn đứng dữ liệu rác gây đứt gãy hệ thống.

Chạy thử:

Input chuẩn ("App trừ tiền 2 lần"): {"status": "OK", "error": "Trừ tiền 2 lần", "level": "HIGH", "reply": "Xin lỗi bạn, chúng tôi sẽ hoàn tiền trong 2h."}

Input lỗi ("@@@ 123"): {"status": "ERROR"}
