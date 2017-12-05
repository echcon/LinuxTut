# Kiểm tra đánh giá hiệu năng của CENTOS
### Kiểm tra thông số CPU
Bạn dùng lệnh “lscpu” để kiểm tra thông tin CPU

*[root@chithongn ~]# lscpu*

Bằng lệnh “lscpu” bạn có thể biết được các thông số cơ bản của CPU như Architecture,CPU(s),Thread(s) per core,CPU MHz,…

### Kiểm tra thông số của nhiều đơn vị phần cứng
Cài đặt:  yum install -y lshw 

Chạy lệnh =>
*# lshw -short*
### Kiểm tra phân vùng ổ đĩa lưu trữ
Chạy lệnh: *#lsblk*
