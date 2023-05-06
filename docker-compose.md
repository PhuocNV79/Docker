## Dinh nghia
- docker-compose: la cong cu dung de tao, them config cac container (co the goi la cac services) va chay cac container do cung 1 luc.
- duoc viet trong file docker-compose.yml
<img width="738" alt="image" src="https://user-images.githubusercontent.com/96764572/236610223-e111365d-c0c8-46c2-b2a6-84fab6f6e973.png">

## Command:
- **version**: chỉ ra phiên bản docker-compose đã sử dụng.
- **services**: thiết lập các services(containers) muốn cài đặt và chạy. Ở đây có 2 service tên là web và redis.
    - Đây là nơi khai báo tất cả các services được build trực tiếp từ images trên dockerhub hay build từ Dockerfile đã được tạo sẵn.
- **image**: chỉ ra image được sử dụng trong lúc tạo ra container.
- **build**: dùng để tạo container.
- **ports**: thiết lập ports chạy tại máy host và trong container.
- **restart**: tự động khởi chạy khi container bị tắt.
- **environment**: thiết lập biến môi trường ( thường sử dụng trong lúc config các thông số của db).
- **depends_on**: chỉ ra sự phụ thuộc. Tức là services nào phải được cài đặt và chạy trước thì service được config tại đó mới được chạy.
- **volumes**: dùng để mount hai thư mục trên host và container với nhau.
- - **networks**:
