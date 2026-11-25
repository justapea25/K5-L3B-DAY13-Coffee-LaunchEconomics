# Hồ sơ launch v0 · Trợ lý hoàn phí LogiX-VN · Gate 2a

Nhóm Coffee · Lớp L3B · Bản rà soát trước duyệt chéo

| Mục | Con số chính | Trạng thái | Người phụ trách |
| --- | --- | --- | --- |
| 1 · Chi phí mỗi việc thành công | **4.472 đ** trên toàn mẫu và **3.414 đ** trong phạm vi nội địa + hàng nặng, chưa cộng cố định (`simulated`). Trong phạm vi này, tổng **3.072.513 đ** chia cho **900** việc thành công (`simulated`). | Giả lập | Người viết code |
| 2 · Ba yếu tố nhạy nhất | Trên toàn mẫu, gấp đôi số ca làm lại **+51,8%**, gấp đôi tỉ lệ xem lại **+40,7%**, tăng lương 25% **+23,1%** (`simulated`). | Giả lập | Người kiểm số |
| 3 · So với nhân viên tự làm | Mốc **12.000 đ/yêu cầu**. Nội địa + hàng nặng đạt **4.131 đ/yêu cầu** gồm xử lý thay, hoặc **5.217 đ/yêu cầu** gồm cả cố định ở quy mô toàn hệ thống **45.000 yêu cầu/tháng**, tiết kiệm dự kiến **56,5%** (`simulated`). Loại quốc tế (**22.515 đ/việc thành công**, `simulated`, thành công **27,3%**) và đối tác (**10.215 đ/việc thành công**, `simulated`, có điều khoản riêng). | Giả lập | PM trợ lý hoàn phí |
| 4 · Chỉ số chính, chỉ số dùng, chỉ số an toàn | Đợt chạy thử ghi nhận **82,83%** đóng trong 24 giờ và không mở lại trong 7 ngày (994/1.200), **27,12%** gợi ý bị sửa hoặc bỏ (48/177), **4,25%** mở lại trong 7 ngày (51/1.200). Tỉ lệ mở lại là chỉ số đại diện cho một phần lỗi lọt đến khách. [Đặc tả 5 chỉ số và 13 event](chi_so.md) đã hoàn thành trên tài liệu, triển khai và kiểm thử trong pilot là bước riêng. | Xong, có bằng chứng | Người kiểm số |
| 5 · Bảng lỗi và cách khắc phục | Hai bộ nhãn độc lập trùng **18/20 (90%)**, đạt ngưỡng **80%**. Nhóm đã thống nhất ca **6, 8** và chọn **5** ca khắc phục, mỗi loại một ca. Ưu tiên kiểm thử ca **7** (báo hoàn thành dù sổ cái lỗi), **17** (bảng giá cũ gây hoàn sai) và **20** (hoàn trùng). [Bảng CP3](bang_loi.md) | Xong, có bằng chứng | Người gắn nhãn 2 kiêm giữ hồ sơ |
| 6 · Pilot plan | Ngẫu nhiên theo nhân viên **20 + 20**, đối chứng cùng kỳ. **299 yêu cầu/người** × **20** = **5.980 thực tế/nhóm**, tương đương **859,2 hiệu dụng/nhóm**. Power **80%** ở chênh lệch **6 điểm %**, khoảng **64%** ở **5 điểm %**. [Kế hoạch pilot](pilot_plan.yaml) có cửa sổ theo dõi, phân tích theo cụm và **5 luật dừng**. Chờ Giám đốc vận hành duyệt. | Chưa | Giám đốc vận hành LogiX-VN |
| 7 · Rủi ro kinh tế | Gấp đôi ca làm lại đưa chi phí toàn mẫu lên **6.787 đ/việc thành công** (`simulated`). Xem lại 100% trong phạm vi pilot đưa CPS lên **11.743–12.415 đ** (`simulated`, chưa gồm xử lý thay và cố định). Đo phút xem lại thật với mốc B4 **4,8–5,1 phút** (`simulated`), giảm tỉ lệ theo bậc khi đạt điều kiện an toàn và so chi phí cả hệ thống khi giới hạn **2 lần chạy**. [Rủi ro và hành động](chi_so.md#e2--rủi-ro-kinh-tế) | Giả lập | PM trợ lý hoàn phí |

<details>
<summary>Cách đối chiếu số</summary>

- Từ [CSV lần chạy](../../src/logix_runs.csv), cộng `(26 × token vào + 130 × token ra) / 1.000 + 15 × số lần gọi tool` cho mọi lần chạy. Từ [CSV yêu cầu](../../src/logix_requests.csv), cộng 2.000 đ cho mỗi phút ở hai cột `_simulated`. Toàn mẫu được 4.373.585,13 đ chia 978 việc thành công (`simulated`).
- Mục 3 dùng cùng đơn vị đ/yêu cầu. Phần vận hành gồm xử lý thay là `(3.072.513,274 + 82 × 12.000) / 982 ≈ 4.131 đ/yêu cầu` (`simulated`). Phần cố định là `40.000.000 / (45.000 × 982 / 1.200) ≈ 1.086 đ/yêu cầu`. Cộng hai phần rồi tính `1 − 5.217 / 12.000 ≈ 56,5%` (`simulated`). Bảng A4 dùng mẫu số việc thành công nên phần cố định là `40.000.000 / (45.000 × 900 / 1.200) ≈ 1.185 đ/việc thành công`.
- Với B4, `(224.513,274 + 948 × 5 × 2.000 + 48 × phút làm lại × 2.000) / 900`. Dùng 9 phút theo đề và 15,3 phút là trung bình đã làm tròn từ toàn mẫu (`simulated`). Xem [bảng A/B](bang_chi_phi.md#b4--nếu-phải-xem-lại-tất-cả) và [công thức của lab](../../docs/du_lieu_va_cong_thuc.md).

</details>

**Đề xuất · No-go tại lần rà soát này.** CP3 đã đạt **90%** đồng thuận và có **5** phương án khắc phục. Để quay lại Gate 2a cho nội địa + hàng nặng, Kỹ sư trưởng agent kiểm thử ca **7, 17 và 20** để xác nhận trợ lý báo hoàn tất sau khi ghi sổ, áp dụng đúng phiên bản bảng giá và ghi sổ tối đa **1** giao dịch cho mỗi khoản hoàn được phép. Người kiểm số xác nhận tính được **3** chỉ số bắt buộc từ trace kiểm thử. Giám đốc vận hành phê duyệt thiết kế **20 + 20**, tối thiểu **299 yêu cầu/người**, **5** luật dừng và chấp nhận power khoảng **64%** ở mức chênh **5 điểm %**. Trưởng nhóm CSKH chốt cách đo phút xem lại và tiêu chí an toàn trước khi giảm tỉ lệ xem lại. Nhóm xác nhận ngày kiểm tra từng điều kiện khi chốt lịch.
