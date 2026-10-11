# Báo cáo QA — Đăng Hỏa U (Việt hóa)

Thẻ đã sửa: `Dang_Hoa_U_Vi_da_sua.json`. Tất cả script tiếng Việt host tại repo này, khóa theo commit `8660d65`.

[Hạng mục 0] Không phát hiện lỗi.

**[Hạng mục 1]** Lỗi ngôn ngữ
- **[Vị trí]** Script 1 (Cấu trúc biến), Script 3 (Chỉ mục lời mở đầu), Script 4 (Bộ điều khiển ngụy đồng tầng)
- **[Mô tả lỗi]** Các script này vẫn là bản tiếng Trung của upstream: key biến, prompt và thông báo đều bằng tiếng Trung.
- **[Đề xuất sửa]** Đã dịch toàn bộ và host tại `cau_truc_bien/`, `chi_muc_loi_mo_dau/`, `dieu_khien_nguy_dong_tang/`. Key được căn token với frontend nên trùng khớp từng chữ.

- **[Vị trí]** Entry 18, 19 và prompt trong schema
- **[Mô tả lỗi]** Rules và prompt bắt AI viết tóm tắt bằng tiếng Trung giản thể, giữ tên người theo tên gốc tiếng Trung.
- **[Đề xuất sửa]** Đã đổi thành yêu cầu viết bằng tiếng Việt, dùng tên tiếng Việt trong thẻ.

**[Hạng mục 2]** Tên biến: SCHEMA vs RULES vs INITVAR
- **[Vị trí]** Script 1
- **[Mô tả lỗi]** Schema dùng key tiếng Trung (`本尊`, `红颜`…), còn rules, initvar, frontend và dynamic WB dùng key tiếng Việt. Ngoài ra URL của script đã bị dịch (`Nơi ánh đèn le lói-Cấu trúc biến`) nên trả về 404.
- **[Đề xuất sửa]** Đã thay bằng schema tiếng Việt. Cấu trúc cây mặc định trùng 100% với bản gốc (389 đường dẫn).

- **[Vị trí]** Entry 18, 19
- **[Mô tả lỗi]** Key trong rules lệch schema:

  | Rules đang viết | Schema |
  |---|---|
  | `Bản Tôn` | `Bản tôn` |
  | `Hành Tung` | `Hành tung` |
  | `Tình cảnh hiện tại` | `Hoàn cảnh hiện tại` |
  | `$Cơ hội có thể tham gia` | `$Cơ duyên có thể tham gia` |
  | `Độ hảo cảm` | `Độ thiện cảm` |
  | `Ngữ cảnh quan hệ` | `Bối cảnh quan hệ` (5 trường con) |
  | `Ghi chép gắn kết` | `Ký sự ràng buộc` |
  | `Túi tạp vật` | `Túi chứa tạp vật` |
  | `Tên` / `Mô tả` | `Tên gọi` / `Miêu tả` |
  | `Biến hóa gần nhất` | `Biến đổi gần đây` |
  | `Ảnh hưởng có thể thấy` | `Ảnh hưởng nhìn thấy được` |
  | `Cấp bậc ảnh hưởng` | `Cấp độ ảnh hưởng` |
  | `Loại` (của cơ duyên/nhiệm vụ) | `Loại hình` |
  | `Số hiệp giao phong` | `Vòng giao phong` |

  Danh sách trường phái sinh trong rules có nhắc các trường không tồn tại trong schema.
- **[Đề xuất sửa]** Đã sửa theo schema. Một công cụ quét tự động mọi đường dẫn trong rules: tất cả đều hợp lệ.

- **[Vị trí]** Initvar trong 22 lời mở đầu (thẻ này đặt initvar trong lời mở đầu, không có entry `[initvar]`)
- **[Mô tả lỗi]** Hơn 1.190 key sai, mỗi lời mở đầu dịch một kiểu, ví dụ `Bản Tôn`, `Binh khí bản mệnh`, `Năm tháng đã sống`, `Mối quan hệ`, `Đồ giám NPC`, `Thời gian thế giới`, `Tài`. Zod tự xóa các key này nên trạng thái khởi đầu bị mất.
- **[Đề xuất sửa]** Đã chuẩn hóa theo ngữ cảnh đường dẫn. Đã chạy lại 22 khối qua schema: không còn key nào bị loại ngoài ý muốn.

