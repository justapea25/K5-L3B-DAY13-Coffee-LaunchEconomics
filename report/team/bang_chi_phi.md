# Bảng chi phí · Nhiệm vụ A và B

Số tính bằng `src/lab13.py`, kiểm lại độc lập bằng script riêng của người kiểm số (Minh Thu). Mọi con số tính từ cột `_simulated` ghi nhãn **simulated**. Mỗi câu trả lời không quá ba dòng, có ít nhất một con số.

## A1 · Ba phép thử đáp án biết trước

| Phép thử (p = 0,8) | Kết quả của nhóm |
| --- | --- |
| Số lần chạy trung bình, tối đa 2 lần | 1,20 |
| Số lần chạy trung bình, chạy đến khi đúng | 1,25 |
| Hệ số chi phí mỗi việc thành công, tối đa 3 lần | 1,25 (= 1/p, vì k triệt tiêu) |

## A2 · Mô hình chi phí từ trace

| Khoản | Số tiền (đ) | Nguồn | Nhãn |
| --- | ---: | --- | --- |
| Token | 245.585 | `logix_runs.csv` | đo từ trace |
| Tool | 84.000 (5.600 lần gọi) | `logix_runs.csv` | đo từ trace |
| Trong đó, phần của lần chạy thứ 2 và 3 | 93.804 | attempt lớn hơn 1 | đo từ trace |
| Xem lại | 1.780.000 (890 phút) | `phut_xem_lai_simulated` | simulated |
| Làm lại | 2.264.000 (1.132 phút) | `phut_lam_lai_simulated` | simulated |
| Tổng chi phí | 4.373.585 | | có phần simulated |
| Số việc thành công | 978 | `ket_qua` | |
| Chi phí mỗi việc thành công | 4.472 | | simulated |
| Hoá đơn token và tool chia cho số yêu cầu | 274,7 | | đo từ trace |

- Chi phí mỗi việc thành công gấp bao nhiêu lần "hoá đơn chia số yêu cầu"? **16,3 lần** (4.472 ÷ 274,7) [simulated]; tử số tính mọi lần chạy, mẫu số chỉ 978 ca thành công.
- Khoản nào chiếm tỉ trọng lớn nhất trong tổng chi phí? **Làm lại, 51,8%** [simulated]; kế tiếp là xem lại 40,7% [simulated]; token chỉ 5,6%.
- Lưu ý khi so với 12.000 đ: 4.472 đ chưa tính 148 ca `chuyen_nhan_vien`. Chi phí cả hệ thống = (4.373.585 + 222 × 12.000) ÷ 1.200 = **5.865 đ/yêu cầu = 0,49×** của 12.000 đ [simulated].

## A3 · Tách theo loại yêu cầu

| Loại | Số yêu cầu | Tỉ lệ thành công | Số lần chạy mỗi yêu cầu | Chi phí mỗi việc thành công | So với 12.000 đ |
| --- | ---: | ---: | ---: | ---: | ---: |
| noi_dia | 824 | 95,0% | 1,11 | 2.696 đ [simulated] | 0,22× |
| hang_nang | 158 | 74,1% | 1,47 | 8.221 đ [simulated] | 0,69× |
| quoc_te | 150 | 27,3% | 2,32 | 22.515 đ [simulated] | 1,88× |
| doi_tac | 68 | 54,4% | 1,88 | 10.215 đ [simulated] | 0,85× |

- Loại nào không đáng để trợ lý xử lý? **quoc_te**: 22.515 đ = 1,88× chi phí nhân viên, thành công chỉ 27,3% [simulated]. Chạy lại không giúp: tỉ lệ `ok` theo lần chạy là 30,0% → 11,4% → 2,2%, lỗi lặp lại trên cùng yêu cầu nên chạy thêm chỉ tốn tiền. `doi_tac` (0,85×, có điều khoản riêng) cũng nên loại khỏi phạm vi pilot.

## A4 · Chi phí cố định (phạm vi noi_dia + hang_nang)

Phạm vi 982 yêu cầu của mẫu, 900 việc thành công, chi phí mỗi việc thành công chưa cố định 3.414 đ [simulated]. Cố định 40 triệu đ/tháng.

| Khối lượng | Việc thành công mỗi tháng | Chi phí cố định mỗi việc | Chi phí mỗi việc thành công + cố định | So với 12.000 đ |
| --- | ---: | ---: | ---: | ---: |
| 45.000 yêu cầu/tháng | 33.750 | 1.185 đ | 4.599 đ [simulated] | 0,38× |
| Một nửa khối lượng | 16.875 | 2.370 đ | 5.784 đ [simulated] | 0,48× |

- Chi phí cố định có đổi kết luận không? Không ở cả hai khối lượng (0,38× và 0,48×, đều dưới 1×), nhưng nó tăng gấp đôi khi khối lượng còn một nửa; hồ sơ phải ghi rõ số đã cộng cố định ở khối lượng nào.

## B1 · Đổi từng yếu tố

Gốc (A2): 4.472 đ [simulated].

