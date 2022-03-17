# Tìm hiểu về Docker
- Docker là công cụ tạo các vùng cách ly để chạy 1 ứng dụng

### Các lệnh của Docker:
- Để sử dụng docker trong terminal thì lệnh bắt đầu bắt "docker", theo sau là những lệnh con.
- Ví dụ: docker image --help: để xem docker hướng dẫn về lệnh image
 1. Lệnh images:
  - Image trong docker là gì: Đó là những phần mềm được quản lý bởi docker và không thể chỉnh sửa, image đóng gói các phần mềm như linux, mySQL...
  - Khi docker khởi chạy các images thì các phiên bản của image gọi là các container, container có thể ghi dữ liệu vào trong nó.
  - Để kiểm tra docker đang có các image nào thì mình sử dụng câu lệnh là <span style="color: 	#FF0000">docker image</span>
