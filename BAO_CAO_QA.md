# Báo cáo QA — MOD “Phần Thiên Các” 4.6.1 (Việt hóa, liên kết Đạo Uyên 5.4.2)

- **File gốc:** `4.6.1.Trung.json`, World Info gồm 121 entry (uid 0–120).
- **File kết quả:** `4.6.1.Viet.json`.
- **Đối chiếu:** worldbook Việt hóa 5.4.2 “Đạo_hữu_lên_trước_ta_đoạn_hậu”:
  - entry 231 `[initvar] Khởi tạo`
  - entry 229 `[mvu_update]`
- **Phạm vi áp dụng tiêu chí:** file 4.6.1 là World Info thuần, không có `tavern_helper.scripts`, `regex_scripts` hay khối `[initvar]` riêng. Vì vậy:
  - Hạng mục 2 và 4 được đối chiếu với [INITVAR] của bản 5.4.2 mà MOD gắn vào.
  - Các mục chỉ áp dụng cho script/EJS được ghi theo quy tắc cứng.
- **Ký hiệu trạng thái:**
  - **ĐÃ SỬA**: lỗi đã được sửa trong `4.6.1.Viet.json`.
  - **GIỮ + GHI CHÚ**: mâu thuẫn thiết lập mà sửa thì phải tự chọn phiên bản cốt truyện. Số liệu được giữ nguyên để tác giả quyết.

---

## [Hạng mục 0] TRUNCATION (cắt xén / vỡ cấu trúc)

- **[Hạng mục]** 0 — Truncation
- **[Vị trí]** Entry #1 【Thế lực】Phân nhóm thành viên cốt lõi (khối 内卫与执法); Entry #19 (detection)
- **[Mô tả lỗi]** List item rỗng `  - ` (nội dung bị cắt).
- **[Đề xuất sửa]** Xóa item rỗng. — ĐÃ SỬA

---

- **[Hạng mục]** 0 — Truncation
- **[Vị trí]** Entry #11 【Thế lực】Vòng tròn quan hệ và quan hệ thứ yếu
- **[Mô tả lỗi]** “灾兽组” lặp 2 lần, bản thứ hai thiếu dấu `"` đóng (chuỗi cụt). Hai dòng thụt lề sai.
- **[Đề xuất sửa]** Xóa bản cụt, chuẩn hóa thành `- Tên: "..."`. — ĐÃ SỬA

---

- **[Hạng mục]** 0 — Truncation
- **[Vị trí]** Entry #12 【Thế lực】Tài nguyên và kinh tế
- **[Mô tả lỗi]** Khối JSON hỏng: giá trị “丹药” thiếu dấu `"` đóng.
- **[Đề xuất sửa]** Đóng chuỗi. JSON đã parse hợp lệ. — ĐÃ SỬA

---

