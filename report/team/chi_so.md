# Đặc tả chỉ số, event và rủi ro kinh tế · Nhiệm vụ E1, E2

## E1 · Đặc tả chỉ số

| Loại | Chỉ số | Công thức từ event trong pilot | Tính thử trên 1.200 yêu cầu |
| --- | --- | --- | --- |
| Chính (kết quả) | % yêu cầu đóng trong 24 giờ và không mở lại trong 7 ngày | Trong các yêu cầu được tuyển đã qua 8 × 24 giờ kể từ lúc tạo, đếm ca đóng lần đầu trong 24 giờ và không mở lại trong 7 ngày kể từ lần đóng đó, chia tổng số yêu cầu đủ thời gian theo dõi. | **82,83%** (994/1.200) |
| Dùng | % gợi ý bị sửa hoặc bỏ | Đếm yêu cầu có quyết định xem lại cuối cùng là `sua` hoặc `bo`, chia số yêu cầu có quyết định xem lại trong tuần. | **27,12%** (48/177, gồm 41 sửa và 7 bỏ) |
| An toàn | Tỉ lệ mở lại trong 7 ngày, chỉ số đại diện lỗi lọt đến khách | Theo cửa sổ đóng đã đủ 7 ngày quan sát, đếm yêu cầu mở lại trong vòng 7 ngày từ lần đóng đầu, chia số yêu cầu đã đóng đủ thời gian theo dõi. Theo dõi riêng ca chưa đóng hoặc đang theo dõi. | **4,25%** (51/1.200 yêu cầu CSV, theo mẫu số của bài lab) |
| Dùng | % yêu cầu nhân viên can thiệp mở bằng trợ lý mỗi tuần | Trong số yêu cầu đủ phạm vi được phân lần đầu cho nhóm can thiệp trong tuần, đếm yêu cầu có `agent_opened` trong cùng tuần từ nhân viên thuộc nhóm, chia số yêu cầu nhóm này được phân. | Đo trong pilot |
| An toàn | % giao dịch hoàn sai tiền trong mẫu hằng tuần | Đếm giao dịch được kiểm có `so_tien_da_hoan` khác `so_tien_dung`, chia tổng số giao dịch trong mẫu. | Đo trong pilot |

Số tính thử từ [CSV yêu cầu](../../src/logix_requests.csv). Dùng cờ `dong_trong_24h` và `mo_lai_trong_7_ngay` cho chỉ số chính, `duoc_xem_lai` và `quyet_dinh_xem_lai` cho chỉ số dùng, `mo_lai_trong_7_ngay` cho chỉ số an toàn. Đây là kết quả mô tả đợt chạy thử. Tỉ lệ mở lại phụ thuộc việc khách phát hiện và báo lỗi. Kiểm mẫu và đối soát sổ cái bổ sung khả năng phát hiện lỗi tài chính ngầm.

## Danh sách event

Mọi event mang `request_id` và `trace_id`. Hệ thống ticket cấp hai mã ngay khi tạo yêu cầu cho cả hai nhóm. Khử trùng theo `request_id` khi đếm yêu cầu, theo `ledger_txn_id` khi đếm giao dịch.

| Event | Ai tạo | Thuộc tính chính | Thời điểm |
| --- | --- | --- | --- |
| `refund_request_created` | Hệ thống ticket | request_id, trace_id, created_at, loai, so_tien | Khi tiếp nhận yêu cầu |
| `refund_request_assigned` | Hệ thống phân việc | request_id, trace_id, assigned_at, staff_id, depot_id, arm | Khi phân cho nhân viên, lấy lần phân đầu cho phân tích |
| `agent_opened` | Giao diện nhân viên | request_id, trace_id, staff_id, opened_at | Khi nhân viên mở trợ lý cho yêu cầu |
| `agent_run_completed` | Agent | request_id, trace_id, attempt, tokens_in, tokens_out, tool_calls, status, completed_at | Sau mỗi lần chạy, kể cả lỗi |
| `agent_suggestion_shown` | Giao diện nhân viên | request_id, trace_id, staff_id, so_tien_de_xuat, shown_at | Khi gợi ý hiện ra |
| `staff_review_decision` | Giao diện nhân viên | request_id, trace_id, staff_id, quyet_dinh (giu/sua/bo), phut_xem_lai, decided_at | Khi lưu quyết định xem lại, ghi phút đo thật |
| `staff_rework_completed` | Giao diện nhân viên | request_id, trace_id, phut_lam_lai, ly_do, completed_at | Khi làm lại xong, ghi phút đo thật |
| `handoff_to_staff` | Agent | request_id, trace_id, reason, tom_tat, handed_off_at | Khi chuyển nhân viên |
| `refund_ledger_write` | Dịch vụ sổ cái | request_id, trace_id, order_id, refund_intent_id, idempotency_key, ledger_txn_id, so_tien, status, posted_at | Sau mỗi lần ghi sổ, phân biệt đã ghi thành công, lỗi và bị chặn do trùng |
| `refund_notification_sent` | Dịch vụ thông báo | request_id, trace_id, refund_intent_id, status, sent_at | Khi gửi trạng thái hoàn tiền cho khách |
| `ticket_closed` | Hệ thống ticket | request_id, trace_id, closed_at | Mỗi lần đóng yêu cầu |
| `ticket_reopened` | Hệ thống ticket | request_id, trace_id, reopened_at, reason | Khi yêu cầu được mở lại |
| `audit_sample_checked` | Kế toán | request_id, trace_id, ledger_txn_id, so_tien_da_hoan, so_tien_dung, price_table_version, checked_at | Kiểm mẫu hằng tuần |

