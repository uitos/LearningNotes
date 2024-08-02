# 安装

## 免安装版本

下载

> 下载地址 [Download MySQL Community Server](https://dev.mysql.com/downloads/mysql/)

解压

> D:\Program Files\MySQL\MySQL Server 8.0

配置环境变量

> 系统变量->新建系统变量
>
> 变量名
>
> MYSQL_HOME
>
> 变量值
>
> D:\Program Files\MySQL\MySQL Server 8.0
>
> 编辑（Path）环境变量->新建
>
> %MYSQL_HOME%\bin

配置 MySQL 的配置文件

```ini
#客户端部分
[client]

# pipe=

# socket=MYSQL
#指定MySQL服务器监听的TCP/IP端口。
port=3306

#Mysql部分
[mysql]
#当发生错误时，禁用蜂鸣声提示。
no-beep

# default-character-set=

# server_type=3

#Mysqld部分
[mysqld]

# The next three options are mutually exclusive to SERVER_PORT below.
# skip-networking
# enable-named-pipe
# shared-memory

# shared-memory-base-name=MYSQL

# The Pipe the MySQL Server will use
# socket=MYSQL

#再次声明MySQL服务器的TCP/IP端口。
port=3306

#设定数据库根目录路径。
# basedir="D:/Program Files/MySQL/MySQL Server 8.0/"

# Path to the database root
datadir=D:/Program Files/MySQLData/MySQL Server 8.0\Data

# The default character set that will be used when a new schema or table is
# created and no character set is defined
# character-set-server=

#设定默认的存储引擎为InnoDB。
default-storage-engine=INNODB

#设置SQL模式为严格模式，确保事务表遵循严格的标准，不使用替代存储引擎。
sql-mode="STRICT_TRANS_TABLES,NO_ENGINE_SUBSTITUTION"

#日志输出方式为文件。
log-output=FILE

#关闭一般查询日志。
general-log=0

#指定一般查询日志文件名。
general_log_file="LAPTOP-JFFS3BI2.log"

#开启慢查询日志。
slow-query-log=1

#指定慢查询日志文件名。
slow_query_log_file="LAPTOP-JFFS3BI2-slow.log"

#设定慢查询时间阈值为10秒。
long_query_time=10

#指定错误日志文件名。
log-error="LAPTOP-JFFS3BI2.err"

# ***** Group Replication Related *****
#指定二进制日志基名，用于备份和复制。
log-bin="LAPTOP-JFFS3BI2-bin"

# ***** Group Replication Related *****
#设定服务器ID，对于复制拓扑结构中的服务器，必须指定唯一的服务器ID。
server-id=1

# ***** Group Replication Related *****
# The host name or IP address of the replica to be reported to the source
# during replica registration. This value appears in the output of SHOW REPLICAS
# on the source server. Leave the value unset if you do not want the replica to
# register itself with the source.
# report_host=0.0

#设定表名和数据库名一律小写。
lower_case_table_names=1

#设定安全文件导入导出权限。
secure-file-priv="D:/Program Files/MySQLData/MySQL Server 8.0/Uploads"

#设定最大并发会话数。
max_connections=151

#设定所有线程可打开的表数，增加此值可以提高打开大量表时的性能。
table_open_cache=2000

#设定内存临时表的最大尺寸，超过此值将转为基于磁盘的表。
tmp_table_size=105M

#设定线程缓存大小，用于重用断开连接的客户端线程，减少线程创建。
thread_cache_size=10

#*** MyISAM Specific options
#设定MyISAM索引重建时允许使用的最大临时文件大小。
myisam_max_sort_file_size=100G

#设定用于排序MyISAM索引的缓冲区大小。
myisam_sort_buffer_size=200M

#设定MyISAM表索引缓存大小
key_buffer_size=8M

#设定读取MyISAM表全表扫描时的缓冲区大小。
read_buffer_size=64K

#设定随机读取MyISAM表时的缓冲区大小。
read_rnd_buffer_size=256K

#*** INNODB Specific options ***
# innodb_data_home_dir=

# Use this option if you have a MySQL server with InnoDB support enabled
# but you do not plan to use it. This will save memory and disk space
# and speed up some things.
# skip-innodb

#设定InnoDB在每次提交时刷新日志到磁盘，确保ACID特性。
innodb_flush_log_at_trx_commit=1

#设置InnoDB日志缓冲区的大小为1M，用于缓存日志数据，以减少磁盘I/O操作。
innodb_log_buffer_size=1M

#设置InnoDB缓冲池的大小为8M，用于缓存索引和数据页，减少磁盘I/O操作。
innodb_buffer_pool_size=8M

#设置InnoDB日志文件的大小为48M，日志文件用于记录事务的修改操作，以便在系统崩溃时进行恢复。
innodb_log_file_size=48M

#设置InnoDB内核允许的最大线程并发数为33，以避免过多的线程竞争导致性能下降。
innodb_thread_concurrency=33

#置InnoDB表空间文件自动扩展的增量为64M。
innodb_autoextend_increment=64

#将InnoDB缓冲池划分为8个区域，以减少缓存争用。
innodb_buffer_pool_instances=8

#设置InnoDB并发控制的票数为5000，用于控制进入InnoDB内核的线程数量。
innodb_concurrency_tickets=5000

#设置InnoDB中旧数据块在旧列表中保留的时间为1000ms。
innodb_old_blocks_time=1000

#设置InnoDB能够同时打开的文件数为300。
innodb_open_files=300

#禁止在元数据语句中更新InnoDB的统计信息。
innodb_stats_on_metadata=0

#将每个InnoDB表的数据和索引存储在单独的.ibd文件中，而不是系统表空间中。
innodb_file_per_table=1

#设置InnoDB的校验和算法为crc32
innodb_checksum_algorithm=0

#设置MySQL能够处理的连接请求队列的长度为80。
back_log=80

#禁止定期刷新缓冲池和日志文件到磁盘。
flush_time=0

#设置连接缓冲区的大小为256K。
join_buffer_size=256K

#设置最大允许的数据包大小为4M。
max_allowed_packet=4M

#设置最大允许的连接错误次数为100。
max_connect_errors=100

#设置MySQL能够打开的文件数限制为4161。
open_files_limit=4161

#设置排序缓冲区的大小为256K。
sort_buffer_size=256K

#设置表定义缓存的大小为1400。
table_definition_cache=1400

#设置行式二进制日志事件的最大大小为8K
binlog_row_event_max_size=8K

#设置中继日志同步到磁盘的间隔为10000次写入。
sync_relay_log=10000

#设置中继日志信息文件同步到磁盘的间隔为10000次事务。
sync_relay_log_info=10000

#设置MySQLX协议监听的端口号为33060。
loose_mysqlx_port=33060

```

初始化data目录

> cmd管理员
>
> cd到ini文件下

```shell
mysqld --initialize-insecure
```

启动mysql服务

```shell
net start mysql
```

登录mysql

```shell
mysql -u root -p
```

查询用户密码

> 查询用户密码命令：

```mysql
select host,user,authentication_string from mysql.user;
```

host： 允许用户登录的ip；
user：当前数据库的用户名；
authentication_string： 用户密码；
如果没密码， root 这一行应该是空的。

设置root用户密码
  注意：在MySQL 5.7.9以后废弃了password字段和password()函数
步骤1.如果当前root用户authentication_string字段下有内容，先将其设置为空，没有就跳到步骤 2。

```mysql
use mysql; 
update user set authentication_string='' where user='root'
```

步骤2.使用ALTER修改root用户密码为123456

```mysql
use mysql；
ALTER user 'root'@'localhost' IDENTIFIED BY '123456';
FLUSH PRIVILEGES;
```

命令

自动生成无密码的root用户；

```shell
mysqld –initialize-insecure
```

自动生成带随机密码的root用户；

```shell
mysqld –initialize
```

移除自己的mysqld服务；

```shell
mysqld -remove
```

命令，停止mysql服务

```shell
net stop mysql
```

启动服务报错

```shell
D:\Program Files\MySQLData\MySQL Server 8.0>net start mysql
MySQL 服务正在启动 .
MySQL 服务无法启动。

服务没有报告任何错误。

请键入 NET HELPMSG 3534 以获得更多的帮助。
```

重新执行初始化data目录

```shell
mysqld --initialize-insecure
```