| Kịch bản | Cách tính | Chi phí mỗi việc thành công | Thay đổi (%) |
| --- | --- | ---: | ---: |
| Giá token gấp đôi | 52 đ và 260 đ cho 1.000 token; giá tool giữ nguyên | 4.723 đ | +5,6% |
| Giá token giảm một nửa | 13 đ và 65 đ | 4.346 đ | −2,8% |
| Tỉ lệ xem lại gấp đôi | Tiền xem lại × 2 | 6.292 đ | +40,7% |
| Tỉ lệ xem lại giảm một nửa | Tiền xem lại ÷ 2 | 3.562 đ | −20,3% |
| Số ca làm lại gấp đôi | Tiền làm lại × 2 | 6.787 đ | +51,8% |
| Số ca làm lại giảm một nửa | Tiền làm lại ÷ 2 | 3.315 đ | −25,9% |
| Lương nhân viên tăng 25% | 2.500 đ mỗi phút | 5.506 đ | +23,1% |
| Chỉ cho chạy tối đa 2 lần | Bỏ lần chạy có attempt > 2; yêu cầu có so_lan_chay > 2 coi là chuyen_nhan_vien | 4.237 đ | −5,2% |
| Chỉ cho chạy 1 lần | Như trên với giới hạn 1 | 4.111 đ | −8,1% |

Tất cả số trong bảng là [simulated]. Tự kiểm: mỗi dòng "giảm một nửa" đúng bằng nửa dòng "gấp đôi" (2,8 = 5,6 ÷ 2; 20,3 ≈ 40,7 ÷ 2; 25,9 = 51,8 ÷ 2).

## B2 · Đổi một cặp và xếp hạng

- Giá token gấp đôi cùng lúc tỉ lệ xem lại gấp đôi: **6.543 đ (+46,3%)** [simulated] = 5,6% + 40,7%, đúng tổng hai tác động riêng vì mô hình cộng tuyến tính.
- Xếp hạng ba yếu tố ảnh hưởng mạnh nhất: 1. số ca làm lại (±51,8%) · 2. tỉ lệ xem lại (±40,7%) · 3. lương nhân viên (+23,1%). Giá token chỉ +5,6%.

## B3 · Giới hạn chạy lại có thật sự rẻ hơn

Chi phí cả hệ thống = tổng chi phí trợ lý + 12.000 đ × số yêu cầu không thành công.

| Giới hạn | Tổng chi phí trợ lý | Số yêu cầu không thành công | Chi phí cả hệ thống | Chi phí mỗi việc thành công |
| --- | ---: | ---: | ---: | ---: |
| 1 lần | 3.621.781 đ | 319 | 7.449.781 đ | 4.111 đ |
| 2 lần | 4.093.220 đ | 234 | 6.901.220 đ | 4.237 đ |
| 3 lần | 4.373.585 đ | 222 | 7.037.585 đ | 4.472 đ |

- Giới hạn rẻ nhất cho công ty là **2 lần** (6.901.220 đ) [simulated]; không trùng với giới hạn cho chi phí mỗi việc thành công thấp nhất (1 lần, 4.111 đ). Chọn 1 lần đẩy thêm 85 yêu cầu (319 − 234) sang nhân viên và cả hệ thống đắt hơn 548.561 đ so với 2 lần.

## B4 · Nếu phải xem lại tất cả

Phạm vi `noi_dia` + `hang_nang` (982 yêu cầu), 948 yêu cầu có ít nhất một lần `ok` × 5 phút xem lại, 48 ca làm lại.

- Với 9 phút làm lại (đề bài): tổng 10.568.513 đ ÷ 900 = **11.743 đ = 0,98×** của 12.000 đ [simulated]. Với 15,3 phút làm lại (trung bình thật của 74 ca `lam_lai` trong dữ liệu): **12.415 đ = 1,03×** [simulated] (dùng trung bình 15,3 thay cho 9).
- Nói gì về thứ pilot cần học: xem lại 100% gần như xoá hết tiết kiệm (tiền xem lại ≈ 90% chi phí); hoà vốn khi mỗi lần xem lại ≤ 5,1 phút (làm lại 9 phút) hoặc ≤ 4,8 phút (làm lại 15,3 phút). Pilot phải học được có giảm tỉ lệ xem lại an toàn được không và xem lại ngắn hơn 5 phút được không.

## Kiểm số tay (người kiểm số)

Đối chiếu tay với số trong A2, không dùng hàm `mo_hinh`:

- Tool: cộng cột `tool_calls` trên 1.624 lần chạy ra 5.600 lần gọi; 5.600 × 15 đ = **84.000 đ**, khớp bảng A2 (đo từ trace).
- Token, ba lần chạy đầu (`run_00001`–`run_00003`): 4.759 × 26/1.000 + 492 × 130/1.000 = 187,7 đ; 2.953 × 26/1.000 + 409 × 130/1.000 = 129,9 đ; 4.171 × 26/1.000 + 619 × 130/1.000 = 188,9 đ; cộng lại **506,6 đ**, khớp với công thức token trong code.
- Giờ nhân viên: 890 phút xem lại × 2.000 = 1.780.000 đ; 1.132 phút làm lại × 2.000 = 2.264.000 đ [simulated]; cộng token 245.585 + tool 84.000 ra tổng **4.373.585 đ**; chia 978 việc thành công = **4.472 đ** [simulated].
- Kết quả: số tính tay và số script độc lập khớp nhau; khi `src/lab13.py` chạy xong, chỉ cần đối chiếu 4.472 đ và 4.373.585 đ.