**[Hạng mục 3]** Giá trị enum
- **[Vị trí]** Script 1, frontend, dynamic WB, script 4
- **[Mô tả lỗi]** Bảng alias được tra bằng `map[giá_trị.toLowerCase()]`, trong khi key tiếng Việt viết hoa. Vì vậy mọi giá trị enum (trạng thái sự kiện, giai đoạn, loại cơ duyên…) đều bị reset về mặc định.
- **[Đề xuất sửa]** Đã sửa bằng AST: tra đúng chữ hoa/thường trước, rồi mới tra chữ thường. Đã chuẩn hóa `đang ổn định`/`Ổn định trung` thành `Đang ổn định`, và `tu luyện`/`lôi kiếp`… viết hoa cho thống nhất.

- **[Vị trí]** Entry 18, 19
- **[Mô tả lỗi]** Giá trị enum trong rules lệch schema:

  | Rules đang viết | Schema |
  |---|---|
  | `Hạ màn` | `Khép lại` |
  | `Sóng gợn/Biến đổi nhẹ/Rõ rệt` | `Gợn sóng nhỏ/Biến động nhẹ/Đáng kể` |
  | `Bàng quan` | `Đứng ngoài quan sát` |
  | `Khám phá` | `Thám hiểm` |
  | `Chỉnh bị` | `Chỉnh đốn` |
  | `Kéo dài bình lặng` | `Tiếp diễn êm đềm` |
  | `Thành lập sau khi chọn` | `Thiết lập sau khi chọn` |
  | `Thăm dò` | `Dò xét` |
  | `Thoát khỏi chiến đấu` | `Rời trận chiến` |
  | `Tụt cảnh giới` | `Rớt cảnh` |
  | `Cùng hoạn nạn/Tâm sự` | `Hoạn nạn có nhau/Thổ lộ tâm tình` |
- **[Đề xuất sửa]** Đã sửa.

- **[Vị trí]** Initvar
- **[Mô tả lỗi]** Giá trị không hợp lệ: `layer` = `Tầng đất`/`Tầng dưới`/`Địa Tầng` (5 lời mở đầu báo lỗi Schema); loại nhiệm vụ `Chính tuyến`/`Nhánh`; loại địa điểm `Thành trấn`/`Cấm địa`; `Vô`.
- **[Đề xuất sửa]** Đã đổi sang `Địa tầng`/`Hạ tầng`, `Tuyến chính`/`Tuyến nhánh`, `Thị trấn`/`Cấm Địa`, `Không`.

**[Hạng mục 4]** GETVAR/GETWI
- **[Vị trí]** Entry 88, 89
- **[Mô tả lỗi]** Sáu đường dẫn `getvar` sai, ví dụ `stat_data.Bản Tôn.Hành Tung.Tầng thứ trực thuộc`, `…Thông tin điều hướng`, `stat_data.Tình cảnh hiện tại`, `$Suy đoán tông môn.Thế lực chủ đạo hiện tại`. Hậu quả là khối "Tông môn địa vực" luôn trả về "Vùng đất chưa rõ".
- **[Đề xuất sửa]** Đã đổi sang `Bản tôn.Hành tung.Tầng cấp trực thuộc`, `…Thông tin dẫn đường`, `Hoàn cảnh hiện tại`, `Thế lực chính hiện tại`.

[Hạng mục 5] Không phát hiện lỗi.

**[Hạng mục 6]** JavaScript
- **[Vị trí]** Frontend `dang_hoa_lan_san/index.html`
- **[Mô tả lỗi]** Lỗi cú pháp: key nhiều từ không bọc nháy (`Ngu Tịch_front:`, `Toái Kim Uyên·Vạn Kiếm Trũng:`…), nên toàn bộ giao diện không chạy.
- **[Đề xuất sửa]** Đã bọc nháy cho các key này.

