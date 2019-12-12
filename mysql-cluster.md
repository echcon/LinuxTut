## MySQL Cluster
I. **Chuẩn bị:**
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

II. **Install package on server node**
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
     - please note some OS version 16.04 have not libaio library: please check & install it to initial database
     ```
     #> apt-get install libiao-dev
     ```
     - Point to mysql directory & run script to initial database system.
     ```
     #> cd /usr/local/mysql
     #> scripts/mysql_install_db --user=mysql```
     - Grant permission for MySQL
     ```
     #> chown -R root.
     #> chown -R mysql data
     #> chgrp -R mysql  ```
     - Copy startup script to a directory, allow more permission execute, create trigger Initial when system start
     ```
     #> systemctl enabled /etc/init.d/mysql.server
     ```
  2. Data node
     - Go to downloaded file: extract it & copy ndbd, ndbmtd to /usr/local/bin
      ```#> cd /var/download
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
     - Go to downloaded file: extract it & copy ndb_mgmd, ndb_mgm to /usr/local/bin
      ```#> cd /var/download
      #> tar -zxvf mysql-cluster-gpl-7.6.12-linux-glibc2.12-x86_64.tar.gz
      #> cd mysql-cluster-gpl-7.6.12-linux-glibc2.12-x86_64
      #> cp bin/ndb_mgm /usr/local/bin/ndb_mgm
      #> cp bin/ndb_mgmd /usr/local/bin/ndb_mgmd
      ```
      - Point to directory copied file. Allow execute permission the file:
      ```
      #> chmod +x /usr/local/bin/ndb_mgm /usr/local/bin/ndb_mgmd
      ```
 III. **MySQL Cluster config:**
   -  On data node / sql node need 01 file my.cnf to include management node and parameter enable NDBCluster on host
   1. Create config file of Data nodes & SQL node
      ```
      #> vi /etc/my.cnf
         [mysqld]
         # Options for mysqld process:
         ndbcluster # run NDB storage engine
         [mysql_cluster]
         # Options for MySQL Cluster processes:
         ndb-connectstring=172.17.0.10:1186 # location of management server
      ```
   2. Create config file of Management node
      - File config on Management node include total number server data node, total memory, storage volumn and index per data node, address data node and sql node, data path on data node
      - Create a directory include config file
      shell> mkdir /var/lib/mysql-cluster
      shell> cd /var/lib/mysql-cluster
      shell> vi config.ini
      - At management node, config file:
      ```
      [ndbd default]
      # Options affecting ndbd processes on all data nodes:
      NoOfReplicas=2 # Number of replicas
      DataMemory=1024M # How much memory to allocate for data storage
      IndexMemory=128M # How much memory to allocate for index storage
      # For DataMemory and IndexMemory, we have used the
      # default values. Since the "world" database takes up
      # only about 500KB, this should be more than enough for
      # this example Cluster setup.
      [tcp default]
      # TCP/IP options:
      portnumber=2288 # This the default; however, you can use any
      # port that is free for all the hosts in the cluster
      # Note: It is recommended that you do not specify the port
      # number at all and simply allow the default value to be used instead
      [ndb_mgmd]
      # Management process options:
      hostname=172.17.0.10 # Hostname or IP address of MGM node
      datadir=/var/lib/mysql-cluster # Directory for MGM node log files
      [ndbd]
      # Options for data node "A":
      # (one [ndbd] section per data node)
      hostname=172.17.0.40 # Hostname or IP address
      datadir=/usr/local/mysql/data # Directory for this data node's data files
      [ndbd]
      # Options for data node "B":
      hostname=172.17.0.41 # Hostname or IP address
      datadir=/usr/local/mysql/data # Directory for this data node's data files
      [mysqld]
      # SQL node options:
      hostname=172.17.0.30 # Hostname or IP address
      # (additional mysqld connections can be
      # specified for this node for various
      # purposes such as running ndb_restore)
      ```
   
 IV. **MySQL Cluster START**
   * System MySQL Cluster is starting in the order:
     - Start MySQL Cluster on management node
     - Next, start MySQL Cluster on data node
     - Then, start MySQL Cluster on sql node
   1. Start MySQL Cluster on Management node
      ```
      #> ndb_mgmd -f /var/lib/mysql-cluster/config.ini
      ```
   2. Start Data node
      ```
      #> ndbd
      ```
   3. Start SQL node
      ```
      #> /etc/init.d/mysql.server start
      ```
   4. Monitor MySQL Cluster after start on nodes
      When MySQL nodes is started: system is worked. You can check Mângêmnt node by command ndb_mgm.
      ```
      #> ndb_mgm
      ndb_mgm> show
      ```
      The list all nodes will be show the screen.
      
