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

### Quan sát log file
> Dùng các lệnh cat, less, vi, vim

### Sử dụng lệnh tail/head
tail/head là hai lệnh tương tự nhau, một lệnh để xem các dòng cuối của file và một lệnh để xem các dòng đầu tiên của file.
> tail error.log # xem top 10 dòng cuối file

> tail -n 100 error.log # xem top 100 dòng cuối file


> tail -n 100 error.log | more # xem top 100 dòng cuối file, đọc theo định dạng của lệnh less

### Nén và giải nén file
zip -r archive_name.zip folder_to_compress # To compress
unzip archive_name.zip # To extract
zip -r -X archive_name.zip folder_to_compress # make a zip without those invisible Mac resource files such as “_MACOSX” or “._Filename” and .ds store files, use the “-X” option.
 
#### TAR.GZ – Cross Platform
>tar -zcvf archive_name.tar.gz folder_to_compress # To compress

>tar -zxvf archive_name.tar.gz # To extract
 
#### TAR.BZ2 – Cross Platform
>tar -jcvf archive_name.tar.bz2 folder_to_compress # To compress

>tar -jxvf archive_name.tar.bz2 # To extract
 
#### GZ
>gzip folder_to_compress # To compress

>gunzip archivename.gz # To extract

### Xem lịch sử lệnh đã làm
> history

### Tạo folder 
> mkdir
> 
> mkdir -p webapp/application/controllers

### So sanh nội dung, đếm số từ trong file
> diff
> 
> wc apache/access.log

### Xem lịch
> cal # xem tháng hiện tại

> cal 9 2018 # xem lịch tháng 9 - 2018

> cal -y 2018 # Xem toàn bộ lịch năm 2018
