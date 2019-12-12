## MySQL Cluster
I. Chuẩn bị:
* MySQL Cluster built base on 4+ server:
  * 01 server is responsible for managing cluster system: Management Node
  * 01 server is responsible for receiving queries to the cluster system: SQL Node
  * 02 server is responsible storage database cluster system: 02 Data Node
* Server is installed OS: Ubuntu 16.04 64 bit
* The first you must install MySQL Cluster: access the link to install 
[link](http://dev.mysql.com/downloads/cluster/)
* Choose platform: please select Linux – Generic
* Download MySQL cluster for Linux
* After download please move file to a directory. Ex: /var/download

II. Install package on server node
  1. SQL node:
     - You must create group & account on server: Group mysql, User mysql
     ```
     #> groupadd mysql
     #> useradd -g mysql mysql
     ```
     - Go to downloaded file, exstact & make a symbolic link with name mysql from directory mysql-cluster-gpl-7.6.12-linux-glibc2.12-x86_64
     ```
     #> tar -C /usr/local -xzvf mysql-cluster-gpl-7.6.12-linux-glibc2.12-x86_64.tar.gz
     #> ln -s mysql-cluster-gpl-7.6.12-linux-glibc2.12-x86_64 
     ```
     * please note some OS version 16.04 have not libaio library: please check & install it to initial database
     ```
     #> apt-get install libiao-dev
     ```
  2. Data node
     - Go to downloaded file: extract it & copy ndbd, ndbmtd to /usr/local/bin
      ```#> cd /var/tmp
      #> tar -zxvf mysql-cluster-gpl-7.6.12-linux-glibc2.12-x86_64.tar.gz
      #> cd mysql-cluster-gpl-7.6.12-linux-glibc2.12-x86_64
      #> cp bin/ndbd /usr/local/bin/ndbd
      #> cp bin/ndbmtd /usr/local/bin/ndbmtd
      ```
      - Point to directory copied file. Allow execute permission the file:
      ```
      #> chmod +x /usr/local/bin/ndbd /usr/local/bin/ndbmtd
      ```
  3. Management node
  
