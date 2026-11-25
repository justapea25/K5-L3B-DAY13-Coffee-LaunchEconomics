# Báo cáo cá nhân — Trương Văn Hải - 2A202604018

## 1. Thông tin thành viên

- Họ tên: Trương Văn Hải
- MSSV: 2A202604018
- Email: truongvanhai868@gmail.com
- Vai trong nhóm (người viết code, người kiểm số, người gắn nhãn 1, người gắn nhãn 2 kiêm giữ hồ sơ): Người gắn nhãn 1

## 2. Phần việc phụ trách

Người gắn nhãn 1 của nhóm:
- Đọc đề, theo dõi và kiểm soát điều kiện "Xong khi" của từng checkpoint (CP1 – CP5).
- Thực hiện nhiệm vụ C (CP3): Gắn nhãn độc lập 20 ca lỗi từ đề bài theo 5 loại của Google PAIR trong 8 phút.
- Đối chiếu nhãn với Người gắn nhãn 2 (Khánh Linh) để tính tỉ lệ đồng thuận, thống nhất nhãn cho các ca lệch và xây dựng quy tắc phân biệt.
- Xây dựng bảng khắc phục cho 5 ca (mỗi loại lỗi một ca) với cơ chế phát hiện đo được qua event có `trace_id`, ngưỡng kích hoạt, tần suất và vai trò phụ trách cụ thể.
- Phối hợp cùng nhóm kiểm tra các điều kiện chất lượng của hồ sơ nhóm (không dùng từ cấm của lab, người phụ trách là một vai trò cụ thể chứ không ghi "cả đội").

## 3. Đóng góp cụ thể

- **Gắn nhãn độc lập 20 ca lỗi tại CP3 (`report/team/bang_loi.md`):**
  - Gắn nhãn độc lập 20 ca lỗi trong 8 phút theo nguyên nhân gốc, không theo chỗ cần sửa, bám sát định nghĩa của Google PAIR:
    - *Do người dùng:* Ca 1, 6, 9, 14.
    - *Hệ thống:* Ca 2, 7, 8, 15, 20.
    - *Ngữ cảnh:* Ca 3, 10, 16, 18.
    - *Giới hạn hệ thống:* Ca 4, 11, 13, 19.
    - *Ngầm:* Ca 5, 12, 17.
- **Tính tỉ lệ đồng thuận và làm rõ các ca không trùng:**
  - Đối chiếu với bộ nhãn độc lập của Người gắn nhãn 2 (Khánh Linh): trùng 18/20 ca, đạt tỉ lệ đồng thuận **90%** (vượt yêu cầu tối thiểu $\ge 80\%$).
  - Thống nhất nhãn và xây dựng quy tắc phân biệt cho 2 ca lệch:
    - *Ca 6 (Do người dùng vs. Ngữ cảnh):* Khách chủ động chọn sai phân loại ban đầu ("Hoàn phí giao trễ" thay vì hàng bị vỡ). Gốc lỗi bắt nguồn từ thao tác chọn sai của người dùng $\rightarrow$ Nhãn thống nhất: **Do người dùng** (khả năng phát hiện nội dung mô tả mâu thuẫn là cơ hội cải thiện thuộc về biện pháp khắc phục).
    - *Ca 8 (Hệ thống vs. Ngầm):* Trợ lý tự bịa ra "Điều 7.2" không có trong chính sách hoàn phí (hallucination). Dù số tiền đúng và khách không báo, sai phạm về trích dẫn quy định đã hiển thị công khai trên giao diện người dùng (sai lệch đã lộ ra) $\rightarrow$ Nhãn thống nhất: **Hệ thống**.
