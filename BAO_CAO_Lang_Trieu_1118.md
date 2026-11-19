# Lãng Triều 1118 — Turing Tiếng Việt (đã sửa)

File: `Lang_Trieu_1118_Turing_Tieng_Viet_da_sua.json` — cập nhật từ bản Việt 1105 (đã sửa) lên cấu trúc 1118.

## Cách làm
- Lấy toàn bộ cấu trúc, cài đặt, thứ tự mục, regex và script của bản 1118 (164 mục, 12 regex, 2 script).
- Mục không đổi nội dung: giữ nguyên bản dịch 1105.
- Mục có thay đổi ở 1118: dịch/sửa lại theo bản 1118.
- Trạng thái bật/tắt: giữ theo bản 1105 của bạn; mục mới lấy mặc định của 1118.

## Giữ nguyên chỉnh sửa riêng của bản 1105
- Độ dài mặc định 4000—8000 chữ (cùng `wave_check_length`, `wave_note_length`, nay thêm `wave_fixed_target` để script tính độ dài).
- Ngôn ngữ chính văn: Tiếng Việt; Dọn ngoại ngữ; Song ngữ dịch sang tiếng Việt.
- Giá trị mặc định cài sẵn trong "🧬 Khởi tạo biến" (thân mật dịu dàng, neo tuổi thông thường, ngôi thứ ba, không thuật lại, không cướp lời, văn phong tự thích ứng, phố phường chứng giám, hộp đen) — đã thay bằng nội dung 1118 tương ứng.
- Khối `<age_anchor_scope>` trong Chuỗi tư duy và chính văn.

## Mục mới (16)
Bản sắc nhân vật · Nhân vật vào tranh · Đối thoại Nhiều/Vừa/Ít/Toàn đối thoại · Nhân vật ngôi thứ nhất · Góc nhìn Thượng đế · Nhịp thở đoạn văn · Nhân gian thôn dã · Tự sự phương Tây · Giang hồ chiếu ảnh · Tản văn tùy bút · Thế giới song song · Phần đuôi 4C/4H · Trò chuyện với Lãng Triều.

## Mục đổi nội dung chính
Ranh giới Cách mạng Văn học, Chống toàn tri, Tùy cảnh ứng biến, Kẻ thù cách mạng, Thuận đà / Rảo bước, Kể lại và viết mở rộng, Hộp đen + 2 chế độ tiếng lòng, Độ dài động Nhiều/Ít, Chống máy móc hóa, Miêu tả không dán nhãn, Tăng cường ẩn dụ, Chặn giọng cổ phong, NTR, ASMR, Lựa chọn hành động (cấu hình số lượng/phân loại), Tự phê bình, Xen lời, Kế hoạch (tiếp nối/quyền hạn/nhân vật/kiểm tra), Chuỗi tư duy và chính văn, Đọc dữ liệu, Lời tác giả. Mọi văn phong thêm quy tắc tránh số "ba"/"3". Các câu "dù không liên quan cũng phải viết một dòng" đã bỏ theo 1118.

## Regex / Script
- 12 regex (thêm Thế giới song song) Việt hóa giao diện; regex Lựa chọn hành động nhận cả tên phân loại và "Không áp dụng" tiếng Việt.
- Script "Ta chính là Lãng Triều": Việt hóa thông báo; nút đổi tên thành "Lãng Triều·Trạng thái"; bộ tính độ dài nhận "Mục tiêu chính văn lượt này: X đến Y chữ" và "mỗi đoạn khoảng N chữ". Bảng cụm từ của khiên Gemini giữ tiếng Trung (đó là chuỗi đối chiếu, không phải văn bản hiển thị).
- Bảng điều khiển Thủy triều: Việt hóa lưu ý, hướng dẫn 10 kênh, nhóm, mô tả mục, FAQ, cài đặt giao diện; tên kênh cũ (Trung/Việt 1105) được ánh xạ sang tên mới nên tiến độ đã lưu không mất.
- Đã kiểm tra cú pháp JS của 2 script và 14 khối script trong regex.
