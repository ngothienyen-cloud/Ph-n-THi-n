# Báo cáo QA bổ sung — cập nhật lên 4.6.2

- **File gốc:** `DaoYuan_Workshop___cdca6076-…_1.json` (MOD Phần Thiên Các 4.6.2, 123 entry).
- **File kết quả:** `4.6.2.Viet.json`.
- **Tôi đã kiểm tra:**
  - JSON hợp lệ.
  - Không còn chữ Hán trong `content`/`comment`.
  - Các khối JSON thuộc tính parse được.
  - Thẻ nhân vật mới parse YAML được.
- **Thay đổi giữa 4.6.1 và 4.6.2:**
  - 92 entry giữ nguyên nội dung.
  - 26 entry có bổ sung, chủ yếu là thêm hai nhân vật mới vào các danh sách.
  - Thêm 2 entry mới: #121 Lạc Ân Từ, #122 Thẩm Tri Miểu.
- **Bản 4.6.2 gốc vẫn còn toàn bộ lỗi đã báo ở `BAO_CAO_QA.md` (4.6.1).** Tất cả các bản sửa đó đã được mang sang `4.6.2.Viet.json`, kể cả việc tắt entry #24.
- **Các trường kỹ thuật** lấy theo bản 4.6.2: `role` của #75/#76, `displayIndex`, `extra.daoyuanWorkshopEntry`, sổ cài đặt #120 (revision 2).

---

## [Hạng mục 0] TRUNCATION

- **[Hạng mục]** 0 — Truncation
- **[Vị trí]** Entry #121 Lạc Ân Từ
- **[Mô tả lỗi]** Cấu trúc YAML hỏng:
  - Khóa dùng dấu hai chấm toàn角 (`身份：`, `人际关系：`, `性格：`, `生活方式：`).
  - Các mục danh sách nằm ở cột 0.
  - `核心特质:` chứa chuỗi trần, thiếu `- `.
- **[Đề xuất sửa]** Chuẩn hóa thành YAML hợp lệ. — ĐÃ SỬA

---

- **[Hạng mục]** 0 — Truncation
- **[Vị trí]** Entry #122 Thẩm Tri Miểu
- **[Mô tả lỗi]**
  - Khối JSON thuộc tính bị dồn trên **một dòng**, chung dòng với thẻ mở `<沈知渺角色属性>`.
  - Các mục `身份` / `人际关系` / `核心特质` nằm ở cột 0.
- **[Đề xuất sửa]** Định dạng lại JSON và YAML. — ĐÃ SỬA

---

## [Hạng mục 1] LỖI NGÔN NGỮ

- **[Hạng mục]** 1 — Lỗi ngôn ngữ
- **[Vị trí]** Entry #121, #122 và phần bổ sung của 26 entry thay đổi (#0, 1, 4, 5, 9, 11, 16, 18, 19, 20, 21, 28, 29, 35, 36, 39, 40, 41, 43, 46, 48, 52, 117, …); sổ cài đặt #120
- **[Mô tả lỗi]** Nội dung mới của bản 4.6.2 còn tiếng Trung.
- **[Đề xuất sửa]**
  - Dịch hoàn toàn và ghép vào đúng vị trí trong bản Việt hóa đã sửa lỗi.
  - Thuật ngữ đồng bộ với 5.4.2: Huyết Thần Cung, Phi Nguyệt, Tần Tâm, Thiên Dư, Hợp Hoan Tông, Nam Ly Hỏa Châu.
  - Khóa kích hoạt song ngữ.
  - — ĐÃ SỬA

---

## [Hạng mục 2] Không phát hiện lỗi.

## [Hạng mục 3] Không phát hiện lỗi.

## [Hạng mục 4] Không phát hiện lỗi.

## [Hạng mục 5] Không phát hiện lỗi.

## [Hạng mục 6] Không phát hiện lỗi.

## [Hạng mục 7] LỖI LOGIC LỚN

- **[Hạng mục]** 7 — Logic (số liệu)
- **[Vị trí]** Entry #0 so với #9, #111, #114 …
- **[Mô tả lỗi]** Bản 4.6.2 nâng số thành viên cốt lõi lên 64.
- **[Đề xuất sửa]** Đã cập nhật #0 thành “sáu mươi bốn”. Các chỗ khác vốn đã bỏ con số cứng từ bản 4.6.1. — ĐÃ SỬA

---

- **[Hạng mục]** 7 — Logic (mốc thời gian)
- **[Vị trí]** Entry #122 Thẩm Tri Miểu; Entry #20 (biên niên)
- **[Mô tả lỗi]** Văn bản ghi “Yên Hà Các bị thôn tính năm nàng ba trăm tuổi”, nhưng ngay sau đó lại ghi:
  - chạy trốn 3 năm, lúc đó nàng 16 tuổi;
  - khi bị thôn tính nàng còn quá nhỏ, chưa có hồ sơ.

  Ngoài ra:
  - Tuổi 1300 được chia thành “600 năm ở Yên Hà Các + 300 + 200 + 200”, không khớp với việc nàng rời Yên Hà Các năm 13 tuổi.
  - #20 ghi rời Hợp Hoan Tông khoảng 700 năm trước, còn #122 ngụ ý khoảng 400 năm trước.
- **[Đề xuất sửa]** Đổi thành “năm mười ba tuổi” (khớp với #20: Yên Hà Các diệt vong khoảng 1300 năm trước). Phần chia tuổi và mốc rời Hợp Hoan Tông giữ nguyên, để tác giả thống nhất. — ĐÃ SỬA (một phần) / GIỮ + GHI CHÚ

---

- **[Hạng mục]** 7 — Logic (mốc thời gian)
- **[Vị trí]** Entry #121 Lạc Ân Từ
- **[Mô tả lỗi]** Văn bản ghi “khoảng 2100 tuổi”, nhưng nàng vào Huyết Thần Cung năm 7 tuổi và nằm vùng 1400 năm, tức khoảng 1407 tuổi.
- **[Đề xuất sửa]** Tác giả chọn một mốc. — GIỮ + GHI CHÚ

---

- **[Hạng mục]** 7 — Logic (nhất quán)
- **[Vị trí]** Entry #121 (quan hệ với Lệ Lăng Nhạc so với mục Lối sống); Entry #117 (dòng Thẩm Tri Miểu)
- **[Mô tả lỗi]**
  - #121 vừa ghi “Lệ Lăng Nhạc không biết Lạc Ân Từ tồn tại”, vừa ghi “Lệ Lăng Nhạc biết trong Huyết Thần Cung có người của chúng ta”.
  - #117 tả kiểu tóc/trang phục của Thẩm Tri Miểu (búi rủ mây, khoác sa mực, lúm đồng tiền) hơi khác thẻ #122 (búi sừng dê, áo choàng sa trơn).
- **[Đề xuất sửa]**
  - #121: thống nhất thành “biết có người, không biết là ai”. — ĐÃ SỬA
  - #117: chênh lệch nhỏ, giữ nguyên. — GIỮ + GHI CHÚ
