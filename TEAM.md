# Team

## Thông tin nhóm

- Tên nhóm: Coffee
- Lớp: L3B
- Repo nhóm: `K5-L3B-DAY13-Coffee-LaunchEconomics` (xem [SUBMISSION.md](SUBMISSION.md))
- URL repo, nhánh nộp, commit chốt: https://github.com/justapea25/K5-L3B-DAY13-Coffee-LaunchEconomics · nhánh `main` · commit chốt nội dung `a9f0086` (commit cuối trên `main` trước hạn là bản nộp)

## Thành viên

| STT | Họ tên | MSSV | Email | GitHub | Vai trò |
| --: | ------ | ---- | ----- | ------ | ------- |
|   1 | Đậu Hoàng Minh | 2A202604011 | 26ai.minhdh4@vinuni.edu.vn | justapea25 | Người viết code |
|   2 | Đặng Minh Thu | 2A202604009 | 26ai.thudm@vinuni.edu.vn | minhthu27 | Người kiểm số, viết code từ CP3 |
|   3 | Trương Văn Hải | 2A202604018 | truongvanhai868@gmail.com | haihai868 | Người gắn nhãn 1 |
|   4 | Nguyễn Xuân Khánh Linh | 2A202603801 | 26ai.linhnxk2@vinuni.edu.vn | linkiewinkie | Người gắn nhãn 2 kiêm giữ hồ sơ |

Bốn vai của lab:

- **Người viết code:** viết và chạy `src/lab13.py`.
- **Người kiểm số:** tính tay một con số để đối chiếu, điền bảng.
- **Người gắn nhãn 1:** đọc đề, theo dõi điều kiện "Xong khi"; gắn nhãn 20 ca độc lập ở CP3.
- **Người gắn nhãn 2, kiêm giữ hồ sơ:** điền `report/team/ho_so_launch_v0.md` từ đầu buổi; gắn nhãn 20 ca độc lập ở CP3.

Đổi người viết code sau giờ giải lao, để ít nhất hai người trong nhóm tự tay tính được chi phí.

## Cá nhân

Mỗi thành viên đồng thời tạo một báo cáo riêng trong `report/` theo dạng:

```text
report/team/MSSV_HoTen.md
```

Ví dụ: `report/team/20241234_NguyenVanAn.md`.

Sao chép mục dưới đây cho từng thành viên.

## DauHoangMinh-2A202604011

### Phần việc phụ trách

- Người viết code: `src/lab13.py` (nhiệm vụ A, B, D1) và bản đầu `report/team/pilot_plan.yaml` (nhiệm vụ D); báo cáo nhóm.

### Đóng góp cụ thể

- Ba hàm A1 (ĐẠT 1,20 · 1,25 · 1,25), `mo_hinh`, A2–A4, B1–B4, cỡ mẫu D1 (1.251 · 3.103 · 1.000 · 300 · m ≥ 299).
- `pilot_plan.yaml`: chia theo nhân viên 20 + 20, mde 0,06, phạm vi noi_dia + hang_nang, ba luật dừng đầu tiên.
- `report/team/group_report.md`, phần thông tin nhóm trong `TEAM.md`, `report/team/phieu_cham.md` (chấm nhóm ABCD), cập nhật luật dừng và điều kiện tăng bậc trong `pilot_plan.yaml` theo góp ý của hội đồng.

### Bằng chứng

- Commit `9c0d4e4`, `ce22d69`, `903377d`, `e221624`, `d633a22`; báo cáo cá nhân `report/team/2A202604011_DauHoangMinh.md`.

## DangMinhThu-2A202604009

### Phần việc phụ trách

- Người kiểm số: điền bảng chi phí, đặc tả chỉ số, kiểm số tay.

### Đóng góp cụ thể

- `report/team/bang_chi_phi.md`: A1–A4, B1–B4, mục "Kiểm số tay" (84.000 đ tool, 4.472 đ mỗi việc thành công).
- `report/team/chi_so.md`: 3 chỉ số tính thử (82,83% · 27,12% · 4,25%), danh sách event có `trace_id`, các dòng rủi ro kinh tế.

### Bằng chứng

- Commit `f13e1dd`, `20d0c72`, `12a6a77`; báo cáo cá nhân `report/team/2A202604009_DangMinhThu.md`.

## TruongVanHai-2A202604018

### Phần việc phụ trách

- Người gắn nhãn 1: gắn nhãn độc lập 20 ca lỗi ở CP3.

### Đóng góp cụ thể

- Bộ nhãn độc lập trong `report/team/bang_loi.md`, tỉ lệ đồng thuận 18/20 (90%), quy tắc phân biệt ca 6 và ca 8, bảng khắc phục 5 ca đủ năm loại.

### Bằng chứng

- Commit `7ef7b61` (PR #2 `hai/cp3-bang-loi`); báo cáo cá nhân `report/team/2A202604018_TruongVanHai.md` (commit `1e470f5`).

## NguyenXuanKhanhLinh-2A202603801

### Phần việc phụ trách

- Người gắn nhãn 2 kiêm giữ hồ sơ: gắn nhãn độc lập 20 ca lỗi, điền hồ sơ launch v0.

### Đóng góp cụ thể

- Bộ nhãn độc lập và 20 tình huống trong `report/team/bang_loi.md`; điền tên và vai trong `TEAM.md`.
- `report/team/ho_so_launch_v0.md`: bảy mục và đề xuất cuối Go có điều kiện, mỗi điều kiện có người phụ trách và hạn 04/12/2026.
- Hoàn thiện `report/team/pilot_plan.yaml` (phần theo dõi, năm luật dừng); rà và đồng bộ số trong `bang_chi_phi.md`, `chi_so.md`.

### Bằng chứng

- Commit `c5de251`, `7b46552`, `2887a0d`, `b026973`, `b26c4df`, `b9b84ca`; báo cáo cá nhân `report/team/2A202603801_NguyenXuanKhanhLinh.md` (commit `128b6a6`, `bf193d4`).
