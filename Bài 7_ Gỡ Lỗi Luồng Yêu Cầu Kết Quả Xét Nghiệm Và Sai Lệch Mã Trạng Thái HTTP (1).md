Phần 1: Các lỗi sai về nguyên lý  
DNS & TCP/TLS: Giao thức DNS thực hiện phân giải tên miền thành địa chỉ IP, không dùng để phân giải cổng mạng. Giao thức HTTPS yêu cầu bắt buộc phải hoàn tất tiến trình thiết lập kết nối (TCP/TLS Handshake) trước khi truyền tải dữ liệu HTML.  
Mã lỗi HTTP: Sự cố sập cơ sở dữ liệu là lỗi hệ thống phía máy chủ, bắt buộc trả về mã 500 Internal Server Error. Việc báo lỗi 404 Not Found là sai bản chất kỹ thuật và gây hậu quả hoảng loạn tâm lý do bệnh nhân lầm tưởng hồ sơ đã bị xóa.  
Thao tác DOM: Tab Elements chỉ thay đổi giao diện, không có chức năng gửi dữ liệu cập nhật về cơ sở dữ liệu máy chủ.  
Phần 2: Hoàn thiện quy trình & Giải thích  
Vòng đời HTTP Request chuẩn: Phân giải DNS (tìm IP) \-\> Thiết lập kết nối TCP/TLS \-\> HTTP Request & Response (nhận mã 500 do lỗi máy chủ) \-\> Rendering Pipeline (hiển thị giao diện báo lỗi).  
Nguyên lý bộ nhớ: Thao tác trên Tab Elements là can thiệp trực tiếp vào cấu trúc DOM lưu tại bộ nhớ RAM cục bộ (Client-side). Toàn bộ thay đổi này không có giá trị lưu trữ và sẽ bị ghi đè bằng dữ liệu gốc từ máy chủ (Server-side) ngay khi tiến hành tải lại trang.