- **Bảng khắc phục cho 5 ca (đủ 5 loại lỗi của Google PAIR):**
  - *Ca 9 (Do người dùng):* Phát hiện qua event `input_validation_failed` kèm `trace_id` (ngưỡng $> 2\%$ yêu cầu/ngày) | Nhận diện mã sàn TMĐT và tra cứu sang mã vận đơn LogiX; nếu không được thì hiển thị hướng dẫn kèm hình ảnh minh họa và giữ nguyên thông tin đã điền | Phụ trách: **PM trợ lý hoàn phí**.
  - *Ca 7 (Hệ thống):* Đối soát tự động mỗi giờ tin nhắn gửi khách "đã hoàn tiền" so với bản ghi sổ cái (HTTP 200) cùng `trace_id` (ngưỡng 0 ca) | Chỉ gửi thông báo khi API sổ cái thành công; lỗi 503 sau 3 lần thử lại thì chuyển trạng thái "đang xử lý" và chuyển tiếp nhân viên | Phụ trách: **Kỹ sư trưởng agent**.
  - *Ca 18 (Ngữ cảnh):* Theo dõi tỉ lệ yêu cầu bị mở lại (`ticket_reopened`) có `trace_id` vì lý do thắc mắc số tiền mà kiểm tra lại thấy đúng chính sách | Mẫu thông báo gửi khách luôn hiển thị chi tiết công thức và từng bước tính toán (ví dụ: Phí giao 30.000 đ × 50% mức trễ = 15.000 đ) | Phụ trách: **Trưởng nhóm CSKH**.
  - *Ca 4 (Giới hạn hệ thống):* Event `handoff_to_staff` kèm `trace_id` với lý do `thieu_du_lieu_doi_tac`, tổng hợp theo ngày | Duy trì cơ chế chuyển tiếp kèm bản tóm tắt tự động thông tin đơn hàng; tạm thời loại trừ chặng đối tác quốc tế ra khỏi phạm vi pilot | Phụ trách: **PM trợ lý hoàn phí**.
  - *Ca 17 (Ngầm):* Kiểm tra mẫu ngẫu nhiên 100 đơn/tuần so với bảng giá hiện hành qua `audit_sample_checked` kèm `trace_id` (ngưỡng cảnh báo $\ge 1\%$ số đơn bị lệch giá) | Tự động làm mới và xóa bộ nhớ đệm (cache invalidation) ngay khi cập nhật bảng giá; bổ sung phiên bản bảng giá áp dụng vào trường metadata của `trace_id` | Phụ trách: **Kế toán trưởng**.
- **Kiểm soát điều kiện "Xong khi":**
  - Rà soát các tiêu chí nghiệm thu của lab: đảm bảo bảng chi phí A2 đủ 9 dòng, các số simulated đều có nhãn, pilot_plan.yaml không còn dấu `?`, toàn bộ các file báo cáo không chứa từ cấm của lab và không có mục nào ghi người phụ trách là "cả đội".

## 4. Bằng chứng

- Commit `7ef7b61` trên nhánh `hai/cp3-bang-loi` (đã merge vào nhánh `main` qua Pull Request #2 commit `826517a`).
- File `report/team/bang_loi.md`: Cột "Nhãn Trương Văn Hải" với đầy đủ 20 nhãn, kết quả đối chiếu 18/20 trùng (90%), mục quy tắc phân biệt ca 6 & ca 8, và bảng khắc phục 5 ca đủ 5 loại.
- Bằng chứng đóng góp cá nhân được ghi nhận đồng bộ tại mục `TruongVanHai-MSSV` trong `TEAM.md`.

## 5. Công cụ AI đã dùng

Antigravity IDE (Gemini agent):
- Dùng để hỗ trợ rà soát 20 tình huống lỗi đối chiếu với hướng dẫn 5 phân loại của Google PAIR, tính toán tỉ lệ đồng thuận, định dạng cấu trúc bảng markdown chuẩn và kiểm tra các điều kiện nghiệm thu.
- Cách tự kiểm tra:
  - Đọc trực tiếp nội dung 20 tình huống từ đề bài `docs/Ngay13_Lab13_De_bai_hoc_vien.docx` trước khi gắn nhãn để đảm bảo phân loại độc lập theo nguyên nhân gốc chứ không theo giải pháp sửa.
  - Tính toán và kiểm tra chéo tỉ lệ đồng thuận: $18 / 20 = 90\% \ge 80\%$.
  - Rà soát tiêu chí đo lường của bảng khắc phục: cả 5 ca đều có event, ngưỡng kích hoạt, tần suất cụ thể và gắn với `trace_id`.
  - Chạy lệnh kiểm tra từ cấm của lab để đảm bảo không vi phạm quy tắc dùng từ (từ cấm, "cả đội").

## 6. Tự đánh giá

Hoàn thành trọn vẹn và đúng hạn vai trò Người gắn nhãn 1:
- Đảm bảo thực hiện quy trình gắn nhãn độc lập nghiêm túc, đạt tỉ lệ đồng thuận cao (90%) với Người gắn nhãn 2.
- Làm rõ được bản chất nguyên nhân gốc ở các tình huống dễ gây nhầm lẫn (ca 6 và ca 8).
- Bảng khắc phục đưa ra giải pháp rõ ràng, đo được bằng telemetry và phân công đúng vai trò phụ trách.
- Điểm cần cải thiện: Trong các phiên đánh giá tiếp theo nên thống nhất sớm tiêu chí phân biệt giữa lỗi hệ thống và lỗi ngầm để nâng cao hơn nữa tính đồng thuận ngay từ vòng đầu.
