# Bảng lỗi và cách khắc phục · Nhiệm vụ C

## Hai bộ nhãn độc lập

Người gắn nhãn 1 · Trương Văn Hải. Người gắn nhãn 2 · Nguyễn Xuân Khánh Linh. Mỗi người ghi riêng đủ 20 nhãn trong 8 phút rồi mới nhập vào cột của mình và so kết quả.

Chọn nhãn theo nguyên nhân gốc. Mỗi ca dùng một trong năm nhãn sau.

- **Do người dùng** · Người dùng nhập sai hoặc chọn sai.
- **Hệ thống** · Trợ lý trả lời sai hoặc làm sai so với thiết kế hoặc chính sách.
- **Ngữ cảnh** · Trợ lý làm đúng thiết kế nhưng giả định trong thiết kế lệch với hoàn cảnh của người dùng.
- **Giới hạn hệ thống** · Yêu cầu ngoài phạm vi, thiếu dữ liệu cần thiết hoặc có dạng đầu vào chưa hỗ trợ.
- **Ngầm** · Lỗi chưa được người dùng hay hệ thống nhận ra và chỉ lộ khi kiểm tra.

<details>
<summary>20 tình huống trích từ đề bài</summary>

| Ca | Mô tả |
| --: | --- |
| 1 | Khách nhập số tài khoản nhận hoàn tiền thiếu hai chữ số. Trợ lý tạo lệnh hoàn, ngân hàng trả về lỗi. |
| 2 | Kiện nội địa 28 kg. Trợ lý gọi tool tra bảng giá với tham số hàng thường thay vì hàng nặng, hoàn thiếu 45.000 đ. Khách mở lại sau 2 ngày. |
| 3 | Theo thiết kế, trợ lý hoàn tiền về ví LogiX trong 5 phút. Khách chờ tiền về tài khoản ngân hàng và báo “chưa được hoàn”. |
| 4 | Khách yêu cầu hoàn phí cho chặng do hãng nước ngoài giao. LogiX không có dữ liệu chặng này. Trợ lý nói không xác định được trạng thái và chuyển cho nhân viên. |
| 5 | Kiểm tra mẫu cuối tuần thấy 14 đơn có mã giảm giá bị hoàn theo giá trước giảm, thừa trung bình 12.000 đ mỗi đơn. Không khách nào báo, không cảnh báo nào kích. |
| 6 | Khách chọn mục “Hoàn phí giao trễ” nhưng nội dung mô tả hàng bị vỡ. Trợ lý xử lý theo luồng giao trễ và từ chối vì đơn giao đúng hạn. |
| 7 | API sổ cái trả lỗi 503 ở bước ghi hoàn tiền. Trợ lý thử lại 3 lần rồi vẫn báo khách “đã hoàn tiền thành công”. |
| 8 | Trợ lý dẫn “Điều 7.2 chính sách hoàn phí” làm căn cứ. Bản chính sách hiện hành không có điều 7.2. Số tiền hoàn vẫn đúng. |
| 9 | Khách nhập mã đơn của sàn thương mại điện tử thay vì mã vận đơn. Trợ lý báo “mã không hợp lệ” rồi dừng, không gợi ý gì. |
| 10 | Đơn giao trễ do bão. Trợ lý từ chối hoàn theo điều khoản bất khả kháng, đúng chính sách. Khách thấy vô lý vì ứng dụng vẫn hiện “cam kết giao 24 giờ”. |
| 11 | Khách gửi tin nhắn thoại 40 giây. Trợ lý không xử lý được âm thanh, trả lời “vui lòng nhập bằng chữ”. |
| 12 | Tool tra đơn của depot D05 trả thiếu một trường. Trợ lý vẫn ra kết quả đúng sau nhiều lần gọi, nên tiền token của D05 gấp 3 lần depot khác suốt 3 tuần mà không ai thấy. |
| 13 | Khách hỏi hoàn phí bảo hiểm hàng hoá, sản phẩm của công ty bảo hiểm đối tác, ngoài phạm vi trợ lý. Trợ lý trả lời chung chung về phí vận chuyển, không nói rõ là mình không xử lý được. |
| 14 | Khách bấm nhầm “Xác nhận đã nhận tiền” khi chưa nhận. Yêu cầu bị đóng. |
| 15 | Đơn trễ 26 giờ. Chính sách: trễ 24–48 giờ hoàn 50%. Trợ lý tính hoàn 100%. Nhân viên xem lại bắt được trước khi gửi. |
| 16 | Theo thiết kế “gửi ngay khi xong”, trợ lý gửi thông báo hoàn tiền qua Zalo lúc 2:14 sáng. Khách phản ánh bị làm phiền. |
| 17 | Bảng giá đổi từ ngày 01/11 nhưng trợ lý vẫn dùng bản cũ trong bộ nhớ đệm cho đơn dưới 2 kg. Lệch 1.000–2.000 đ mỗi đơn, 212 đơn trong 9 ngày, không ai mở lại. |
| 18 | Trợ lý tính đúng: phí giao 30.000 đ, hoàn 50%. Tin nhắn chỉ ghi “Đã hoàn 15.000 đ”, không kèm cách tính. Khách cho là hoàn thiếu và mở lại yêu cầu. |
| 19 | Khách yêu cầu hoàn phí cho đơn từ 14 tháng trước. Trợ lý chỉ truy cập được dữ liệu 12 tháng. Trợ lý nói rõ không tra được và chuyển cho nhân viên kèm tóm tắt. |
| 20 | Khách gửi lại yêu cầu sau 10 phút vì chưa thấy phản hồi. Trợ lý hoàn hai lần cho cùng một đơn vì lệnh thứ hai không có khoá chống trùng. |

