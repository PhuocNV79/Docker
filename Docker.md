## Tìm hiểu về Docker Image, chạy 1 container
- Docker là công cụ tạo các vùng cách ly để chạy 1 ứng dụng

### Các lệnh của Docker:
- Để sử dụng docker trong te inal thì lệnh bắt đầu bắt "docker", theo sau là những lệnh con.
- Ví dụ: docker image --help: để xem docker hướng dẫn về lệnh image
 #### 1. Lệnh images:
  - Image trong docker là gì: Đó là những phần mềm được quản lý bởi docker và không thể chỉnh sửa, image đóng gói các phần mềm như linux, mySQL...
  - Khi docker khởi chạy các images thì các phiên bản của image gọi là các container, container có thể ghi dữ liệu vào trong nó.
  - Để kiểm tra docker đang có các image nào thì mình sử dụng câu lệnh là "docker images". Lúc này, terminal sẽ show ra dạng bảng các image đang có 
  - Để tìm các image thì vào trang hub.docker.com hoặc dùng câu lệnh "docker search tenTuKhoa "
  - Để tải 1 image về thì dùng câu lệnh "docker pull tenImage:tenPhienBan(hoac để trống tag hoặc latest để lấy phiên bản mới nhất), tenPhienBan ở trong thẻ tag ở trang hub.docker.com.
  - Để xoá 1 image thì dùng câu lệnh "docker image rm tenImage:tenPhienBan" hoặc "docker image rm IDImageCanXoa "
#### 2. Lệnh run:
 - Để chạy các image thì dùng câu lệnh "docker run thamSoCuaLenh tenImage(hoac id cua image) commandMuonChay(optional) "
      - docker run -it idimage
 - Kiểm tra có container nào đang chạy : docker ps
 - Để vào 1 container nào đó: docker attach idcontainer
 - Để thoát và tắt container thì dùng lệnh exit, nếu thoát mà ko muốn dừng thì dùng ctrl P Q
 - Khi đứng ở root(host), muốn dừng 1 container nào đó thì dùng lệnh : docker stop id
 - Muốn xoá 1 container thì dùng : docker rm idcontainer
 - Có thể đặt tên cho container bằng -name, và đặt tên cho host bằng -h 


