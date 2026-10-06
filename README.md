# AI Coding Assistant

Trợ lý AI giúp người mới học lập trình **C/C++** **hiểu code, tìm lỗi và tự sửa lỗi**, thông qua một trang web có khung chat

> Tiểu luận nhóm môn **Nhập môn Công nghệ số và Trí tuệ nhân tạo**<br>
> Nhóm thực hiện: **Misfits**<br>
> Giảng viên hướng dẫn: **Nguyễn Thành Sơn**<br>
> Trường Đại học Gia Định<br>

**Trang web:** https://cemazzz.github.io/ai_coding_assistant_by_Misfits/
---

## Giới thiệu

Người mới học lập trình thường gặp ba khó khăn: đọc không hiểu đoạn code, không biết vì sao chương trình báo lỗi, và nhận đáp án sẵn nên học xong dễ quên.

AI Coding Assistant giải quyết bằng cách đóng vai một gia sư:

- Giải thích code bằng tiếng Việt, đi từng dòng.
- Chỉ ra dòng bị lỗi và nguyên nhân.
- Gợi ý hướng sửa để người học tự viết lại, thay vì đưa đáp án ngay.

## Tính năng

| Tính năng | Mô tả |
|---|---|
| Giải thích code | Dán đoạn code, nhận giải thích từng bước |
| Tìm lỗi | Chỉ ra dòng lỗi, giải thích thông báo lỗi |
| Gợi ý cách sửa | Đưa gợi ý để người dùng tự sửa |
| Giao diện web | Trang giới thiệu, nút **Bắt đầu dùng** và khung chat |

## Cách sử dụng

1. Mở trang web ở đường dẫn phía trên.
2. Đọc phần giới thiệu, kéo xuống cuối trang và bấm **Bắt đầu dùng**.
3. Chọn một câu hỏi gợi ý, hoặc bấm vào ô chat để mở khung chat.
4. Nhập câu hỏi hoặc dán đoạn code, rồi gửi.
5. Đọc phản hồi của trợ lý và tự sửa lại code.

Nếu khung chat không mở, hãy bấm vào biểu tượng chat ở góc phải dưới màn hình.

## Công nghệ

- **AI Agent:** xây dựng trên nền tảng Coze
- **Giao diện:** HTML, CSS, JavaScript thuần (không dùng framework)
- **Kết nối AI:** Cloudflare Workers gọi Coze Chat API (giấu token khỏi trình duyệt)
- **Triển khai:** GitHub Pages

## Cấu trúc thư mục

```
.
├── index.html    # Toàn bộ giao diện trang web và mã nhúng khung chat
└── README.md     # Tài liệu này
```

## Chạy trên máy

Không cần cài đặt thêm phần mềm nào.

1. Tải hoặc clone repo về máy.
2. Mở file `index.html` bằng trình duyệt (bấm đúp vào file).
3. Cần có kết nối mạng để khung chat tải được.

## Cách kết nối với AI

Trang web không giữ token. Khi người dùng gửi câu hỏi, trang gọi một
Cloudflare Worker; Worker giữ token và bot id trong biến bí mật, gọi
Coze Chat API rồi trả câu trả lời về trang web.

Người dùng → Trang web (GitHub Pages) → Cloudflare Worker → Coze Agent

Trong `index.html` chỉ cần điền địa chỉ Worker ở biến `API_URL`.
> ⚠️ **Lưu ý bảo mật:** trang web tĩnh gửi toàn bộ mã nguồn về trình duyệt, nên token đặt trong `index.html` có thể bị người khác xem được. Vì vậy:
> - Chỉ dùng token riêng cho dự án, cấp quyền tối thiểu và đặt thời hạn ngắn.
> - Không dùng token của tài khoản có dữ liệu quan trọng.
> - Xoá token sau khi kết thúc môn học.
> - **Không** đăng token thật lên nơi công khai ngoài trang web của dự án.

## Giới hạn hiện tại

- Trợ lý có thể trả lời chưa chính xác, cần kiểm tra lại thông tin quan trọng.
- Bot cần vài giây để trả lời, vì câu trả lời hiện về cả khối một lần
- Chất lượng trả lời phụ thuộc vào nội dung huấn luyện (prompt) của Agent trên Coze.

## Hướng phát triển

- Giấu token bằng máy chủ trung gian (ví dụ Cloudflare Workers).
- Mở rộng thêm ngôn ngữ lập trình (Python, Java)
- Thêm bài tập nhỏ sau mỗi lượt giải thích.

## Thành viên nhóm

| STT | Họ và tên | MSSV | Nhiệm vụ |
|---|---|---|---|
| 1 | Nguyễn Văn Đẳng | 26140039 | Triển khai ra công chúng&Chiến dịch truyền thông đa kênh |
| 2 | Trương Quang Phông | 26140029 | Tổng kết và check nội dung |
| 3 | Lê Ngọc Duy | 26140014 | Thiết kế & Huấn luyện AI Agent |
| 4 | Trần Thế Toàn | 26140025 | Xây dựng AI Agent |
| 5 | Phan Văn Duy| 26140013 | Triển khai nền tảng và web |

---
> Một phần mã nguồn và tài liệu của dự án được tạo với sự hỗ trợ của AI.<br>
> Nhóm đã kiểm tra, chỉnh sửa và chịu trách nhiệm về nội dung cuối cùng.<br>

*Dự án phục vụ mục đích học tập.*

