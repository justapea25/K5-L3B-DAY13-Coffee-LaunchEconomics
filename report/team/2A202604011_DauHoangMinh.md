# Báo cáo cá nhân — Đậu Hoàng Minh - 2A202604011

## 1. Thông tin thành viên

- Họ tên: Đậu Hoàng Minh
- MSSV: 2A202604011
- Email: 26ai.minhdh4@vinuni.edu.vn
- Vai trong nhóm (người viết code, người kiểm số, người gắn nhãn 1, người gắn nhãn 2 kiêm giữ hồ sơ): Người viết code (CP1, CP2, CP4)

## 2. Phần việc phụ trách

Người viết code: viết `src/lab13.py` cho nhiệm vụ A (mô hình chi phí), B (bảng độ nhạy) và D1 (cỡ mẫu); điền `report/team/pilot_plan.yaml` (nhiệm vụ D). Chia sẻ output của code cho người kiểm số (`bang_chi_phi.md`, `chi_so.md`) và người giữ hồ sơ (`ho_so_launch_v0.md`).

## 3. Đóng góp cụ thể

- **A1:** ba hàm `so_lan_chay_ky_vong`, `ti_le_thanh_cong`, `he_so_chi_phi_moi_viec_thanh_cong`; ba phép thử in ĐẠT (1,20 · 1,25 · 1,25).
- **A2:** hàm `mo_hinh` tính tử số trên mọi lần chạy, kể cả lần lỗi, và mẫu số chỉ đếm `ket_qua == 'thanh_cong'`. Kết quả: 4.373.585 đ ÷ 978 = **4.472 đ** mỗi việc thành công [simulated], gấp **16,3 lần** hoá đơn token + tool chia số yêu cầu (274,7 đ).
- **A3, A4:** tách theo `loai` (quoc_te 22.515 đ = 1,88× [simulated], tỉ lệ ok lần 1 → 3 chỉ còn 30,0% → 2,2%); cộng chi phí cố định 40 triệu/tháng cho phạm vi noi_dia + hang_nang: **4.599 đ = 0,38×** ở 45.000 yêu cầu/tháng [simulated].
- **B1–B4:** 9 kịch bản độ nhạy, xếp hạng làm lại +51,8% · xem lại +40,7% · lương +23,1% [simulated]; giới hạn 2 lần chạy rẻ nhất cho cả hệ thống (6.901.220 đ); xem lại 100% đưa chi phí lên 11.743 đ = 0,98× (12.415 đ = 1,03× với 15,3 phút làm lại) [simulated].
- **D1:** hàm `co_mau` và `m_toi_thieu`: 1.251 · 3.103 (42 người/nhóm, không đủ) · trần 1.000 · trần 300 · m ≥ 299 với mức chênh 6 điểm; power còn 0,64 nếu tác động thật chỉ 5 điểm.
- **D:** `pilot_plan.yaml`: chia theo nhân viên 20 + 20, phạm vi noi_dia + hang_nang, mde 0,06 (đánh đổi ghi rõ), ba luật dừng đủ NẾU – TRONG – THÌ – KHÔNG THÌ; ngưỡng an toàn đặt theo tỉ lệ mở lại hiện tại 3,97% trong phạm vi (không dùng ngưỡng tuyệt đối 3% vì sẽ dừng ngay tuần đầu).

## 4. Bằng chứng

- Commit `9c0d4e4` (nhánh `minh/cp1-cp2-cp4`, đã merge vào `main` ở `25ef289`): `src/lab13.py`, `report/team/pilot_plan.yaml`.
- `cd src && python lab13.py` in đủ A1–A4, B1–B4, D1 và tỉ lệ mở lại dùng cho luật dừng.
- `yaml.safe_load` đọc được `pilot_plan.yaml`; `grep -v '^ *#' pilot_plan.yaml | grep '?'` không in gì.

## 5. Công cụ AI đã dùng

Claude Code: đọc đề và hướng dẫn trong `docs/`, gợi ý và viết code `lab13.py`, soạn nháp `pilot_plan.yaml`. Tự kiểm tra: chạy ba phép thử A1; đối chiếu từng số A2, A3, B1, B3, B4, D1 với số tự kiểm trong `docs/Lab13_Huong_dan_chi_tiet_buoi_chieu.md` (lệch 0%); kiểm "giảm một nửa" bằng nửa "gấp đôi" (5,6 → 2,8; 40,7 → 20,3); người kiểm số (Minh Thu) tính tay độc lập ra cùng 84.000 đ tool và 4.472 đ; kiểm tra file YAML và từ cấm "production".

## 6. Tự đánh giá

Hoàn thành phần code A, B, D1 và kế hoạch pilot; mọi số khớp đáp án đối chiếu. Giải thích được vì sao tử số tính mọi lần chạy còn mẫu số chỉ đếm việc thành công, và vì sao 20 cụm mỗi nhóm chỉ cho tối đa 1.000 mẫu hiệu dụng (c ÷ ICC). Điểm cần cải thiện: chốt các mốc ngày trong pilot với cả nhóm sớm hơn thay vì tự đặt.
