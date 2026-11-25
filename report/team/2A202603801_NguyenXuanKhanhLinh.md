# Báo cáo cá nhân · Nguyễn Xuân Khánh Linh

## 1. Thông tin thành viên

- **Họ tên** · Nguyễn Xuân Khánh Linh
- **MSSV** · `2A202603801`
- **Email trường** · `26ai.linhnxk2@vinuni.edu.vn`
- **Nhóm và lớp** · Coffee, L3B
- **Vai trò** · Người gắn nhãn 2 kiêm giữ hồ sơ Launch v0

## 2. Phần việc phụ trách

Em phụ trách gắn nhãn độc lập 20 ca lỗi ở CP3 và tổng hợp kết quả các nhiệm vụ A–E vào hồ sơ Launch v0. Em theo dõi các bằng chứng cần có trước khi nhóm đề xuất pilot cho yêu cầu hoàn phí nội địa và hàng nặng.

## 3. Đóng góp cụ thể

- **CP3** · Em tự chọn nhãn cho 20 tình huống theo năm loại lỗi trong đề. Sau khi Hải hoàn thành bộ nhãn độc lập, hai bộ trùng **18/20 ca (90%)**. Nhóm thống nhất ca 6 là **Do người dùng** vì khách chọn sai mục, và ca 8 là **Hệ thống** vì trợ lý viện dẫn điều khoản không có trong chính sách. Bộ nhãn thống nhất khớp **20/20** với bảng tham khảo của lab. Bảng CP3 ghi đủ **5 ca khắc phục**, mỗi loại một ca. [Bảng lỗi CP3](bang_loi.md)
- **Hồ sơ Launch v0** · Em tổng hợp đủ 7 mục và đối chiếu số liệu với bảng chi phí, đặc tả chỉ số và kế hoạch pilot. Trong phạm vi đề xuất, ước tính chi phí cả hệ thống sau khi cộng xử lý thay và chi phí cố định là **5.217 đ/yêu cầu**, thấp hơn **56,5%** so với mốc **12.000 đ/yêu cầu** (`simulated`). Hồ sơ chốt **Go có điều kiện**, với các điều kiện về kiểm thử lỗi tài chính, ghi nhận event, phê duyệt thiết kế và đo thời gian xem lại. [Hồ sơ Launch v0](ho_so_launch_v0.md)
- **Rà soát pilot và chỉ số** · Em bổ sung cách theo dõi **7 ngày sau lần đóng đầu tiên** và làm rõ **299 yêu cầu mỗi nhân viên**, tương đương **5.980 yêu cầu thực tế** và khoảng **859,2 quan sát hiệu dụng** cho mỗi nhóm. Kế hoạch tách luật dừng ngay khi phát hiện hoàn trùng hoặc báo hoàn tất trước khi ghi sổ. Em cũng rà đặc tả **5 chỉ số và 13 event**, gồm event nhân viên mở trợ lý và event ghi sổ hoàn tiền. [Kế hoạch pilot](pilot_plan.yaml) · [Đặc tả chỉ số](chi_so.md)

## 4. Bằng chứng

| Đóng góp | Bằng chứng trong repo |
| --- | --- |
| Bộ nhãn độc lập của Linh và kết quả đối chiếu với Hải | [Bảng lỗi CP3](bang_loi.md#hai-bộ-nhãn-độc-lập) · [Commit c5de251](https://github.com/justapea25/K5-L3B-DAY13-Coffee-LaunchEconomics/commit/c5de251) |
| Rà đặc tả chỉ số, cửa sổ theo dõi và luật dừng | [Kế hoạch pilot](pilot_plan.yaml) · [Commit 7b46552](https://github.com/justapea25/K5-L3B-DAY13-Coffee-LaunchEconomics/commit/7b46552) |
| Tổng hợp và cập nhật hồ sơ Launch v0 | [Hồ sơ Launch v0](ho_so_launch_v0.md) · [Commit 2887a0d](https://github.com/justapea25/K5-L3B-DAY13-Coffee-LaunchEconomics/commit/2887a0d) · [Commit b9b84ca](https://github.com/justapea25/K5-L3B-DAY13-Coffee-LaunchEconomics/commit/b9b84ca) |

## 5. Công cụ AI đã dùng

Em dùng ChatGPT/Codex để đọc đề, tra định nghĩa năm nhãn của Google PAIR, trình bày tình huống theo từng lượt năm ca và ghi vào bảng các nhãn em đã tự chọn. Em cũng dùng công cụ này để rà số liệu, kiểm tra liên kết và chỉnh hồ sơ Launch v0. Việc kiểm tra dựa trên đối chiếu cột của em với 20 lựa chọn đã gửi, đếm số ca trùng giữa hai bộ nhãn và so nhãn thống nhất với bảng tham khảo của lab. Phần kỹ thuật được kiểm tra bằng cách chạy `lab13.py` và đọc kế hoạch qua `yaml.safe_load`. [Nguồn Google PAIR](https://pair.withgoogle.com/guidebook-v2/chapter/errors-failing/)

## 6. Tự đánh giá

Em hiểu rõ hơn vì sao cần phân biệt nguyên nhân gây lỗi với cách lỗi được phát hiện, đặc biệt ở ca 6 và ca 8. Khi tổng hợp hồ sơ, em học cách so chi phí trên cùng đơn vị đ/yêu cầu và phân biệt kết quả giả lập với bằng chứng cần thu trong pilot. Lần sau, em sẽ ghi một câu giải thích ngay khi gắn nhãn các ca dễ nhầm và theo dõi riêng việc hoàn thiện tài liệu với việc phê duyệt pilot.
