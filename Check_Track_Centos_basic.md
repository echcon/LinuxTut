# Kiểm tra đánh giá hiệu năng của CENTOS
### Kiểm tra thông số CPU
Bạn dùng lệnh “lscpu” để kiểm tra thông tin CPU

*[root@chithongn ~]# lscpu*
<code>Architecture:          x86_64  
CPU op-mode(s):        32-bit, 64-bit  
Byte Order:            Little Endian  
CPU(s):                1  
On-line CPU(s) list:   0  
Thread(s) per core:    1  
Core(s) per socket:    1  
Socket(s):             1  
NUMA node(s):          1  
Vendor ID:             GenuineIntel  
CPU family:            6  
Model:                 44  
Model name:            Westmere E56xx/L56xx/X56xx (Nehalem-C)  
Stepping:              1  
CPU MHz:               3392.144  
BogoMIPS:              6784.28  
Hypervisor vendor:     KVM  
Virtualization type:   full  
L1d cache:             32K  
L1i cache:             32K  
L2 cache:              4096K  
NUMA node0 CPU(s):     0  </code>
Bằng lệnh “lscpu” bạn có thể biết được các thông số cơ bản của CPU như Architecture,CPU(s),Thread(s) per core,CPU MHz,…

### Kiểm tra thông số của nhiều đơn vị phần cứng
Cài đặt:  <code># yum install -y lshw </code>

Chạy lệnh =>
<code>*# lshw -short*</code>
### Kiểm tra phân vùng ổ đĩa lưu trữ
Chạy lệnh: *# lsblk*
### Kiểm tra hiệu năng (benchmark performance)
**dd** là lệnh dùng để kiểm tra tốc độ đọc và ghi (read and write) của ổ cứng lưu trữ bằng cách tạo ra 1 GB dữ liệu ngẫu nhiên. Tốc độ (MB/s) càng cao càng tốt.
Chạy lệnh: <code>*dd if=/dev/zero of=test_chithongn bs=64k count=16k conv=fdatasync*</code>
*test_chithongn là file ghi nhận log được trả về theo lệnh*
### Kiểm tra tốc độ truy xuất của ổ cứng lưu trữ bằng lệnh “ioping”
Cài đặt: <code>*# yum install -y ioping;*</code>

Chạy lệnh: <code>*# ioping . -c 20;*</code>

<ul>
<li><b>iops</b> : có nghĩa là trong vòng 1 giây ổ cứng có thể thực hiện 887 lần truy vấn (đọc & ghi), con số này càng cao càng tốt</li>
<li>min/avg/max/mdev : tức là độ trễ trung bình (hoặc khoảng thời gian cần thiết để xử lý 1 truy vấn đọc hoặc ghi) của ổ cứng, con số này càng thấp càng tốt.</li>
</ul>
### Kiểm tra hiệu năng toàn diện Server bằng sysbench 

**Cài đặt Package:** <code># yum install -y sysbench</code>
Chạy lệnh: <code>*#sysbench --test=fileio --file-total-size=5G prepare*</code>
Thực hiện test:  
<code>*# sysbench --test=fileio --file-total-size=5G --file-test-mode=rndrw --i*</code>  
Xóa file sau khi test:  
<code>*# sysbench --test=fileio --file-total-size=5G cleanup*</code>

## Kiểm tra hiệu năng MySQL
* Cần tạo 1 database để test (ở đây mình tạo database có tên là “pep_test”), sau đó bạn chạy lệnh sau :<br/>
Chuẩn bị data để test:<br/>
    <code># sysbench --test=oltp --oltp-table-size=1000000 --db-driver=mysql --mys</code>  
Thực hiện test:<br/>
    <code>#sysbench --test=oltp --oltp-table-size=1000000 --db-driver=mysql --mys</code>  
Dọn sạch dữ liệu test<br/>
    <code># sysbench --test=oltp --db-driver=mysql --mysql-db=pep_test --mysql-user</code>  
