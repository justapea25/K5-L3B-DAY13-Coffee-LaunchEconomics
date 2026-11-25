# Báo cáo nhóm

Báo cáo ngắn, tối đa 2 trang. Số liệu chi tiết nằm trong các file hồ sơ; ở đây chỉ dẫn lại con số chính.

## 1. Thông tin nhóm

- Tên nhóm: Coffee
- Lớp: L3B
- Repo: [justapea25/K5-L3B-DAY13-Coffee-LaunchEconomics](https://github.com/justapea25/K5-L3B-DAY13-Coffee-LaunchEconomics), nhánh nộp `main`
- Thành viên: xem `TEAM.md`

## 2. Mục tiêu và cách tiếp cận

Dựng hồ sơ launch v0 cho trợ lý hoàn phí LogiX-VN để hội đồng Gate 2a quyết định có duyệt **kế hoạch pilot** hay không. Hồ sơ trả lời bốn câu: có đáng chạy không, nhân viên có dùng không, khi hỏng thì sao, pilot có ra được quyết định không.

Cách làm: mọi con số tính từ `src/lab13.py` trên hai file CSV giả lập; người kiểm số tính tay độc lập để đối chiếu; mọi số từ cột `_simulated` ghi nhãn `simulated`; hai người gắn nhãn lỗi độc lập trước khi so. Mỗi nhiệm vụ dùng lại số của nhiệm vụ trước (A3 → phạm vi pilot, B → luật dừng và rủi ro, D → hồ sơ).

## 3. Giải pháp

| Nhiệm vụ | Cách làm | File |
| --- | --- | --- |
| A · Chi phí mỗi việc thành công | Hàm `mo_hinh`: tử số cộng token, tool của **mọi** lần chạy (kể cả lỗi) và phút xem lại, làm lại; mẫu số chỉ đếm `thanh_cong`. Tách theo `loai`, cộng chi phí cố định 40 triệu/tháng | [src/lab13.py](../../src/lab13.py), [bang_chi_phi.md](bang_chi_phi.md) |
| B · Bảng độ nhạy | Gọi lại `mo_hinh` cho 9 kịch bản, 1 cặp, giới hạn 1/2/3 lần chạy và xem lại 100% | [bang_chi_phi.md](bang_chi_phi.md) |
| C · Bảng lỗi | Hai người gắn nhãn 20 ca theo 5 loại của Google PAIR, so nhãn, viết quy tắc cho ca lệch, chọn 5 ca khắc phục | [bang_loi.md](bang_loi.md) |
| D · Kế hoạch pilot | Tính cỡ mẫu theo yêu cầu, nhân viên, depot trước rồi mới chọn cách chia; đặt luật dừng theo tỉ lệ hiện tại | [pilot_plan.yaml](pilot_plan.yaml) |
| E · Chỉ số, rủi ro, hồ sơ | Tính thử 3 chỉ số, liệt kê event có `trace_id`, lấy rủi ro từ bảng độ nhạy, ghép thành hồ sơ 7 mục | [chi_so.md](chi_so.md), [ho_so_launch_v0.md](ho_so_launch_v0.md) |

## 4. Kết quả

- **Chi phí:** 4.472 đ mỗi việc thành công [simulated], gấp **16,3 lần** hoá đơn token + tool chia số yêu cầu (274,7 đ). Giờ nhân viên chiếm 92,5% tổng chi phí [simulated].
- **Phạm vi:** chỉ `noi_dia` (2.696 đ = 0,22×) và `hang_nang` (8.221 đ = 0,69×) [simulated]. Loại `quoc_te` (22.515 đ = 1,88×, thành công 27,3%; lần chạy 3 chỉ ok 2,2%) và `doi_tac` (0,85×, điều khoản riêng).
- **Độ nhạy:** số ca làm lại +51,8% · tỉ lệ xem lại +40,7% · lương +23,1%; giá token chỉ +5,6% [simulated]. Xem lại 100% đưa chi phí lên 11.743–12.415 đ = 0,98–1,03× [simulated].
- **Lỗi:** đồng thuận **18/20 (90%)**; 5 ca khắc phục đủ 5 loại, mỗi ca có event, ngưỡng và một vai trò phụ trách.
- **Pilot:** chia theo nhân viên 20 + 20, mức chênh 6 điểm, ≥ 299 yêu cầu/người; power chỉ ~0,64 nếu tác động thật là 5 điểm; 5 luật dừng.
- **Chỉ số trong đợt chạy thử:** 82,83% đóng trong 24 giờ và không mở lại; 27,12% gợi ý bị sửa hoặc bỏ; 4,25% mở lại trong 7 ngày.
- **Đề xuất cuối:** **Go có điều kiện** cho kế hoạch pilot `noi_dia` + `hang_nang`. Chỉ bắt đầu khi đủ 4 điều kiện:

| Điều kiện trước pilot | Người phụ trách | Hoàn tất trước |
| --- | --- | --- |
| Kiểm thử đạt ca 7, 17, 20: ghi sổ cái trước khi thông báo, chống hoàn tiền trùng, dùng đúng bảng giá | Kỹ sư trưởng agent | 04/12/2026 |
| Ghi nhận đủ 13 event, tính được 5 chỉ số, đối soát thông báo với sổ cái | Người kiểm số | 04/12/2026 |
| Phê duyệt thiết kế 20 + 20, ≥ 299 yêu cầu/người, 5 luật dừng, chấp nhận power ~0,64 ở 5 điểm | Giám đốc vận hành LogiX-VN | 04/12/2026 |
| Chốt cách đo phút xem lại, làm lại và điều kiện an toàn trước khi giảm xem lại | Trưởng nhóm CSKH | 04/12/2026 |

- **Tiềm năng nhưng chưa đủ điều kiện bắt đầu:** trong phạm vi pilot, chi phí gồm xử lý thay và cố định ở 45.000 yêu cầu/tháng là 5.217 đ/yêu cầu, thấp hơn 56,5% so với 12.000 đ [simulated]; đây chưa phải tiết kiệm đã chứng minh. Hiện cả 4 điều kiện chưa đạt: ca 7, 17, 20 chưa kiểm thử, event chưa kiểm thử, thiết kế chưa được duyệt; nếu phải xem lại 100% thì lợi thế gần như mất hoặc âm (0,98–1,03× [simulated]). Nếu chưa đạt đủ thì lùi ngày bắt đầu và trình lại Giám đốc vận hành.
- **Kết quả duyệt chéo (hội đồng: nhóm ABCD):** đồng ý **Go có điều kiện**. Hội đồng đồng ý cách xử lý khi khoảng tin cậy chứa 0 (kết luận chưa đủ bằng chứng; power sát trần khoảng 71% với 20 nhân viên mỗi nhánh) và cách quy đổi xem lại 100% sang 12.850–13.466 đ/yêu cầu [simulated]. Hai góp ý nhóm đã sửa trong `pilot_plan.yaml`:
  - Ngưỡng 520 là **mẫu hiệu dụng**; bậc 10 người có trần 500 nên chưa đủ. Luật lệch 2 điểm chuyển sang bậc 20 người, khi mỗi nhánh có ≥ 1.080 ca theo dõi đủ 7 ngày (≥ 54 ca/nhân viên).
  - Mốc hoà vốn thời gian xem lại phụ thuộc thời gian làm lại (4,56 phút nếu làm lại 9 phút; 4,24 phút nếu 15,3 phút). Nhóm ghi trước điều kiện tăng bậc `rollout_gate`: thời gian xem lại đo thật ≤ 4,2 phút/ca.

## 5. Khó khăn và cách xử lý

- **Nhiều người push cùng lúc lên `main`:** có lần push bị từ chối vì người khác vừa đẩy bản mới. Xử lý: mỗi người làm trên nhánh riêng, `fetch` và merge `origin/main` trước khi push; không force-push.
- **Bộ nhãn CP3 lộ sớm:** bộ nhãn của người gắn nhãn 2 được push lên `main` trước khi người gắn nhãn 1 nộp. Bài học: hai người ghi nhãn ra giấy hoặc file riêng và chỉ đưa vào repo cùng lúc sau khi cả hai xong; cột nhãn ban đầu được giữ nguyên sau khi so.
- **Không cách chia nào đủ mẫu cho 5 điểm** với 40 nhân viên (trần 1.000 < 1.251). Xử lý: nâng mức chênh lên 6 điểm và ghi rõ con số bất lợi power ~0,64 trong hồ sơ.
- **Ngưỡng an toàn:** tỉ lệ mở lại hiện tại đã là 3,97% trong phạm vi, ngưỡng tuyệt đối 3% sẽ dừng pilot ngay tuần đầu. Xử lý: so với nhóm đối chứng (+2 điểm) kèm trần 6%.

## 6. Tổng hợp đóng góp

| Thành viên | Vai | Phần chính |
| --- | --- | --- |
| Đậu Hoàng Minh | Người viết code | `src/lab13.py` (A, B, D1), bản đầu `pilot_plan.yaml`, báo cáo nhóm |
| Đặng Minh Thu | Người kiểm số | `bang_chi_phi.md`, `chi_so.md`, kiểm số tay |
| Trương Văn Hải | Người gắn nhãn 1 | Bộ nhãn độc lập, tỉ lệ đồng thuận, bảng khắc phục trong `bang_loi.md` |
| Nguyễn Xuân Khánh Linh | Người gắn nhãn 2, giữ hồ sơ | Bộ nhãn độc lập, `ho_so_launch_v0.md`, hoàn thiện `pilot_plan.yaml` (theo dõi, 5 luật dừng) |

Chi tiết đóng góp của từng thành viên nằm trong `TEAM.md` và báo cáo cá nhân.

## 7. Hạn chế và hướng cải thiện

- Cả 4 điều kiện trước pilot đều chưa đạt, nên lịch bắt đầu 07/12/2026 phụ thuộc kết quả kiểm thử và phê duyệt. Cải thiện: kiểm thử ca 7, 17, 20 và 13 event trước ngày kiểm tra; không đạt thì lùi ngày bắt đầu và trình lại Giám đốc vận hành.
- Chi phí xem lại và làm lại dựa trên phút **simulated**; tuần đầu pilot phải thay bằng phút đo thật từ `staff_review_decision` và `staff_rework_completed`.
- Đợt chạy thử không có nhóm đối chứng, nên 82,83% chỉ là mức đo được, chưa phải tác động của trợ lý.
- Power ~0,64 ở mức chênh 5 điểm: pilot có thể bỏ sót tác động nhỏ. Cải thiện bằng cách tăng số nhân viên tham gia hoặc kéo dài thời gian thu mẫu.
- Mở lại trong 7 ngày chỉ bắt được lỗi khách nhận ra; lỗi ngầm (ca 5, 17) cần kiểm tra mẫu hằng tuần.
- Ngày bắt đầu và mốc rà soát là đề xuất của nhóm, cần Giám đốc vận hành chốt.

## 8. Tài liệu tham khảo

- Erol và cộng sự, *Cost-of-Pass: An Economic Framework for Evaluating Language Models*, [arxiv.org/abs/2504.13359](https://arxiv.org/abs/2504.13359)
- Google PAIR, *People + AI Guidebook*, chương "Errors + Graceful Failure", [pair.withgoogle.com](https://pair.withgoogle.com)
- Tài liệu statsmodels, `NormalIndPower` và `proportion_effectsize`
- Đề bài và hướng dẫn Lab 13 trong [docs/](../../docs/)
