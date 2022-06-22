# DOCKER
## D01, D02 Tìm hiểu về Docker Image, chạy 1 container
- Docker là công cụ tạo các vùng cách ly để chạy 1 ứng dụng

### Các lệnh của Docker:
- Để sử dụng docker trong terminal thì lệnh bắt đầu la "docker", theo sau là những lệnh con.
- Ví dụ: docker image --help: để xem docker hướng dẫn về lệnh image
 #### 1. Lệnh images:
  - Image trong docker là gì: Đó là những phần mềm được quản lý bởi docker và không thể chỉnh sửa, image đóng gói các phần mềm như linux, mySQL...
  - Khi docker khởi chạy các images thì các phiên bản của image gọi là các container, container có thể ghi dữ liệu vào trong nó.
  - `docker images` : Để kiểm tra docker đang có các image nào thì mình sử dụng câu lệnh là "docker images". Lúc này, terminal sẽ show ra dạng bảng các image đang có 
  - `docker search tenTuKhoa` : Để tìm các image thì vào trang hub.docker.com hoặc dùng câu lệnh "docker search tenTuKhoa "
  - `docker pull tenImage:tenPhienBan`: Để tải 1 image về thì dùng câu lệnh `docker pull tenImage:tenPhienBan`(hoac để trống tag hoặc latest để lấy phiên bản mới nhất), tenPhienBan ở trong thẻ tag ở trang hub.docker.com.
  - `docker image rm tenImage:tenPhienBan" hoặc "docker image rm IDImageCanXoa` : Để xoá 1 image ;
#### 2. Lệnh run:
 - `docker run thamSoCuaLenh tenImage(hoac id cua image) commandMuonChay(optional)` : Để chạy các image thì dùng câu lệnh;
      - ex: docker run -it --name "ABC" idimage
      - `-i` : co the tuong tac interact
      - `-t` : ket noi voi terminal
 - `docker ps` : Kiểm tra có container nào đang chạy;
 - `docker start idcontainer` : start container đang off, co the start nhieu container cung luc;
 - `docker attach idcontainer` : Để vào 1 container nào đó;
 - Để thoát và tắt container thì dùng lệnh `exit`, nếu thoát mà ko muốn dừng thì dùng `ctrl P Q`;
 - `docker stop id` : Khi đứng ở root(host), muốn dừng 1 container nào đó thì dùng lệnh;
 - `docker rm idcontainer` : Muốn xoá 1 container thì dùng; `-f` dung de lam gi
 - Có thể đặt tên cho container bằng --name, và đặt tên cho host bằng -h `docker run -it --name "ABC" -h "hostName" idimage `


***
## D03: Docker exec, lưu container thành image, xuất image thành file

### Docker exec
- `docker exec -it tenContainer cauLenh` : Khi đứng ở ngoài 1 container mà muốn chạy app ở trong nó

### Docker commit
- `docker commit tenContainer (hoac id) tenImageMuonDat:tenTagMuonDat`: Lưu container thành image
- `docker save --output tenFileMuonLuu.tar` tenImageMuonLuu (hoac id)` : Lưu image thành file để chuyển cho máy khác
- `docker load -i tenFileImage.tar` : Load 1 file image.tar trở thành 1 image;
- `docker tag idImage tenimageMuonDat:tenTagMuonDat` : Khi load 1 image lên. nó chưa có tên và tag. dùng lệnh này để đặt tên cho nó;

## D04: Chia se du lieu trong Docker, tao va quan ly o dia docker volume

- `docker run -it -v pathHost:pathContainer idImage` : chia se du lieu tu may host cho container
- `docker run -it --name tenContainerMuonTao --volumes-from idContainerTruoc idImage` : mong muon container tenContainerMuonTao doc duoc du lieu giong du container C1, tenContainerMuonTao duoc tao tu image id idImage, C1 idContainerTruoc
- `docker volume ls` : kiem tra dang co nhung o dia nao trong docker
- `docker volume create tenODia` : tao 1 o dia moi
- `docker volume inspect tenODia` : kiem tra thong tin o dia
- `docker volume rm tenODia` : xoa o dia tenODia
- `docker run -it --mount source=DISK, target=pathContainer imageID`: gan o dia D2 vao container, de container luu du lieu co dinh o trong do
- `docker volume create --opt device=pathHost --opt type=none --opt o=bind tenODiaMuonTao` : tao 1 o dia, chia se du lieu may host voi o dia do
- `docker run -it -v tenODia:pathContainer idImage` : gan o dia duoc tao o phia tren, vao container
- 
## D05: Network trong docker

- `docker network ls` : kiem tra xem trong docker co nhung networks nao
- `docker network inspect tenNetwork` : kiem tra thong tin network
- `wget -O -ipCOntainer2` : Khởi chạy máy chủ web ở Container 2 từ Container 1. 2 container này dùng cùng mạng cầu
- `docker run -it --name tenContainerMuonDat -p congMayHost:congContainer imageDetaoContainer` : tao 1 container, anh xa cong may host vao cong trong container
- `docker network create --driver bridge tenNetWork` : Tao ra 1 network co drive la bridge
- `docker network rm tenNetwork` : xoa 1 network 
- `docker network connect tenNetwork tenHoacIdContainerMuonketnoi` : Ket noi 1 container vao 1 mang nao do

## D06 : Cài đặt, tạo, chạy PHP trong containter

- `docker run -d --name tenContainer -h tenHost -v pathHost:pathContainer --network tenNetwork tenImage:tag` : tao container va chạy nền
 + Chú ý : folder phải được share với docker nếu ko sẽ ra lỗi `Mount denied`
- `docker exec -it tenContainer bash` : chay bash trong tenContainer
- uncomment mod_proxy : Khi truy van den cac file co duoi .php thi apache se yeu cau server chay php-fpm thuc hien file do. De thuc hien duoc thi chung ta can nap cac modul cua proxy 
  + `mod_proxy` : nap module proxy
  + AddHandler : yeu cau apache chay php thong qua proxy 

## D10 : Tra cuu thong tin image, container, giam sat hoat dong
- `docker image history idHoacNameContainer` : kiem tra lich su hinh thanh cua images
- `docker logs idHoactenContainer` : kiem tra file log cua container
- `docker logs --tail soDong idhoacTenContainer` : lay soDong cuoi cua file log
- `docker logs -f idContainer` : phat sinh log realtime
- `docker stats idhoacTenContainer` : kiem tra container do su dung tai nguyen may host