Nguồn [Đề bài Lab 13, mục Hai mươi ca lỗi](../../docs/Ngay13_Lab13_De_bai_hoc_vien.docx).

</details>

| Ca | Nhãn Trương Văn Hải | Nhãn Nguyễn Xuân Khánh Linh | Trùng? | Nhãn thống nhất |
| --: | --- | --- | --- | --- |
| 1 | Do người dùng | Do người dùng | Có | Do người dùng |
| 2 | Hệ thống | Hệ thống | Có | Hệ thống |
| 3 | Ngữ cảnh | Ngữ cảnh | Có | Ngữ cảnh |
| 4 | Giới hạn hệ thống | Giới hạn hệ thống | Có | Giới hạn hệ thống |
| 5 | Ngầm | Ngầm | Có | Ngầm |
| 6 | Do người dùng | Ngữ cảnh | Không | Do người dùng |
| 7 | Hệ thống | Hệ thống | Có | Hệ thống |
| 8 | Hệ thống | Ngầm | Không | Hệ thống |
| 9 | Do người dùng | Do người dùng | Có | Do người dùng |
| 10 | Ngữ cảnh | Ngữ cảnh | Có | Ngữ cảnh |
| 11 | Giới hạn hệ thống | Giới hạn hệ thống | Có | Giới hạn hệ thống |
| 12 | Ngầm | Ngầm | Có | Ngầm |
| 13 | Giới hạn hệ thống | Giới hạn hệ thống | Có | Giới hạn hệ thống |
| 14 | Do người dùng | Do người dùng | Có | Do người dùng |
| 15 | Hệ thống | Hệ thống | Có | Hệ thống |
| 16 | Ngữ cảnh | Ngữ cảnh | Có | Ngữ cảnh |
| 17 | Ngầm | Ngầm | Có | Ngầm |
| 18 | Ngữ cảnh | Ngữ cảnh | Có | Ngữ cảnh |
| 19 | Giới hạn hệ thống | Giới hạn hệ thống | Có | Giới hạn hệ thống |
| 20 | Hệ thống | Hệ thống | Có | Hệ thống |

**Tỉ lệ đồng thuận:** 18 / 20 = 90% (đạt yêu cầu $\ge 80\%$).

## Quy tắc phân biệt cho các ca không trùng

Sau khi so sánh và thảo luận, quy tắc phân biệt cho hai ca khác nhãn như sau:

