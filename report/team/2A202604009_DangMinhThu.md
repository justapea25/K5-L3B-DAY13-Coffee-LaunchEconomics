# Báo cáo cá nhân — Đặng Minh Thu - 2A202604009

## 1. Thông tin thành viên

- Họ tên: Đặng Minh Thu
- MSSV: 2A202604009
- Email: 26ai.thudm@vinuni.edu.vn
- Vai trong nhóm (người viết code, người kiểm số, người gắn nhãn 1, người gắn nhãn 2 kiêm giữ hồ sơ): Người kiểm số

## 2. Phần việc phụ trách

Người kiểm số của nhóm:
- Tính tay một con số để đối chiếu với code.
- Điền bảng A2, A3, A4, B1–B4 trong `report/team/bang_chi_phi.md`.
- Tính ba chỉ số, danh sách event và rủi ro kinh tế trong `report/team/chi_so.md`.

## 3. Đóng góp cụ thể

- `bang_chi_phi.md`: điền A1, A2, A3, A4, B1–B4 (mọi số tính từ cột `_simulated` đều ghi nhãn simulated).
  - A2: chi phí mỗi việc thành công 4.472 đ, gấp 16,3 lần hoá đơn token + tool chia số yêu cầu; làm lại chiếm 51,8% và xem lại chiếm 40,7% tổng chi phí.
  - A3: `quoc_te` tốn 22.515 đ (1,88× nhân viên tự làm) nên không đáng xử lý; chạy lại không giúp (tỉ lệ ok 30,0% → 11,4% → 2,2%).
  - A4: cộng chi phí cố định, 4.599 đ (0,38×) ở 45.000 yêu cầu/tháng và 5.784 đ (0,48×) ở một nửa khối lượng.
  - B1–B4: xếp hạng yếu tố mạnh nhất là làm lại (+51,8%), xem lại (+40,7%), lương (+23,1%); giới hạn 2 lần rẻ nhất cho công ty; xem lại 100% ra 11.743 đ (0,98×), hoặc 12.415 đ (1,03×) nếu làm lại 15,3 phút.
- Kiểm số tay (mục cuối `bang_chi_phi.md`): 5.600 lần gọi tool × 15 đ = 84.000 đ; token của 3 lần chạy đầu = 506,6 đ; tổng 4.373.585 đ ÷ 978 = 4.472 đ.
- `chi_so.md`: chỉ số chính 82,83%, bỏ qua gợi ý 27,12%, lỗi lọt đến khách 4,25%; 9 event có `trace_id`; 4 dòng rủi ro kinh tế lấy số từ bảng độ nhạy.
- Đối chiếu số của nhóm với `src/lab13.py` của người viết code: khớp toàn bộ A2, A3, A4, B1–B4; một chỗ lệch 1 đ ở B4 (12.414 đ → 12.415 đ) đã sửa theo code.

## 4. Bằng chứng

- File `report/team/bang_chi_phi.md` (có mục "Kiểm số tay" ở cuối) và `report/team/chi_so.md`.
- Commit trên nhánh `minhthu`, đã merge `origin/main` để có `lab13.py` của người viết code.
- Số tính độc lập từ `logix_runs.csv` và `logix_requests.csv`, rồi đối chiếu với kết quả `python lab13.py`.

## 5. Công cụ AI đã dùng

Claude Code, dùng để viết script tính độc lập từ hai file CSV và soạn nháp hai file báo cáo. Cách tự kiểm tra:
- Cộng tay tool, token và tổng chi phí.
- Đối chiếu từng bảng với kết quả `lab13.py` của người viết code.
- Kiểm tra mỗi dòng "giảm một nửa" bằng nửa dòng "gấp đôi".
- Rà từ cấm của lab trong các file báo cáo.

## 6. Tự đánh giá

Hoàn thành phần việc người kiểm số: bảng chi phí, chỉ số, event và rủi ro đã đủ, số khớp với code (4.472 đ và 4.373.585 đ). Còn hạn chế: hai chỉ số tự đề xuất và danh sách event là bản đề xuất của riêng tôi, chưa được cả nhóm xem lại.
