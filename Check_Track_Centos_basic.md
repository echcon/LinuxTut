# Kiểm tra đánh giá hiệu năng của CENTOS
### Kiểm tra thông số CPU
Bạn dùng lệnh “lscpu” để kiểm tra thông tin CPU

*[root@chithongn ~]# lscpu*
Architecture:          x86_64<br/>
CPU op-mode(s):        32-bit, 64-bit<br/>
Byte Order:            Little Endian<br/>
CPU(s):                1<br/>
On-line CPU(s) list:   0<br/>
Thread(s) per core:    1<br/>
Core(s) per socket:    1<br/>
Socket(s):             1<br/>
NUMA node(s):          1<br/>
Vendor ID:             GenuineIntel<br/>
CPU family:            6<br/>
Model:                 44<br/>
Model name:            Westmere E56xx/L56xx/X56xx (Nehalem-C)<br/>
Stepping:              1<br/>
CPU MHz:               3392.144<br/>
BogoMIPS:              6784.28<br/>
Hypervisor vendor:     KVM<br/>
Virtualization type:   full<br/>
L1d cache:             32K<br/>
L1i cache:             32K<br/>
L2 cache:              4096K<br/>
NUMA node0 CPU(s):     0<br/>
Bằng lệnh “lscpu” bạn có thể biết được các thông số cơ bản của CPU như Architecture,CPU(s),Thread(s) per core,CPU MHz,…

### Kiểm tra thông số của nhiều đơn vị phần cứng
Cài đặt:  yum install -y lshw 

Chạy lệnh =>
*# lshw -short*
### Kiểm tra phân vùng ổ đĩa lưu trữ
Chạy lệnh: *# lsblk*
### Kiểm tra hiệu năng (benchmark performance)
**dd** là lệnh dùng để kiểm tra tốc độ đọc và ghi (read and write) của ổ cứng lưu trữ bằng cách tạo ra 1 GB dữ liệu ngẫu nhiên. Tốc độ (MB/s) càng cao càng tốt.
Chạy lệnh: *dd if=/dev/zero of=test_chithongn bs=64k count=16k conv=fdatasync*
*test_chithongn là file ghi nhận log được trả về theo lệnh*
### Kiểm tra tốc độ truy xuất của ổ cứng lưu trữ bằng lệnh “ioping”
Cài đặt: *# yum install -y ioping;*

Chạy lệnh: *# ioping . -c 20;*

<ul>
<li><b>iops</b> : có nghĩa là trong vòng 1 giây ổ cứng có thể thực hiện 887 lần truy vấn (đọc & ghi), con số này càng cao càng tốt</li>
<li>min/avg/max/mdev : tức là độ trễ trung bình (hoặc khoảng thời gian cần thiết để xử lý 1 truy vấn đọc hoặc ghi) của ổ cứng, con số này càng thấp càng tốt.</li>
</ul>
### Kiểm tra hiệu năng toàn diện Server bằng sysbench 

**Cài đặt Package:** # yum install -y sysbench
Chạy lệnh: *#sysbench --test=fileio --file-total-size=5G prepare*<br/>
Thực hiện test
*# sysbench --test=fileio --file-total-size=5G --file-test-mode=rndrw --i*
Xóa file sau khi test<br/>
*# sysbench --test=fileio --file-total-size=5G cleanup* <br/>

----
## Kiểm tra hiệu năng MySQL
* Cần tạo 1 database để test (ở đây mình tạo database có tên là “pep_test”), sau đó bạn chạy lệnh sau :<br/>
Chuẩn bị data để test:<br/>
    <code># sysbench --test=oltp --oltp-table-size=1000000 --db-driver=mysql --mys</code>
