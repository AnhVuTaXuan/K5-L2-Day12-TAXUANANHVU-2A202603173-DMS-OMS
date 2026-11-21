# Tự đánh giá — Tạ Xuân Anh Vũ · G07

## 1. Tự rà soát 4 cảnh

Nghỉ tay 1 phút, mở lại bài của mình, chọn 4 ảnh (2 S##, 2 D##), đọc như người lạ.

Loại lỗi: `seat_flip`, `wrong_class`, `guess`, `box`, `missing`, `extra`, `lr_flip` (trái/phải mặt), `flag` (thiếu cờ điểm), `ok`.

| Ảnh | Đối tượng | Loại lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|
| S01_rgb | person (ghế trái ảnh) | ok | Đã gán đúng seat=rear_right (theo xe, không theo ảnh) | rồi |
| S02_ir | person | guess | Ban đầu đoán seatbelt từ ảnh RGB, sau đó đã chuyển về unknown theo quy tắc | rồi |
| D01 | face13 | lr_flip | Lúc đầu đặt skeleton theo chiều dọc thông thường, sau đó đã chỉnh lại mắt trái có y lớn hơn mắt phải | rồi |
| D03 | hand | ok | Bàn tay trái người lái xác định đúng theo người, on_wheel=no chính xác | rồi |

## 2. Lỗi mình lặp lại nhiều nhất hôm nay

Lỗi: Thói quen phản xạ ban đầu đặt toạ độ trái/phải theo góc nhìn người quan sát màn hình thay vì theo góc nhìn giải phẫu người lái (trên ảnh Drive&Act xoay 90°) và theo hướng nhìn của xe (trên ảnh SVIRO quay ngược ra sau).

Vì sao mình mắc: Do phản xạ mắt nhìn màn hình tự nhiên chưa quen với việc camera bị xoay góc hoặc quay ngược chiều khoang lái.

Lần sau tránh bằng cách: Tự đặt câu thần chú trước khi gán: "OMS: Trái ảnh là Phải xe (rear_right); DMS xoay 90°: Mắt trái nằm thấp hơn (y lớn hơn)".

## 3. Ghi chú về disagreement_log

Một dòng bạn của mình đúng và mình sai. Mình học được gì từ dòng đó:
Ở cảnh S02_rgb, bạn của mình phát hiện ra mình để thuộc tính ghế `seat = driver` (do CVAT tự điền giá trị mặc định đầu danh sách) thay vì `rear_right` theo xe. Mình học được rằng với camera khoang sau (OMS), luôn phải chủ động mở tab DETAILS để chọn lại vị trí ghế theo xe (trái ảnh là phải xe), không được dựa vào giá trị mặc định của phần mềm.