- **Ca 6 (Do người dùng vs. Ngữ cảnh):** Khách chọn sai phân loại ban đầu ("Hoàn phí giao trễ" thay vì hàng bị vỡ). Gốc lỗi trực tiếp bắt nguồn từ thao tác chọn sai của người dùng nên nhãn thống nhất là **Do người dùng**. Việc trợ lý thiếu khả năng phát hiện nội dung mô tả mâu thuẫn để gợi ý lại là cơ hội cải thiện thuộc về giải pháp khắc phục.
- **Ca 8 (Hệ thống vs. Ngầm):** Trợ lý trích dẫn điều khoản không có thật ("Điều 7.2") trong văn bản trả lời khách hàng (hallucination). Dù số tiền hoàn vẫn đúng và khách hàng không phản ánh, nhưng sai phạm về căn cứ pháp lý đã hiển thị công khai trên giao diện người dùng (sai lệch đã lộ ra) chứ không phải ẩn giấu bên trong, nên nhãn thống nhất là **Hệ thống**.

## Bảng khắc phục cho 5 ca, mỗi loại một ca

Mỗi dòng xác định rõ cách phát hiện đo được qua event có `trace_id`, ngưỡng kích hoạt, tần suất giám sát và vai trò cụ thể chịu trách nhiệm.

| Ca | Loại lỗi | Phát hiện bằng gì | Khắc phục thế nào | Ai phụ trách |
| --: | --- | --- | --- | --- |
| 9 | Do người dùng | Event `input_validation_failed` kèm `trace_id`; cảnh báo khi tỉ lệ vượt quá 2% tổng số yêu cầu/ngày. | Nhận diện mã đơn sàn TMĐT và tra cứu sang mã vận đơn LogiX; nếu không tra được thì hiển thị hướng dẫn kèm hình ảnh minh họa vị trí mã vận đơn và giữ nguyên thông tin đã điền. | PM trợ lý hoàn phí |
| 7 | Hệ thống | Đối soát tự động mỗi giờ: phát hiện tin nhắn gửi khách "đã hoàn tiền" nhưng không có bản ghi sổ cái thành công (HTTP 200) cùng `trace_id`; ngưỡng kích hoạt cảnh báo là 0 ca (bất kỳ ca nào lệch). | Chỉ gửi thông báo hoàn tất khi API sổ cái trả mã thành công; nếu API trả lỗi 503 sau 3 lần thử lại, tự động chuyển trạng thái "đang xử lý" và chuyển tiếp nhân viên đối soát. | Kỹ sư trưởng agent |
| 18 | Ngữ cảnh | Tỉ lệ yêu cầu bị mở lại (`ticket_reopened`) có `trace_id` vì khiếu nại số tiền mà kiểm tra lại thấy đúng chính sách; theo dõi hàng tuần. | Mẫu thông báo gửi khách luôn ghi chi tiết công thức và từng bước tính toán (ví dụ: Phí giao 30.000 đ × 50% mức trễ = 15.000 đ hoàn) thay vì chỉ gửi số tiền tổng. | Trưởng nhóm CSKH |
| 4 | Giới hạn hệ thống | Event `handoff_to_staff` kèm `trace_id` với lý do `reason = thieu_du_lieu_doi_tac`, tổng hợp và giám sát theo ngày. | Duy trì cơ chế chuyển tiếp cho nhân viên kèm tóm tắt tự động thông tin đơn hàng; tạm thời loại trừ chặng đối tác quốc tế ra khỏi phạm vi pilot cho đến khi tích hợp API đối tác. | PM trợ lý hoàn phí |
| 17 | Ngầm | Kiểm tra mẫu ngẫu nhiên 100 đơn/tuần so với bảng giá hiện hành qua `audit_sample_checked` kèm `trace_id`; ngưỡng cảnh báo $\ge 1\%$ số đơn bị lệch giá. | Tự động làm mới và xóa bộ nhớ đệm (cache invalidation) ngay khi có quyết định cập nhật bảng giá; bổ sung phiên bản bảng giá áp dụng vào trường metadata của `trace_id`. | Kế toán trưởng |