- **[Vị trí]** Frontend
- **[Mô tả lỗi]** Tên file ảnh chân dung trên R2 bị dịch (`Bạch Thanh Huyền (1).png`, `Vũ Lam (2).png`…) nên ảnh không tải được và hiện bóng người "?".
- **[Đề xuất sửa]** Đã khôi phục tên file gốc (26 lời gọi và 15 tên file).

- **[Vị trí]** Script 1, frontend, dynamic WB, script 4
- **[Mô tả lỗi]** Hàm làm sạch tên nhiệm vụ đòi phải có chữ Hán, nên mọi tên nhiệm vụ tiếng Việt bị thay thành "Nhiệm vụ tuyến chính". Regex đọc thời gian bị dịch hỏng (`(\d+) Năm…`, `[Tý Sửu …]`), làm sai thứ tự sắp xếp Thế giới đồ chí.
- **[Đề xuất sửa]** Đã sửa cả hai.

- **[Vị trí]** Frontend, dynamic WB
- **[Mô tả lỗi]** Key `事件`/`关联事件ID` chưa được dịch ở frontend, còn dynamic WB lại dịch thành `Sự kiện liên kếtID`.
- **[Đề xuất sửa]** Đã thống nhất thành `Sự kiện` / `ID sự kiện liên quan` ở mọi nơi.

- **[Vị trí]** Initvar, lời mở đầu 5
- **[Mô tả lỗi]** Bẫy YAML: dòng `Danh sách thần thông:` thụt lề sai, nên cả khối initvar không parse được.
- **[Đề xuất sửa]** Đã chỉnh lại thụt lề.

**[Hạng mục 7]** Lỗi logic lớn
- **[Vị trí]** Script 3, 4 và regex "Frontend ngụy đồng tầng"
- **[Mô tả lỗi]** URL import bị dịch nên trả về 404. Bộ điều khiển chèn `<pseudo_layer>灯火阑珊</pseudo_layer>`, trong khi regex chỉ bắt tên tiếng Việt.
- **[Đề xuất sửa]** Đã host bản tiếng Việt, cập nhật URL, và cho bộ điều khiển xuất `Đăng Hỏa Lan San`. Frontend chấp nhận cả thẻ `Nội dung chính` và `Chính văn`.

- **[Vị trí]** Dynamic WB và các entry giai đoạn
- **[Mô tả lỗi]** Dynamic WB tìm `Giai đoạn hảo cảm`/`Giai đoạn yêu sâu sắc`, trong khi thẻ đặt tên `Giai đoạn thiện cảm`/`Giai đoạn yêu sâu đậm`. Thẻ viết `Mộng Yểu Linh`, còn mọi script dùng `Mộng Diểu Linh`. Hậu quả là các entry giai đoạn không bao giờ được bật.
- **[Đề xuất sửa]** Đã sửa dynamic WB và đổi tên trong thẻ thành `Mộng Diểu Linh`. Entry 36 và 40 đổi thành `…yêu sâu đậm`.

- **[Vị trí]** Dynamic WB
- **[Mô tả lỗi]** Các mẫu comment bị dịch tách chữ (`(?:势|Thế)(?:力|Lực)-…ESJ`, `[Hồng nhanChỉ mục]`, `[mvu]Danh sách biến`) không khớp với entry 20, 75, 88, 89.
- **[Đề xuất sửa]** Đã sửa mẫu để nhận đúng tên comment trong thẻ.

- **[Vị trí]** Entry 33–40 (ghi chú, không sửa)
- **[Mô tả lỗi]** Comment `Ngu Tịch Nhan-Giai đoạn …` bị trùng ở hai bộ entry (Ngu Tịch và Ngu Nhan). Đây là thiết kế hai nhân cách: hai bộ cùng bật theo giai đoạn, và không có `getwi` nào gọi tới.
- **[Đề xuất sửa]** Giữ nguyên.
