# Phần Thiên Các — MOD 4.6.1 (Việt hóa)

Bản Việt hóa của MOD 焚天阁 (Phần Thiên Các) 4.6.1. MOD này là World Info dành cho thẻ 道渊 (Đạo Uyên) và được liên kết với bản Việt hóa 5.4.2 “Đạo hữu lên trước ta đoạn hậu”.

| File | Nội dung |
|---|---|
| `4.6.1.Viet.json` | World Info đã dịch hoàn toàn. Đã sửa lỗi theo bộ tiêu chí QA (message.txt) và dùng tên biến của 5.4.2. |
| `BAO_CAO_QA.md` | Báo cáo QA theo các hạng mục 0–7. |
| `4.6.2.Viet.json` | Bản cập nhật 4.6.2 (Việt hóa, mang theo toàn bộ sửa lỗi của 4.6.1, thêm Lạc Ân Từ và Thẩm Tri Miểu). |
| `BAO_CAO_QA_4.6.2.md` | Báo cáo QA bổ sung cho 4.6.2. |
| `chan_dung_4.6.2.json` | Ảnh chân dung (URL từ Workshop 4.6.2), sắp theo tên tiếng Việt, 66 nhân vật/68 ảnh — dùng cho Thanh trạng thái. |
| `ten_nhan_vat_nu_4.6.2.txt` | Danh sách tên nhân vật nữ (tiếng Việt) để đưa vào Regex Tuyệt Sắc Bảng. |
| `DaoUyen_5.4.2_Viet_PhanThienCac_4.6.2.png` | Thẻ Đạo Uyên 5.4.2 Việt hóa đã cập nhật: Thanh trạng thái (regex MVU.MOD) có ảnh chân dung 66 nhân vật Phần Thiên Các; 2 regex Tuyệt Sắc Bảng Huyền Thiên Giới có thêm 63 tên. |
| `regex/*.json` | Ba regex đã sửa, xuất riêng để nhập thẳng vào SillyTavern nếu không muốn thay cả thẻ. |
| `glossary.md` | Bảng thuật ngữ và tên biến dùng khi dịch. |

## Cài đặt

1. Nhập `4.6.1.Viet.json` vào World Info của SillyTavern.
2. Dùng cùng thẻ Đạo Uyên 5.4.2 Việt hóa.

Entry #119 (DaoYuan Workshop · Character Binding) vẫn trỏ tới `《道渊》v5.4.2.png`. Nếu file thẻ Việt hóa của bạn có tên khác, sửa `characterId` cho khớp.
