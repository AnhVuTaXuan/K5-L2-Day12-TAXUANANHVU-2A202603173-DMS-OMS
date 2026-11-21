# Danh sách lớp v0 — Tạ Xuân Anh Vũ · G07

Viết tiếp từ slide 54 bài giảng. Mỗi lớp trả lời: **model cần nhận ra cái này để làm gì?**

## DMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng DMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | `eye_state` | open / closed / unknown | Phát hiện ngủ gật và trạng thái vi ngủ (microsleep) thông qua chỉ số PERCLOS (% thời gian nhắm mắt). | Có, trừ khi tròng kính bị đốm LED rọi loá trực tiếp. |
| 2 | `gaze_zone` | road / mirror_l / mirror_r / mirror_c / cluster / center / lap / other | Phát hiện mất tập trung (distraction detection); phát cảnh báo khi mắt rời khỏi đường quá 2–3 giây. | Có, nhìn rõ hướng con ngươi và hốc mắt dưới ánh sáng IR. |
| 3 | `head_pose` | yaw, pitch, roll (tính từ 13 keypoints) | Phát hiện gục đầu ngủ gật, quay đầu nhìn sang bên hoặc cúi đầu bấm điện thoại. | Có, 13 điểm skeleton mặt thể hiện rõ tư thế 3D trên IR. |
| 4 | `hand_on_wheel` | yes / no / unknown | Giám sát tài xế tuân thủ quy tắc giữ tay lái khi xe đang kích hoạt tính năng hỗ trợ lái ADAS/L2. | Có, thấy rõ biên dạng bàn tay và vị trí tiếp xúc vô lăng. |
| 5 | `phone_use` | held / mounted / lap | Phát hiện hành vi sử dụng điện thoại khi đang lái xe gây mất an toàn giao thông. | Có, nhận diện qua khối viền kim loại/màn hình phẳng trên IR. |
| 6 | `glasses_type` | none / clear / sun / unknown | Cung cấp ngữ cảnh để hiệu chỉnh thuật toán phát hiện mắt/mí (tránh báo động giả khi đeo kính). | Có, phân biệt được kính cận và kính râm (dù một số kính râm trong suốt trên NIR). |

## OMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng OMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | `seat_occupancy` | empty / occupied | Kích hoạt hệ thống nhắc cài dây an toàn và điều tiết hướng gió điều hòa thông minh theo ghế có người. | Có, phân biệt rõ người/vật với mặt ghế trên IR. |
| 2 | `occupant_type` | adult / child / object / empty | Phân loại đối tượng trên ghế để điều chỉnh lực bung túi khí phù hợp hoặc vô hiệu hoá túi khí thông minh. | Có, nhận biết qua kích thước và hình dáng trên IR. |
| 3 | `child_seat_presence` | child_seat / infant_seat / none | Tự động tắt túi khí ghế phụ/ghế sau khi phát hiện ghế trẻ em quay ngược hướng (rear-facing). | Có, cấu trúc và quai xách của nôi/ghế trẻ em thể hiện rất rõ trên IR. |
| 4 | `seatbelt_status` | worn_correct / worn_incorrect / not_worn / unknown | Nhắc nhở người ngồi sau cài dây an toàn đúng cách nhằm đáp ứng tiêu chuẩn an toàn Euro NCAP. | Khó thấy hơn trên IR nếu trang phục màu tối do mất kênh màu. |
| 5 | `forgotten_child` | child_detected / none | Cảnh báo trẻ em hoặc vật nuôi bị bỏ quên trong xe khi xe đã tắt máy và khoá cửa (Child Presence Detection). | Có, nhận biết chuyển động và hình dáng ngay cả trong bóng tối. |
| 6 | `left_behind_object` | bag / box / phone_laptop / other | Nhắc nhở hành khách không để quên hành lý, ba lô, ví tiền hoặc đồ đạc giá trị khi rời xe. | Có, phân biệt qua hình khối hộp/túi trên ghế và sàn xe. |

## 2 câu hỏi leo thang

1. **Câu hỏi:** Khi tài xế đeo khẩu trang hoặc quàng khăn che kín toàn bộ mũi và miệng, cụm 13 keypoints mặt (`face13`) có bắt buộc phải đánh dấu ước lượng vị trí giải phẫu các điểm môi/mũi kèm cờ `occluded = 1` không, hay được phép gán `outside = 1` hoặc bỏ qua skeleton?
   - **Khung ví dụ:** `D05.png`
   - **Bạn tạm gán thế nào và vì sao:** Tạm vẽ box `face`, các điểm mắt không bị che gắn bình thường, điểm chóp mũi và 4 điểm môi ước lượng vị trí giải phẫu và bật cờ `occluded = 1` vì vẫn xác định được vùng giải phẫu của chúng nằm bên trong khuôn mặt.
2. **Câu hỏi:** Trong OMS, trường hợp hành khách mang theo thú cưng (chó/mèo) nằm trên ghế sau thì hệ thống nên gán là `person` (vì là thực thể sống cần kích hoạt cảnh báo sinh mạng) hay gán là `object` (loại `other`)?
   - **Khung ví dụ:** `S07_rgb.png` / `S07_ir.png`
   - **Bạn tạm gán thế nào và vì sao:** Tạm gán là `object` với `type = other` vì Guideline v1.0 chỉ định nghĩa `person` là người; đồng thời ghi chú vào báo cáo để đề xuất cập nhật Guideline v1.1 bổ sung nhãn riêng cho thú cưng (`pet`).