- **[Hạng mục]** 0 — Truncation
- **[Vị trí]** Entry #39 【Nhân vật】Tra nhanh phong cách chiến đấu; Entry #40 【Nhân vật】Các cặp ràng buộc cốt lõi; Entry #48 【Nhân vật】Chủng tộc và nhu cầu đặc biệt
- **[Mô tả lỗi]** JSON không hợp lệ:
  - Phần tử kết thúc bằng dấu phẩy toàn角 `，` / `}，`.
  - Thiếu dấu phẩy giữa hai phần tử mảng “种族间潜在冲突” (#48).
- **[Đề xuất sửa]** Thay bằng `,` ASCII và bổ sung dấu phẩy thiếu. — ĐÃ SỬA

---

- **[Hạng mục]** 0 — Truncation
- **[Vị trí]** Entry #21 【Quy tắc】Xử trí khẩn cấp
- **[Mô tả lỗi]**
  - Dòng cuối “附则” thừa (rác/cụt).
  - 丁案 có dấu `"` lồng phá vỡ chuỗi.
  - 附则六 đặt dấu `"` sai vị trí.
  - Ba khóa 罗刹饥饿管控 / 敖眠保护条例 / 万象悬赏阁对{{user}}条款 bị nuốt vào cuối chuỗi weakness_quickref.
  - Nhiều chỗ dính dòng.
- **[Đề xuất sửa]** Xóa dòng rác, tách chuỗi, đưa ba khóa ra khối `special_clauses`, đổi weakness_quickref sang block scalar `|`. — ĐÃ SỬA

---

- **[Hạng mục]** 0 — Truncation
- **[Vị trí]** Entry #18, #19, #49, #50, #51, #52, #55, #90, #93
- **[Mô tả lỗi]** Thiếu xuống dòng giữa các key YAML, làm vỡ cấu trúc. Ví dụ:
  - `…"顾长宁体制深潜: …"`
  - `reaction_ladder:一级・痕迹期:`
  - `核心特质:- "…"`
  - `…"修炼氛围:`
  - `路径F` (#52) thụt lề 0 nên rơi ra ngoài `chain_matrix`.
  - `说话方式` (#55, #93) thụt sai cấp.
- **[Đề xuất sửa]** Tách từng key thành dòng riêng, chỉnh thụt lề đúng cấp. — ĐÃ SỬA

---

- **[Hạng mục]** 0 — Truncation
- **[Vị trí]** Entry #88 Mộ Phi Hàn (dòng 年龄); Entry #106 Thẩm Hồng Tuyết (背景); Entry #108 Bùi Hành Nghi (quan hệ với Ôn Như Uẩn)
- **[Mô tả lỗi]** Dấu `"` ASCII đóng sớm hoặc lồng trong chuỗi YAML nháy kép, nên chuỗi kết thúc giữa chừng. Ví dụ:
  - `"沈氏学宗（"沈氏学宗与沈鹤归…"）`
  - `'她不是"看不见"…'`
- **[Đề xuất sửa]** Gộp lại thành một chuỗi. Trích dẫn lồng dùng `‘ ’` / `“ ”`. — ĐÃ SỬA (cả 63 thẻ nhân vật đã kiểm tra parse YAML hợp lệ)

---

- **[Hạng mục]** 0 — Truncation
- **[Vị trí]** Entry #92 Lăng Tố Thường
- **[Mô tả lỗi]**
  - Thiếu thẻ đóng `</凌素裳角色卡>` và `</凌素裳角色属性>`.
  - `身份:- "…"` dính dòng; mục thân phận thứ hai nằm ngoài list.
  - Các mục quan hệ thiếu `- `.
  - 外貌 / 性格 không thụt lề.
  - Khối JSON thuộc tính dồn một dòng.
- **[Đề xuất sửa]** Bổ sung thẻ đóng và chuẩn hóa toàn bộ cấu trúc. — ĐÃ SỬA

---

- **[Hạng mục]** 0 — Truncation
- **[Vị trí]** Entry #99 Hàn Chiêu Ninh
- **[Mô tả lỗi]** Thiếu hoàn toàn khối `<Thuộc tính nhân vật>`: không có cảnh giới, DC, công pháp, kỹ năng. Mọi thẻ cốt lõi khác đều có khối này, và thẻ 99 có nhắc tới “thương/súng”, “Hành Linh Căn”.
- **[Đề xuất sửa]** Tác giả bổ sung khối thuộc tính (tham khảo dòng Hàn Chiêu Ninh trong Entry #117: Đại Thừa sơ kỳ 169, Hành Thiên Thương · Xưng Lượng + Hành Thiên Súng · Định Giá). Không tự bịa số liệu. — GIỮ + GHI CHÚ

---

- **[Hạng mục]** 0 — Truncation
- **[Vị trí]** Entry #68 Thẩm Miên Sương; Entry #112 Tư Dạ Hoa; Entry #113 Tư Tễ Nguyệt; Entry #115 Tiết Ánh Hàn
- **[Mô tả lỗi]** Khối thuộc tính thiếu trường so với schema chung:
  - #68 thiếu “Danh sách đặc tính”.
  - #112, #113, #115 thiếu “Tổng cương võ học” và “Danh sách kỹ năng”.
- **[Đề xuất sửa]** Tác giả bổ sung các trường còn thiếu. — GIỮ + GHI CHÚ

---

- **[Hạng mục]** 0 — Truncation
- **[Vị trí]** Entry #118 Phần Thiên Các · Quy tắc nhận biết lẫn nhau giữa thành viên và cách ly an toàn
- **[Mô tả lỗi]** YAML hỏng:
  - `- |沈鸿雪…` (chỉ báo `|` dính văn bản cùng dòng).
  - Key `pairs:` dính vào cuối chuỗi `scope`.
  - Key `note:` dính vào phần tử cuối của `pairs`.
  - Nhiều câu trong rule_1/2/3 dính dòng.
- **[Đề xuất sửa]** Tách đúng cấu trúc (bản dịch đã parse YAML hợp lệ). — ĐÃ SỬA

---

## [Hạng mục 1] LỖI NGÔN NGỮ

- **[Hạng mục]** 1 — Lỗi ngôn ngữ
- **[Vị trí]** Toàn bộ `content` entry #0–#118, tiêu đề, `displayName` trong sổ cài đặt (#120)
- **[Mô tả lỗi]** Toàn bộ nội dung còn tiếng Trung.
- **[Đề xuất sửa]**
  - Dịch hoàn toàn sang tiếng Việt (Hán-Việt cho tên riêng).
  - Thuật ngữ, tên tổ chức và tên biến thống nhất theo bản 5.4.2.
  - Kiểm tra cuối: 0 ký tự Hán trong `content`/`comment`.
  - — ĐÃ SỬA

---

- **[Hạng mục]** 1 — Lỗi ngôn ngữ
- **[Vị trí]** Entry #1, #19, #117 (dòng Minh Yểu / Tễ Vô Ưu)
- **[Mô tả lỗi]** Tên nhân vật chính bị viết cứng “陈晓” thay cho macro.
- **[Đề xuất sửa]** Thay bằng `{{user}}`. — ĐÃ SỬA

---

- **[Hạng mục]** 1 — Lỗi ngôn ngữ
- **[Vị trí]** Entry #66 Long Quân (bối cảnh)
- **[Mô tả lỗi]** Văn bản hỏng “反复重第五届灭之战” (đúng nghĩa: 反复重温灭族之战).
- **[Đề xuất sửa]** Dịch theo nghĩa đúng “lặp đi lặp lại trận chiến diệt tộc”. — ĐÃ SỬA

---

- **[Hạng mục]** 1 — Lỗi ngôn ngữ
- **[Vị trí]** Entry #67, #61, #68 và các entry #0–#55 (rải rác)
- **[Mô tả lỗi]**
  - Cặp ngoặc lệch “『本宫」”.
  - Trộn 「」/『』/nháy ASCII `'` trong chuỗi YAML.
  - 《》 trong tên sách.
- **[Đề xuất sửa]** Chuẩn hóa: trích dẫn trong chuỗi dùng `‘ ’`, tên sách dùng `“ ”`. — ĐÃ SỬA

---

- **[Hạng mục]** 1 — Lỗi ngôn ngữ
- **[Vị trí]** Entry #59, #60, #68, #75, #77, #109 (và cách gọi Yến Vô Minh ở #108)
- **[Mô tả lỗi]** Dùng đại từ nam “他” cho nhân vật nữ. Gồm:
  - Dung Đường Nguyệt
  - Lệ Lăng Nhạc
  - Ân Vô Quy
  - Yến Vô Minh
- **[Đề xuất sửa]** Dùng “nàng” hoặc tên riêng. — ĐÃ SỬA

---

## [Hạng mục 2] TÊN BIẾN: SCHEMA vs RULES vs INITVAR

- **[Hạng mục]** 2 — Tên biến
- **[Vị trí]** Entry #5 【Quy tắc】Quy tắc chạm trán · Cốt lõi; Entry #6 【Quy tắc】Hệ thống con chạm trán; Entry #37 【Quy tắc】Ràng buộc chạm trán động; Entry #50 【Quy tắc】Nhịp độ chèn sự kiện nền
- **[Mô tả lỗi]** MOD gọi biến bằng tên tiếng Trung, không tồn tại trong [INITVAR] của 5.4.2 Việt hóa (entry 231). Các biến bị ảnh hưởng:
  - `世界.遭遇冷却`
  - `世界.动向`
  - `机遇`
  - `stat_data.世界.当前地点`
  - `stat_data.主角.境界`
- **[Đề xuất sửa]** Đổi sang:
  - `Thế Giới.Hồi Chiêu Chạm Trán`
  - `Thế Giới.Động Hướng`
  - `Cơ Ngộ`
  - `stat_data.Thế Giới.Địa Điểm Hiện Tại`
  - `stat_data.Nhân Vật Chính.Cảnh Giới`

  Đã xác nhận từng khóa có trong entry 231 của 5.4.2. — ĐÃ SỬA

---

## [Hạng mục 3] Không phát hiện lỗi.

## [Hạng mục 4] GETVAR/GETWI: KEY PATH VÀ COMMENT LOOKUP

- **[Hạng mục]** 4 — Truy xuất WB / path
- **[Vị trí]** Entry #50 【Quy tắc】Nhịp độ chèn sự kiện nền; Entry #116 【Quy tắc】Giao thức điều phối chạm trán Phần Thiên Các với chạm trán của thẻ chính
- **[Mô tả lỗi]** Tham chiếu khóa `ongoing_operations` không tồn tại. Khóa thật trong Entry #18 【Thế lực】Tuyến hành động hiện tại là `active_threads`.
- **[Đề xuất sửa]** Đổi thành `active_threads`. — ĐÃ SỬA

---

- **[Hạng mục]** 4 — Truy xuất WB / path
- **[Vị trí]** Entry #116
- **[Mô tả lỗi]** Trỏ tới “焚天阁【规则】剧情触发条目的profiles” — không có entry nào mang tên này. `profiles` nằm ở Entry #4 【人物】掩护身份速写.
- **[Đề xuất sửa]** Đổi thành “profiles trong mục 【Nhân vật】Phác họa thân phận yểm hộ”. — ĐÃ SỬA

---

- **[Hạng mục]** 4 — Truy xuất WB / path
- **[Vị trí]** Entry #118 (core_principle, rule_7)
- **[Mô tả lỗi]** Trỏ tới “应变章程眠眠在场守则”, nhưng 眠眠在场守则 thực tế nằm ở Entry #41 【规则】情报处理流程, không nằm trong mục 应变/应急处置 (#21).
- **[Đề xuất sửa]** Đổi thành “‘Thủ tắc khi Miên Miên có mặt’ trong mục 【Quy tắc】Quy trình xử lý tình báo”. — ĐÃ SỬA

---

- **[Hạng mục]** 4 — Truy xuất WB / path
- **[Vị trí]** Entry #119 DaoYuan Workshop · Character Binding (`extra.daoyuanWorkshop.data.characterId`)
- **[Mô tả lỗi]** Ràng buộc trỏ tới thẻ `《道渊》v5.4.2.png` (tên file bản Trung). Nếu bản Việt hóa 5.4.2 dùng tên PNG khác thì ràng buộc này sẽ không khớp.
- **[Đề xuất sửa]** Giữ nguyên vì không biết tên PNG của bản Việt hóa (worldbook là “Đạo_hữu_lên_trước_ta_đoạn_hậu”). Khi cài, đổi `characterId` thành đúng tên file thẻ Việt hóa, hoặc cài lại MOD qua DaoYuan Workshop. — GIỮ + GHI CHÚ

---

## [Hạng mục 5] Không phát hiện lỗi.

## [Hạng mục 6] Không phát hiện lỗi.

## [Hạng mục 7] LỖI LOGIC LỚN

- **[Hạng mục]** 7c — Chồng chéo bộ điều khiển
- **[Vị trí]** Entry #24 【Quy tắc】Đánh giá người chơi & Entry #25 【Quy tắc】Cụ thể hóa sự kiện kích hoạt nâng cấp đánh giá
- **[Mô tả lỗi]** Hai entry cùng bật, levels/dimensions trùng gần 100%. `change_rules` mâu thuẫn:
  - #24: tự tụt nấc không điều kiện.
  - #25: cần ≥10 lượt.
- **[Đề xuất sửa]** Tắt #24 (`disable: true`). #25 là bản thay thế đầy đủ. — ĐÃ SỬA

---

- **[Hạng mục]** 7 — Logic (trùng khóa/mục)
- **[Vị trí]** Entry #5, #9, #11, #16, #46
- **[Mô tả lỗi]** Trùng khóa hoặc trùng mục (YAML ghi đè):
  - Vận Ly bị liệt kê 2 lần trong never_leave (#5).
  - Key “司夜华” lặp (dòng 2 thực ra là Tư Tễ Nguyệt) (#9).
  - “声音猎人组” lặp (#11).
  - “言丝双潜” đặt cho 2 cặp khác nhau; “法阵傀儡矩阵” và “空间三层嵌套” lặp (#16).
  - Key “韵璃” lặp (#46).
- **[Đề xuất sửa]** Gộp mục trùng, sửa đúng tên, đổi tên tổ hợp thứ hai thành “Ngôn Tình Song Phá”. — ĐÃ SỬA

---

- **[Hạng mục]** 7 — Logic (số liệu mâu thuẫn)
- **[Vị trí]** Entry #7, #29, #40, #48, #52, #110, #111, #114
- **[Mô tả lỗi]** Số thành viên không khớp với Entry #0 (62). Các con số rải rác: 32, 48, 52, 53, 56, 57, 60; “7 kẻ lặn sâu” nhưng liệt kê 10.
- **[Đề xuất sửa]**
  - #7: đổi thành 62.
  - Các entry còn lại: bỏ con số cứng.
  - Giữ số hiệu “thành viên số 58” của Ngao Miên.
  - — ĐÃ SỬA

---

- **[Hạng mục]** 7 — Logic (dữ kiện chéo sai)
- **[Vị trí]** Nhiều entry, xem bảng dưới
- **[Mô tả lỗi]** Dữ kiện chéo sai, đã sửa:

| Entry | Lỗi | Đã sửa thành |
|---|---|---|
| #4 | Lan Nguyệt · Tễ vừa có profile riêng vừa nằm trong “những người còn lại” | Bỏ khỏi danh sách |
| #19 | Lộc Khê “金丹小修” trong khi hiển thị Trúc Cơ | Trúc Cơ |
| #30 | Đan phá cảnh ghi Liễu Nhứ Vãn; “8 người” nhưng liệt kê 9 | Tiết Ánh Hàn; sửa số |
| #32 | “~1000 năm trước” lệch biên niên #20 | ~1800 năm trước |
| #35 | Bùi Hành Nghi “2300 năm” | “hơn một nghìn năm” |
| #36 | Ngân Lũ gọi “điện hạ” (cách gọi của Tễ Vô Ưu) | “đại tiểu thư” |
| #45 | Danh sách phôi Tiên khí sai so với #28 | Sửa theo #28 |
| #46 | “霜盾” của Văn Nhân Sương mâu thuẫn hệ trọng lực | “thiết bích” |
| #71/#73 | Chiều quan hệ Ôn Như Uẩn ↔ Kỳ Vô U bị đảo | Sửa chiều |
| #74 | Ngu Mạn La “phê chuẩn” Tinh Trụy Diệt Thế | Ân Vô Quy phê chuẩn |
| #75 | “Cách ba đại cảnh giới” | Hai |
| #82 | Xưng hô “Ân tỷ~” trùng Sở Dao Lưu | Làm rõ |
| #86 | Tên “Luật Linh Căn” trùng Tiêu Vận Thanh | Thêm “(luật pháp)” |
| #92 | Người phát hiện ghi Ngu Mạn La; “ba quân cờ” nhưng liệt kê bốn | Dung Đường Nguyệt; bốn |
| #94 | Chiều cao sai số học; “ba nghìn ức dặm” | Sửa chiều cao; ba nghìn dặm |
| #95 | “Sáu kẻ lặn sâu” nhưng liệt kê năm | Năm |
| #98 | Trận doanh “混沌”; Markdown `**`; so sánh tầng đáy với Chu Lăng | “Hỗn loạn”; bỏ `**`; Kỷ Diên |
| #100 | Người cứu, số năm đeo vòng, Phi Dạ “đúc bằng pháp tắc Độ Kiếp” | Sửa |
| #105 | Chiều cao | Thuộc nhóm thấp nhất; Vận Ly 1m42 thấp nhất |
| #109 | “Già hơn Ân Vô Quy gần nghìn năm” (Ân Vô Quy ~6000) | Kém ~800 năm |
| #110 | Mốc 8/12/120 tuổi; ba bản danh sách thuộc hai chủ | Sắp lại mốc; thống nhất của Hoắc Khỉ La |
| #111 | Nhặt được khi đã nở hay còn là trứng | Theo bối cảnh: còn là trứng |
| #112 | So tuổi với Tô Vãn Nguyệt | Bỏ phép so sánh |

- **[Đề xuất sửa]** Như cột “Đã sửa thành”. — ĐÃ SỬA

---

- **[Hạng mục]** 7 — Logic (đơn vị thời gian)
- **[Vị trí]** Entry #36 【Nhân vật】Tra nhanh giờ giấc và thói quen; Entry #111 Ngao Miên
- **[Mô tả lỗi]** “一天睡十六个时辰 / 清醒八个时辰”, “亥至午睡十三时辰” — một ngày chỉ có 12 canh giờ, nên con số bất khả.
- **[Đề xuất sửa]** Hiểu 时辰 là “giờ/tiếng”: ngủ 16 tiếng, tỉnh 8 tiếng; ngủ ~13 tiếng. — ĐÃ SỬA

---

- **[Hạng mục]** 7 — Logic (mâu thuẫn mốc thời gian, cần tác giả chọn)
- **[Vị trí]** Nhiều entry, xem bảng dưới
- **[Mô tả lỗi]** Các mâu thuẫn chưa sửa:

| Entry | Mâu thuẫn |
|---|---|
| #88 | Sương Nguyệt thị bị săn 2000 năm trước + ngủ 1800 năm, nhưng tuổi 3200 |
| #92 | Thảm sát 1100 năm trước vs “tám trăm năm” |
| #94 | Các mốc 5 vạn năm / 3000 năm |
| #95 | Tuổi 900+ vs 19 + 400 năm |
| #100 vs #99 | Hai phiên bản cảnh cha Hàn Chiêu Ninh tử nạn |
| #101 | 600 vs 300 năm; “thọ nguyên vạn năm” vs 15 vạn năm của Đại Thừa (5.4.2) |
| #104 | Đếm số lần thay tim |
| #106 | Hoạt động “hơn hai nghìn năm” vs ~2500 năm |
| #108 | Bùi Hành Nghi 17 tuổi khi Thánh Đình diệt (2300 năm trước) nhưng “phụng sự 1500 năm” và “độc hành 800 năm” |
| #115 | 1200 + 200 + 1000 + 500 > 2400 tuổi; Bạch Hà (3000 tuổi) già hơn chủ |

- **[Đề xuất sửa]** Tác giả chọn một mốc thống nhất cho từng nhân vật. Bản dịch giữ số liệu gốc. Riêng #108, cụm “hai nghìn ba trăm năm cô độc” đã được diễn đạt trung tính. — GIỮ + GHI CHÚ

---

- **[Hạng mục]** 7 — Logic (thành viên mồ côi / cách ly mâu thuẫn)
- **[Vị trí]** Entry #4, #5, #21, #46 (Ân Cửu Quan); Entry #87, #106, #118 (cơ chế biết thân phận)
- **[Mô tả lỗi]**
  - 殷九棺 (Ân Cửu Quan) được nhắc ở nhiều quy tắc nhưng không có entry nhân vật.
  - “Chỉ ba/bốn thành viên biết thân phận” mâu thuẫn với:
    - việc Ôn Như Uẩn nhận bản tự đánh giá tâm lý;
    - tier_1 mặc định “mọi thành viên biết nhau” (#118).
- **[Đề xuất sửa]**
  - Tác giả bổ sung entry Ân Cửu Quan.
  - Đã thêm chú thích Ôn Như Uẩn chỉ nhận đánh giá qua mã hiệu kẻ lặn sâu.
  - Cần thống nhất #87 với #118.
  - — GIỮ + GHI CHÚ (một phần ĐÃ SỬA)

---

### Ghi chú liên kết với 5.4.2 Việt hóa

- **Từ khóa kích hoạt** (`key`/`keysecondary`): giữ nguyên khóa tiếng Trung và nối thêm khóa tiếng Việt, đúng quy ước song ngữ của worldbook 5.4.2. Ví dụ Entry #53: `殷无归, …, Ân Vô Quy, Phần Thiên Nữ Đế, các chủ, …`.
- **Nhân vật/thế lực của thẻ chính** dùng đúng tên trong 5.4.2: Cơ Hạo Thiên, Bạch Vi, Dao Tịch, Tô Thiên Mị, Hầu Cảnh, Vĩnh Ninh Công Chúa, Thần Sách Quân, Trận Thiên Tông, Nhân Đan Tông, Thi Ma Tông, U Duyệt, Vạn Bảo Lầu, Trấn Ma Ty…
- **Tiêu đề entry** đổi thành `[MOD][Phần Thiên Các][4.6.1][…]`. Các trường khác (uid, order, position, depth, constant, …) giữ nguyên. Thay đổi duy nhất ngoài dịch thuật là tắt #24.
