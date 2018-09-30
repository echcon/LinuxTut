### SSH protocol
  > scp Test.tgz ubuntu@192.168.1.1:~/thongnc/ # upload file to server
  
  > scp thongnc@192.168.1.1:~/thongnc/Test.tgz ~/Download/ # download file from server

### Quản lý các tiến trình
Theo dõi/monitor sự hoạt động của các tiến trình là cần thiết khi ứng dụng đang hoạt động
#### Xem top các tiến trình đang hoạt động, sắp xếp theo cpu/mem/…
> top -o cpu

#### Xem tất cả các tiến trình
Dùng để in ra tất cả các tiến trình dưới dạng danh sách. Từ đó, ta có thể kết hợp với cơ chế pipe “|” để tìm kiếm, lọc ra các tiến trình ta muốn quan sát và xử lý.
> ps aux # liệt kê tất cả các tiến trình
> 
> ps aux | grep spark # tìm tiến trình tên spark 

ps = processes
a = xem tiến trình của all users
u = hiển thị tiến trình của user/owner
x = hiển thị các tiến trình khác

Tắt một tiến trình khi biết trước mã của tiến trình (pid)
kill –
> kill -9 process_id

Tắt một tiến trình khi biết trước một phần tên của tiến trình
pkill – -f

> pkill -15 -f spring

### Tìm kiếm bằng lệnh Zgrep/Grep

> find path expression # template tìm kiếm
> 
> find ~/Document -name "someimage.jpg" # ví dụ
> 
> find ~ -name *.plist -and -not -path *QuickTime* -and -not -path *Preferences* # kết hợp tìm kiếm loại trừ