**Đối chiếu 5 chỉ số với event**

- **Kết quả** · Nối `refund_request_created`, lần phân đầu của `refund_request_assigned`, lần đóng đầu của `ticket_closed` và `ticket_reopened`. Dùng `created_at` để xác định mốc 24 giờ và `closed_at` để xác định mốc 7 ngày.
- **Sửa hoặc bỏ gợi ý** · Dùng quyết định cuối ghi bởi `staff_review_decision` cho mỗi yêu cầu, gán tuần theo thời điểm quyết định cuối.
- **Mở lại trong 7 ngày** · Dùng `ticket_closed` đủ theo dõi và `ticket_reopened`, tính theo nhóm của lần phân đầu.
- **Mở trợ lý** · Dùng `refund_request_created` để lọc loại yêu cầu, `refund_request_assigned` để lập mẫu số và `agent_opened` để đếm lần mở thực sự theo yêu cầu.
- **Hoàn sai tiền qua kiểm mẫu** · So hai số tiền trong `audit_sample_checked`, dùng `ledger_txn_id` để đối soát giá trị đã ghi trong `refund_ledger_write`.

Đặc tả trên bao phủ 5 chỉ số. Kiểm thử hai luật an toàn tức thời bằng cách đối soát các event sổ cái và thông báo theo `refund_intent_id`, mã nghiệp vụ dùng chung cho các lần gửi lại cùng một khoản hoàn. Cảnh báo khi có hai giao dịch ghi sổ thành công khác nhau cho cùng mã, hoặc thông báo hoàn thành không có bản ghi thành công trước thời điểm gửi. Trong pilot, dùng phút đo thật từ event xem lại và làm lại để thay dần số `simulated`.

## E2 · Rủi ro kinh tế

Số chi phí lấy từ [bảng A/B](bang_chi_phi.md) và có nhãn `simulated`.

| Rủi ro | Tác động đã tính | Dấu hiệu theo dõi | Hành động | Người phụ trách |
| --- | --- | --- | --- | --- |
| Số ca làm lại tăng gấp đôi | +51,8%, từ 4.472 đ lên 6.787 đ mỗi việc thành công (B1) | Tỉ lệ `lam_lai` theo tuần > 7% (đợt chạy thử: 4,9% trong phạm vi noi_dia + hang_nang) | Thu hẹp về noi_dia, rà 20 trace làm lại | PM trợ lý hoàn phí |
| Phải xem lại 100% kéo dài | 11.743 đ = 0,98× của 12.000 đ (12.415 đ = 1,03× nếu làm lại 15,3 phút như dữ liệu) (B4) | % yêu cầu được xem lại còn > 50% sau bước 0.25 | Đo phút xem lại thật, đối chiếu các mốc B4 là 4,8–5,1 phút. Chỉ giảm theo bậc sau khi tỉ lệ sửa + bỏ < 15%, kiểm mẫu đạt và Giám đốc vận hành xác nhận đạt điều kiện an toàn | Trưởng nhóm CSKH |
| Khối lượng thấp hơn dự kiến | Cố định 40 triệu/tháng: +1.185 đ/việc ở 45.000 yêu cầu/tháng, +2.370 đ/việc nếu còn một nửa; tổng 5.784 đ = 0,48× (A4) | Số việc thành công theo tuần < 50% kế hoạch | Hoãn tăng bậc và tính lại chi phí cố định ở khối lượng thực tế | PM trợ lý hoàn phí |
| Khối lượng xem lại tăng, nhân viên ít chấp nhận gợi ý | Tỉ lệ xem lại gấp đôi: +40,7% (6.292 đ) (B1) | Tỉ lệ xem lại tăng hoặc tỉ lệ sửa + bỏ > 40% (đợt chạy thử 27,12%) | Rà gợi ý bị bỏ theo loại yêu cầu, sửa prompt hoặc thu hẹp phạm vi | Trưởng nhóm CSKH |
