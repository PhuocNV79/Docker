# Huong dan su dung docker file
(https://viblo.asia/p/tim-hieu-ve-dockerfile-va-tao-docker-image-V3m5WWag5O7)

(https://hocchudong.com/docker-phan-3-huong-dan-su-dung-dockerfile-de-build-image/)
### Gioi thieu:
- Docker co the build 1 image tu cac chi thi (instruction) tu dockerfile.
- Dockerfile la 1 file text, khong co extension, dockerfile bao gom tat ca cac cau lenh co the chay tu commandline

### Chi thi (Instructions) trong dockerfile
- Cac chi thi thuong duoc VIET HOA
- **FROM** : Từ image nào đó làm image cơ sở , để thực hiện các lệnh tiếp theo
- **LABEL**: Chỉ thị LABEL được dùng để thêm các thông tin meta vào Docker Image khi chúng được build. 
  - Chúng tồn tại dưới dạng các cặp key - value, được lưu trữ dưới dạng chuỗi. 
  - Có thể chỉ định nhiều label cho một Docker Image, và tất nhiên mỗi cặp key - value phải là duy nhất.
  - Bạn có thể khai báo metadata cho Image theo từng dòng chỉ thị hoặc có thể tách ra khai báo thành từng dòng riêng biệt.
- **MAINTAINER** : Chỉ thị MAINTAINER dùng để khai báo thông tin tác giả người viết ra file Dockerfile.
  - Theo tài liệu chính thức từ bên phía Docker thì việc khai báo MAINTAINER đang dần được thay thế bằng LABEL maintainer bới tính linh hoạt của nó.
- **RUN** : Chỉ thị RUN dùng để chạy một lệnh nào đó trong quá trình build image và thường là các câu lệnh Linux. 
  - Tùy vào image gốc được khai báo trong phần FROM thì sẽ có các câu lệnh tương ứng.
  -  Ví dụ, để chạy câu lệnh update đối với Ubuntu sẽ là RUN apt-get update -y còn đối với CentOS thì sẽ là Run yum update -y. 
  - Kết quả của câu lệnh sẽ được commit lại, kết quả commit đó sẽ được sử dụng trong bước tiếp theo của Dockerfile.
  - <img width="738" alt="image" src="https://user-images.githubusercontent.com/96764572/236108559-774c55ac-2385-46ec-9488-01ec2fca6580.png">

- **ADD** : Chỉ thị ADD sẽ thực hiện sao chép các tập, thư mục từ máy đang build hoặc remote file URLs từ src và thêm chúng vào filesystem của image dest.
- **COPY** : Chỉ thị COPY cũng giống với ADD là copy file, thư mục từ <src> và thêm chúng vào <dest> của container. Khác với ADD, nó không hỗ trợ thêm các file remote file URLs từ các nguồn trên mạng.
    - COPY [--chown=user:group] src... dest
    - COPY [--chown=user:group] ["src",... "dest"]
- **ENV** : Chỉ thị ENV dùng để khai báo các biến môi trường. 
    Các biến này được khai báo dưới dạng key - value bằng các chuỗi. 
    Giá trị của các biến này sẽ có hiện hữu cho các chỉ thị tiếp theo của Dockerfile.
