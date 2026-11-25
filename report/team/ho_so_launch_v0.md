# Hồ sơ launch v0 · Trợ lý hoàn phí LogiX-VN · Gate 2a

Nhóm Coffee · Lớp L3B · Bản rà soát 0.4

Phạm vi đề xuất gồm yêu cầu nội địa (`noi_dia`) và hàng nặng (`hang_nang`). Số có nhãn `simulated` dùng dữ liệu giả lập của lab.

| Mục | Con số chính | Trạng thái | Người phụ trách |
| --- | --- | --- | --- |
| 1 · Chi phí mỗi việc thành công | CPS (**chi phí mỗi việc thành công**) toàn mẫu là **4.373.585 đ ÷ 978 ≈ 4.472 đ**. Trong phạm vi pilot là **3.072.513 đ ÷ 900 ≈ 3.414 đ** (`simulated`, chưa cộng cố định). Dự phòng nhân viên xử lý **82/982** yêu cầu trong phạm vi mà trợ lý chưa xử lý thành công. | Giả lập | Người viết code |
| 2 · Ba yếu tố nhạy nhất | Toàn mẫu, gấp đôi ca làm lại đưa CPS lên **6.787 đ (+51,8%)**, gấp đôi tỉ lệ xem lại lên **6.292 đ (+40,7%)**, tăng lương 25% đưa CPS lên **5.506 đ (+23,1%)**. Gấp đôi giá token làm CPS tăng **5,6%**. Kịch bản **2 lần chạy** có tổng chi phí cả hệ thống thấp nhất trên 1.200 yêu cầu, **6.901.220 đ** (`simulated`). [Bảng độ nhạy và B3](bang_chi_phi.md#b3--giới-hạn-chạy-lại-có-thật-sự-rẻ-hơn) | Giả lập | Người kiểm số |
| 3 · So với nhân viên tự làm | Mốc **12.000 đ/yêu cầu**. Chi phí gồm xử lý thay là **4.131 đ/yêu cầu**. Ở quy mô toàn hệ thống **45.000 yêu cầu/tháng**, khoảng **36.825** yêu cầu thuộc phạm vi pilot. Phân bổ cố định thêm **1.086 đ/yêu cầu**, tổng **5.217 đ/yêu cầu**, thấp hơn **56,5%** (`simulated`). Quốc tế nằm ngoài phạm vi vì CPS **22.515 đ** (`simulated`) và thành công **27,3%**. Đối tác có CPS **10.215 đ** (`simulated`) và điều khoản riêng nên cũng nằm ngoài phạm vi. | Giả lập | PM trợ lý hoàn phí |
| 4 · Chỉ số chính, chỉ số dùng, chỉ số an toàn | Mẫu chạy thử ghi nhận **82,83%** đóng trong 24 giờ và không mở lại trong 7 ngày (994/1.200), **27,12%** gợi ý bị sửa hoặc bỏ (48/177) và **4,25%** mở lại trong 7 ngày (51/1.200). Tỉ lệ mở lại phản ánh một phần lỗi lọt đến khách. Đã hoàn thành đặc tả **5 chỉ số và 13 event** có `request_id` và `trace_id`. Cần kiểm thử các event trước pilot. [Đặc tả chỉ số](chi_so.md) | Xong, có bằng chứng | Người kiểm số |
| 5 · Bảng lỗi và cách khắc phục | Hai bộ nhãn độc lập trùng **18/20 (90%)**. Hai ca khác nhau (**6 và 8**) đã có quy tắc thống nhất. Bộ nhãn thống nhất khớp **20/20** với nhãn tham khảo của lab, vượt ngưỡng **16/20** trong rubric C3. Bảng có **5** ca khắc phục, mỗi loại một ca. Ưu tiên kiểm thử ca **7, 17 và 20**. [Bảng CP3](bang_loi.md) · [Nhãn tham khảo](../../docs/Lab13_Huong_dan_chi_tiet_buoi_chieu.md#nhãn-tham-khảo-cho-20-ca) | Xong, có bằng chứng | Người gắn nhãn 2 kiêm giữ hồ sơ |
| 6 · Thiết kế pilot | Ngẫu nhiên theo nhân viên, phân tầng theo depot, **20 dùng trợ lý + 20 đối chứng** cùng kỳ. Thu tối thiểu **299 yêu cầu/người**, tức **5.980 thực tế/nhóm** và **859,2 hiệu dụng/nhóm**. Power **80%** ở chênh lệch **6 điểm %**, khoảng **64%** ở **5 điểm %**. Dự kiến bắt đầu **07/12/2026**, rà soát **11/01/2027**. Chỉ kết luận khi đủ mẫu và đủ cửa sổ **8 ngày**. Trong **5** luật dừng, hoàn trùng và báo hoàn tất trước khi ghi sổ kích hoạt dừng ngay. Chờ Giám đốc vận hành duyệt. [Kế hoạch pilot](pilot_plan.yaml) | Chưa | Giám đốc vận hành LogiX-VN |
| 7 · Rủi ro kinh tế và cách kiểm soát | Gấp đôi ca làm lại đưa CPS toàn mẫu lên **6.787 đ** (`simulated`). Xem lại 100% trong phạm vi pilot đưa CPS lên **11.743 đ** với 9 phút làm lại hoặc **12.415 đ** với 15,3 phút làm lại (`simulated`, chưa gồm xử lý thay và cố định). Khi khối lượng giảm một nửa, cố định tăng từ **1.185 lên 2.370 đ/việc thành công** (`simulated`). Đo phút xem lại thật, tỉ lệ làm lại và chi phí cả hệ thống theo tuần. Chỉ giảm xem lại theo bậc khi đạt điều kiện an toàn. [Rủi ro và hành động](chi_so.md#e2--rủi-ro-kinh-tế) | Giả lập | PM trợ lý hoàn phí |

<details>
<summary>Cách đối chiếu số</summary>

- Từ [CSV lần chạy](../../src/logix_runs.csv), cộng `(26 × token vào + 130 × token ra) / 1.000 + 15 × số lần gọi tool` cho mọi lần chạy. Từ [CSV yêu cầu](../../src/logix_requests.csv), cộng 2.000 đ cho mỗi phút ở hai cột `_simulated`. Toàn mẫu được 4.373.585,13 đ chia 978 việc thành công (`simulated`).
- Mục 3 dùng cùng đơn vị đ/yêu cầu. Phần vận hành gồm xử lý thay là `(3.072.513,274 + 82 × 12.000) / 982 ≈ 4.131 đ/yêu cầu` (`simulated`). Phần cố định là `40.000.000 / (45.000 × 982 / 1.200) ≈ 1.086 đ/yêu cầu`. Cộng hai phần rồi tính `1 − 5.217 / 12.000 ≈ 56,5%` (`simulated`). Bảng A4 dùng mẫu số việc thành công nên phần cố định là `40.000.000 / (45.000 × 900 / 1.200) ≈ 1.185 đ/việc thành công`.
- Với B4, `(224.513,274 + 948 × 5 × 2.000 + 48 × phút làm lại × 2.000) / 900`. Dùng 9 phút theo đề và 15,3 phút là trung bình đã làm tròn từ toàn mẫu (`simulated`). Xem [bảng A/B](bang_chi_phi.md#b4--nếu-phải-xem-lại-tất-cả) và [công thức của lab](../../docs/du_lieu_va_cong_thuc.md).
- **70%** là baseline giả định để thiết kế cỡ mẫu, với MDE **6 điểm %**, alpha **0,05** và ICC **0,02**. **82,83%** là tỉ lệ quan sát trong mẫu chạy thử. Đợt chạy thử chưa có nhóm đối chứng nên các tỉ lệ chỉ mô tả mẫu.
- Cửa sổ **8 ngày** để chấm chỉ số chính gồm 24 giờ kể từ lúc tạo để đóng yêu cầu và 7 ngày theo dõi kể từ lần đóng đầu. Nếu chưa đủ mẫu hoặc chưa đủ thời gian theo dõi vào ngày rà soát, lùi ngày kết luận.

</details>

**Điều kiện bắt buộc trước khi bắt đầu pilot** · Cả 6 điều kiện hiện **chưa đạt**. Ngày kiểm tra là đề xuất, đặt trước ngày dự kiến bắt đầu 07/12/2026. [Tiêu chí đạt trong kế hoạch pilot](pilot_plan.yaml)

| Điều kiện | Đạt khi | Người phụ trách | Ngày kiểm tra |
| --- | --- | --- | --- |
| 1 · Chống hoàn tiền trùng (ca 20) | Gửi lại cùng một khoản hoàn, kể cả đồng thời, chỉ có tối đa **1** giao dịch ghi sổ thành công | Kỹ sư trưởng agent | 03/12/2026 |
| 2 · Ghi sổ trước khi thông báo (ca 7) | Sổ cái lỗi 503 thì không báo hoàn tất và chuyển nhân viên; đối soát có **0** thông báo thiếu bản ghi thành công trước đó | Kỹ sư trưởng agent | 03/12/2026 |
| 3 · Cập nhật bảng giá (ca 17) | Đổi bảng giá thì bộ nhớ đệm được làm mới, **0** ca kiểm thử dùng sai phiên bản | Kế toán trưởng | 03/12/2026 |
| 4 · Event và chỉ số | **13** event có `request_id`, `trace_id`; tính được **5** chỉ số từ trace kiểm thử | Người kiểm số | 03/12/2026 |
| 5 · Cách đo và xem lại | Chốt cách đo phút xem lại, làm lại và điều kiện an toàn trước khi giảm tỉ lệ xem lại | Trưởng nhóm CSKH | 03/12/2026 |
| 6 · Phê duyệt thiết kế | Duyệt **20 + 20**, tối thiểu **299 yêu cầu/người**, **5** luật dừng, rollback; chấp nhận power khoảng **64%** ở chênh lệch **5 điểm %** | Giám đốc vận hành LogiX-VN | 04/12/2026 |

**Vì sao có điều kiện** · Tiềm năng kinh tế: **5.217 đ/yêu cầu**, thấp hơn **56,5%** so với **12.000 đ** (`simulated`), chưa phải mức tiết kiệm đã chứng minh. Bất lợi: xem lại 100% đưa CPS lên **11.743–12.415 đ**, bằng **0,98–1,03×** mốc nhân viên (`simulated`), nên lợi thế có thể mất; xử lý bằng đo phút thật và chỉ giảm xem lại khi đạt điều kiện an toàn. Pilot có thể bỏ sót tác động 5 điểm %. Rủi ro hoàn sai, hoàn trùng được chặn bằng điều kiện 1–3, **5** luật dừng và rollback trong 30 phút.

**Đề xuất · GO CÓ ĐIỀU KIỆN** cho kế hoạch pilot yêu cầu nội địa và hàng nặng: chỉ bắt đầu khi đủ cả **6** điều kiện; thiếu bất kỳ điều kiện nào thì không bắt đầu và quay lại Gate 2a.
