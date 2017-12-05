# Kiểm tra đánh giá hiệu năng của CENTOS
### Kiểm tra thông số CPU
Bạn dùng lệnh “lscpu” để kiểm tra thông tin CPU

[root@chithongn ~]# lscpu
Architecture:          x86_64
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
Model:                 45
Stepping:              7
CPU MHz:               1999.999
BogoMIPS:              3999.99
Virtualization:        VT-x
Hypervisor vendor:     KVM
Virtualization type:   full
L1d cache:             32K
L1i cache:             32K
L2 cache:              4096K
NUMA node0 CPU(s):     0

Bằng lệnh “lscpu” bạn có thể biết được các thông số cơ bản của CPU như Architecture,CPU(s),Thread(s) per core,CPU MHz,…

# Kiểm tra thông số của nhiều đơn vị phần cứng
Cài đặt:  yum install -y lshw 

Chạy lệnh 

\# lshw -short
