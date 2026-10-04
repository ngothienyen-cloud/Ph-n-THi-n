# Phần Thiên Các — MOD 4.6.2 (Việt hóa)

Bản Việt hóa của MOD 焚天阁 (Phần Thiên Các) 4.6.2. MOD này là World Info dành cho thẻ 道渊 (Đạo Uyên) và được liên kết với bản Việt hóa 5.4.2 “Đạo hữu lên trước ta đoạn hậu”.

| File | Nội dung |
|---|---|
| `4.6.2.Viet.json` | Bản cập nhật 4.6.2 (Việt hóa, mang theo toàn bộ sửa lỗi của 4.6.1, thêm Lạc Ân Từ và Thẩm Tri Miểu). |
| `BAO_CAO_QA_4.6.2.md` | Báo cáo QA bổ sung cho 4.6.2. |
| `chan_dung_4.6.2.json` | Ảnh chân dung (URL từ Workshop 4.6.2), sắp theo tên tiếng Việt, 66 nhân vật/68 ảnh — dùng cho Thanh trạng thái. |
| `ten_nhan_vat_nu_4.6.2.txt` | Danh sách tên nhân vật nữ (tiếng Việt) để đưa vào Regex Tuyệt Sắc Bảng. |
| `DaoUyen_5.4.2_Viet_PhanThienCac_4.6.2.png` | Thẻ Đạo Uyên 5.4.2 Việt hóa đã cập nhật: Thanh trạng thái (regex MVU.MOD) có ảnh chân dung 66 nhân vật Phần Thiên Các; 2 regex Tuyệt Sắc Bảng Huyền Thiên Giới có thêm 63 tên; regex Thiên Đạo Phán Định có bảng ảnh 66 nhân vật nhúng sẵn. |
| `regex/*.json` | Bốn regex đã sửa (Thanh trạng thái, Thiên Đạo Phán Định, Tuyệt Sắc Bảng 1/2), xuất riêng để nhập thẳng vào SillyTavern nếu không muốn thay cả thẻ. |

## Cài đặt

1. Nhập thẻ `DaoUyen_5.4.2_Viet_PhanThienCac_4.6.2.png` (hoặc chỉ nhập các file trong `regex/` vào thẻ đang dùng).
2. Nhập `4.6.2.Viet.json` vào World Info.

Entry #119 (DaoYuan Workshop · Character Binding) vẫn trỏ tới `《道渊》v5.4.2.png`. Nếu file thẻ Việt hóa của bạn có tên khác, sửa `characterId` cho khớp.
