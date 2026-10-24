---
name: ui-ux-app-design
description: Thiết kế và review UI/UX cho app (web, mobile, desktop WPF/WinForms) — chọn design system, layout, màu, chữ, trạng thái, accessibility, rồi tự audit trước khi giao. Dùng khi tạo màn hình mới, làm lại giao diện, hoặc review UI có sẵn.
---

# UI/UX App Design

Mục tiêu: giao diện **đúng việc, dễ dùng, nhất quán, không "na ná AI"**. Làm theo 5 bước, không nhảy cóc.

## Bước 1 — Hiểu bài toán (trước khi vẽ bất cứ gì)
Trả lời ngắn 5 câu, ghi vào đầu output:
1. Ai dùng? (kỹ sư, khách hàng, người mới…) — mức thành thạo?
2. Việc chính họ phải làm xong trên màn hình này là gì? (1 câu)
3. Tần suất: dùng 1 lần / hằng ngày / cả ngày liên tục?
4. Môi trường: desktop màn rộng, laptop, điện thoại, ngoài công trường?
5. Ràng buộc: framework, brand màu có sẵn, offline, đa ngôn ngữ?

Nếu thiếu thông tin quan trọng → hỏi tối đa 3 câu. Còn lại tự giả định và ghi rõ giả định.

## Bước 2 — Chọn hướng thiết kế theo loại app
| Loại app | Hướng | Mật độ |
|---|---|---|
| Tool kỹ thuật / nội bộ (CAD, E3D, quản lý dữ liệu) | Gọn, trung tính, ưu tiên dữ liệu | Dày, ít khoảng trắng thừa |
| Dashboard / báo cáo | Số liệu nổi bật, biểu đồ rõ | Trung bình |
| App khách hàng / mobile | Thân thiện, tap target lớn | Thoáng |
| Landing / marketing | Cá tính, typography mạnh | Rất thoáng |

Chọn **một** hướng, nói lý do trong 1 câu. Không trộn phong cách.

## Bước 3 — Design system tối thiểu (định nghĩa trước, dùng xuyên suốt)
- **Màu:** 1 màu chính, 1 màu nhấn, thang xám 5–7 bậc, 4 màu trạng thái (success / warning / error / info). Khai báo thành token/biến, không hardcode rải rác. Có cả light và dark nếu nền tảng hỗ trợ.
- **Chữ:** tối đa 2 font. Thang cỡ cố định (vd 12 / 14 / 16 / 20 / 24 / 32). Body ≥ 14px desktop, ≥ 16px mobile.
- **Khoảng cách:** lưới 4 hoặc 8 (4, 8, 12, 16, 24, 32, 48). Không dùng số lẻ tùy hứng.
- **Bo góc, viền, bóng:** chọn 1 bộ, áp đồng nhất.
- **Icon:** một bộ duy nhất, cùng nét, cùng cỡ.

## Bước 4 — Dựng màn hình
### Bố cục
- Thứ bậc rõ: mắt người dùng phải biết nhìn đâu trước trong 3 giây.
- Hành động chính (primary) chỉ **một** nút nổi bật mỗi vùng. Hành động nguy hiểm (xoá) tách xa, màu đỏ, có xác nhận.
- Nhóm thông tin liên quan gần nhau; dùng khoảng trắng để phân nhóm thay vì kẻ khung khắp nơi.
- Căn lề thẳng hàng theo lưới; số liệu canh phải, chữ canh trái.

### Đủ mọi trạng thái (hay bị quên nhất)
Mỗi màn hình/thành phần phải có: **mặc định, đang tải, rỗng (empty), lỗi, thành công, disabled, hover/focus/pressed**. Empty state phải nói người dùng làm gì tiếp.

### Form & nhập liệu
- Label luôn hiển thị (không chỉ placeholder). Đơn vị đo ghi rõ (mm, m, kg).
- Validate ngay khi rời ô, báo lỗi cạnh ô, nói cách sửa — không chỉ "Invalid".
- Giá trị mặc định hợp lý; nhớ lựa chọn lần trước nếu có ích.
- Hỗ trợ bàn phím: Tab đúng thứ tự, Enter = xác nhận, Esc = huỷ.

### Câu chữ trong giao diện
- Nút dùng động từ cụ thể: "Xuất báo cáo", không phải "OK".
- Thông báo lỗi: chuyện gì xảy ra + vì sao + làm gì tiếp.
- Ngắn, cùng một thuật ngữ cho cùng một thứ trong toàn app.

### Riêng desktop (WPF/WinForms/tool kỹ thuật)
- Có phím tắt cho thao tác lặp lại; hiển thị phím tắt trong tooltip.
- Cửa sổ resize được, nhớ kích thước/vị trí; panel chia được.
- Bảng dữ liệu: sort, filter, chọn nhiều, copy ra Excel.
- Tác vụ lâu: progress + nút Huỷ, không đơ UI (chạy nền).
- Undo cho thao tác sửa dữ liệu khi có thể.

### Riêng mobile
- Tap target ≥ 44×44 pt; hành động chính nằm vùng ngón cái.
- Tôn trọng safe area, dark mode, cỡ chữ hệ thống.

## Bước 5 — Tự audit trước khi giao (bắt buộc)
Chạy checklist, sửa hết mục fail rồi mới giao:
- [ ] Tương phản chữ ≥ 4.5:1 (chữ lớn ≥ 3:1)
- [ ] Không truyền đạt thông tin chỉ bằng màu
- [ ] Mọi thao tác làm được bằng bàn phím; focus nhìn thấy được
- [ ] Đủ 7 trạng thái ở Bước 4
- [ ] Không còn giá trị màu/cỡ/khoảng cách nằm ngoài design system
- [ ] Hành động nguy hiểm có xác nhận hoặc undo
- [ ] Văn bản dài / dữ liệu rỗng / dữ liệu rất nhiều không vỡ layout
- [ ] Ở khung hẹp nhất được hỗ trợ không bị cuộn ngang
- [ ] 10 heuristic Nielsen: trạng thái hệ thống, ngôn ngữ người dùng, kiểm soát & thoát, nhất quán, phòng lỗi, nhận biết hơn nhớ, linh hoạt, tối giản, giúp sửa lỗi, trợ giúp

## Tránh "giao diện AI rập khuôn"
- Không mặc định gradient tím-xanh, card bo tròn đổ bóng xếp lưới, emoji làm icon.
- Không nhồi hiệu ứng; animation 150–250ms, chỉ để báo thay đổi trạng thái.
- Không thêm tính năng/nút người dùng không cần chỉ để "trông đầy đủ".

## Định dạng output
1. Tóm tắt Bước 1 (5 dòng) + hướng đã chọn (1 dòng)
2. Bảng token design system
3. Code/mockup màn hình
4. Kết quả checklist Bước 5 (pass/fail, đã sửa gì)
5. Giả định đã đặt + điểm cần người dùng quyết định
