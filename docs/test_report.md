# Báo cáo kiểm thử — Portfolio CV

**Ngày kiểm thử:** 25/11/2026  
**Đối tượng:** Website portfolio tĩnh trong `index.html`  
**Môi trường:** Chromium 140, phục vụ trang qua `python3 -m http.server`; desktop 1440 × 900 px và mobile 390 × 844 px.

## Tổng quan kết quả

| Tiêu chí | Kết quả | Tóm tắt |
|---|---|---|
| Tính đúng đắn | Đạt có điều kiện | Nội dung, điều hướng neo, tài nguyên ảnh và xác thực cơ bản của biểu mẫu hoạt động; liên kết dự án vẫn là placeholder. |
| UI/UX | Đạt cơ bản | Bố cục desktop và mobile đã được chụp lại; không ghi nhận nội dung hero bị khuất ở hai khung hình kiểm thử. |
| Khả năng vận hành - xử lý lỗi | Đạt một phần | Trang tĩnh tải được; trình duyệt kiểm tra trường bắt buộc và email, nhưng không có xử lý/gửi biểu mẫu phía máy chủ. |
| Bảo mật | Đạt trong phạm vi website tĩnh | Không thấy backend, thư viện hoặc nơi lưu trữ dữ liệu biểu mẫu; chưa thực hiện kiểm thử xâm nhập hay đánh giá máy chủ. |
| Chất lượng mã nguồn | Đạt cơ bản | HTML có cấu trúc ngữ nghĩa, CSS tách riêng; chưa có bộ kiểm thử tự động trong dự án. |
| Khả năng triển khai | Đạt cho nội dung tĩnh | Trang và tài nguyên đã tải thành công qua local HTTP server; không chạy bước build hoặc container. |

## 1. Tính đúng đắn

- Mở trang thành công qua local server; các phần Giới thiệu, Kỹ năng, Dự án và Liên hệ hiện diện.
- Bấm điều hướng **Kỹ năng** đưa URL tới `#skills`.
- Cả 5 ảnh (ảnh đại diện và 4 ảnh dự án) tải thành công, không có ảnh lỗi.
- Biểu mẫu từ chối trường để trống và email sai định dạng bằng kiểm tra HTML gốc của trình duyệt; các trường hợp nhập đủ và email hợp lệ vượt qua kiểm tra này.
- **Chưa đạt đầy đủ:** bốn liên kết “Xem chi tiết” trong thẻ dự án hiện dùng `href="#"`, chưa dẫn tới dự án thực tế.

**Minh chứng:** [Ảnh desktop](screenshots/01-desktop.png), [ảnh mobile](screenshots/02-mobile.png).

## 2. UI/UX

- Ở desktop 1440 × 900 px, phần dự án hiển thị theo bố cục nhiều cột và các vùng chính được thể hiện trong ảnh toàn trang đã làm mới.
- Ở mobile 390 × 844 px, ảnh chụp mới ghi nhận bố cục một cột và toàn bộ phần hero nằm trong khung hình; không thấy phần mô tả hoặc ảnh đại diện bị khuất ở mép ngang.
- Giao diện đang ở mức nhất quán nhưng tên dự án và vai trò vẫn trộn Việt – Anh; cần thống nhất nếu yêu cầu phát hành hoàn toàn bằng tiếng Việt.

**Minh chứng:** [Ảnh desktop](screenshots/01-desktop.png), [ảnh mobile](screenshots/02-mobile.png).

## 3. Khả năng vận hành - xử lý lỗi

- Trang tĩnh mở được qua HTTP server và tải các tài nguyên tương đối.
- Các trường `required` và `type="email"` cung cấp kiểm tra dữ liệu cơ bản ở phía trình duyệt.
- Biểu mẫu chưa có backend/dịch vụ tiếp nhận, không gửi thông tin liên hệ và không có trạng thái thành công hoặc lỗi từ dịch vụ.
- Không có ứng dụng máy chủ hoặc luồng xử lý lỗi ứng dụng để kiểm thử trong phiên bản tĩnh này.

**Minh chứng:** [Ảnh desktop](screenshots/01-desktop.png) có phần Liên hệ và biểu mẫu.

## 4. Bảo mật

- Trong phạm vi các tệp được kiểm tra, website là nội dung HTML/CSS tĩnh, không có backend, thư viện bên ngoài hoặc nơi lưu trữ dữ liệu biểu mẫu.
- Kiểm tra email của trình duyệt chỉ hỗ trợ trải nghiệm nhập liệu, không thay thế xác thực phía máy chủ nếu sau này tích hợp dịch vụ nhận dữ liệu.
- Chưa thực hiện pentest, quét lỗ hổng, kiểm thử tải hoặc rà soát cấu hình HTTP/TLS/security headers của máy chủ triển khai.

**Minh chứng:** [Ảnh desktop](screenshots/01-desktop.png) ghi nhận trang và biểu mẫu ở trạng thái tĩnh.

## 5. Chất lượng mã nguồn

- Có các vùng HTML ngữ nghĩa như `header`, `nav`, `main`, `section`, `article` và `footer`; CSS được tách thành `assets/css/styles.css`.
- Các trường biểu mẫu có nhãn; ảnh nội dung có văn bản thay thế.
- CSS có breakpoint responsive, kiểu `focus-visible` và hỗ trợ `prefers-reduced-motion`.
- Chưa có kiểm thử tự động, quy trình lint/validate HTML hoặc CI trong dự án.
- Các `href="#"` của dự án là phần cần hoàn thiện để tránh điều hướng không có đích hữu ích.

**Minh chứng:** [Ảnh desktop](screenshots/01-desktop.png) và [ảnh mobile](screenshots/02-mobile.png).

## 6. Khả năng triển khai

- Xác nhận trang có thể mở trực tiếp từ `index.html` hoặc qua local HTTP server; các ảnh và CSS cục bộ được tải cùng trang.
- Không có bước build hay dependency cài đặt theo mô tả dự án.
- Không chạy bước triển khai production hoặc kiểm thử container.
- Cần thay liên kết mẫu và quyết định cách tiếp nhận biểu mẫu trước khi phát hành chính thức.

**Minh chứng:** [Ảnh desktop toàn trang](screenshots/01-desktop.png) và [ảnh mobile](screenshots/02-mobile.png).

## Kết luận

Website đáp ứng mức trình bày portfolio tĩnh cơ bản trên desktop và mobile. Các ảnh minh chứng đã được làm mới theo giao diện hiện tại.

Website vẫn chưa được coi là hoàn tất phát hành cho người dùng thực tế cho đến khi thay các liên kết dự án mẫu và xác định rõ biểu mẫu liên hệ sẽ được tích hợp hay bỏ chức năng gửi.
