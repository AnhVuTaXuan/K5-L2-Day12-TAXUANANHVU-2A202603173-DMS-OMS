# TEAM — Ngày 12

Mã bộ ảnh: **G07** · Hình thức: **cá nhân**

| Họ tên | MSSV | Đã gán đủ 22 ảnh? | Review chéo với (peer diff) | Số dòng disagreement đã xử lý |
|---|---|---|---|---|
| Tạ Xuân Anh Vũ | 2A202603173 | có | Bạn cùng mã G07 | 24 |

Ca hai bạn vẫn không thống nhất và đã hỏi coach (ghi tên ảnh + đối tượng):

- D01 (hand): Tranh luận về việc bàn tay chạm hờ vào vô lăng khi xe đang tự lái có tính `on_wheel = yes` hay `no`. Coach giải thích: chỉ tính `yes` khi tay nắm/chạm giữ vô lăng, chạm hờ hoặc rời vô lăng gán `no`.

## Cá nhân

### TaXuanAnhVu-2A202603173
- Phần mình làm: Tự gán đủ 22 ảnh cốt lõi trên CVAT local (S01–S08 RGB+IR và D01–D06), chạy script `cabin_check.py` qua tất cả checkpoint A, B, Final, thực hiện diff đối chiếu với bạn cùng mã G07 và xử lý 5 điểm bất đồng, hoàn thiện báo cáo và bài nộp.
- Điều mình học được hôm nay: Hiểu sâu sắc sự khác biệt giữa ảnh RGB và ảnh hồng ngoại NIR/IR-sim; nắm vững quy tắc gọi ghế theo chiều xe và trái/phải theo giải phẫu người dù góc camera bị đảo chiều hay xoay 90°.
