# Khai báo dùng AI — Tạ Xuân Anh Vũ

| # | Công cụ | Bạn hỏi gì (tóm tắt) | Bạn dùng kết quả thế nào | Bạn có kiểm lại không? Bằng gì? |
|---|---|---|---|---|
| 1 | Antigravity AI Assistant | Lập kế hoạch thực hiện Lab 12 theo Rubric và giải thích quy tắc toạ độ mắt trục y trên ảnh DMS xoay 90°. | Áp dụng lộ trình các mốc Checkpoint A, B, Final; kiểm tra mắt trái có toạ độ y lớn hơn mắt phải trên ảnh Drive&Act. | Có, đối chiếu trực tiếp với GUIDE.md §4.4 và chạy script `cabin_check.py` kiểm tra mã lỗi. |
| 2 | Antigravity AI Assistant | Gợi ý các hiện tượng quang học IR thực tế và lập danh sách chức năng model cabin cho DMS/OMS. | Tham khảo hoàn thiện bảng `ir_log.csv` và `class_list_v0.md`. | Có, đối chiếu slide bài giảng 15–26, 40–54 và kiểm tra cấu trúc schema trong `cabin_schema.py`. |
| 3 | Antigravity AI Assistant | Hướng dẫn kiểm tra định dạng file export và lệnh nén zip nộp bài không kèm ảnh. | Sử dụng các câu lệnh powershell/bash để kiểm tra `annotations.xml` trong file zip nộp bài. | Có, chạy `python -m zipfile -l export_final.zip` kiểm tra thực tế. |
