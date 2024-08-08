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



配置 MySQL 的配置文件my.ini

```ini
[mysql]
default-character-set=utf8
[mysqld]
# 设置3306端口
port = 3306
# 设置mysql的安装目录
basedir = D:/Program Files/MySQL/MySQL Server 8.0/
# 设置mysql数据库的数据的存放目录
datadir=D:/Program Files/MySQLData/MySQL Server 8.0\Data
# 允许最大连接数
max_connections=20
# 服务端使用的字符集默认为8比特编码的latin1字符集
character-set-server=utf8
# 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB
# 创建模式
sql_mode = NO_ENGINE_SUBSTITUTION,STRICT_TRANS_TABLES

```

安装mysqld服务

```shell
mysqld --install
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

# 基本概念



# 基本操作

## 可操作对象有哪些？

数据库（database）

表（table）

行（row）

列（column）

## 操作库



## 操作表

## 数据增删改

## 数据查询

### 简单查询

​		基本语法
​			select ... from 表名
​		别名
​			select 列名 [as] 列别名  from 表名 [as] 表别名
​		去重关键字
​			select distinct 列名 from 表名

### 条件查询

​		select ... from 表名 where 条件
​			关系运算符
​			in关键字
​				select ... from 表名 where 列名 in(值1,值2..);
​			between关键字
​				select ... from 表名 where 列名 between 较小的值 and  较大的的值
​			is null关键字
​				is null  为空
​				is not null  不为空
​			逻辑运算符
​				and
​				or
​				not
​					取反
​						常与In ，between连用
​							not in（）
​							not between 
​			like关键字
​				_ 单个任意字符
​				% 多个任意字符

### 聚合函数

​		会忽略掉值为null行
​		count
​			返回某列的行数
​				如果是count（*）使用*通配符则代表统计所有符合条件的行数，包括null
​				单独统计某列 count（列名），会忽略掉值为null的列
​		max
​		min
​		sum
​		avg
​		还有大量函数.....
​	分组
​		select 分组列,聚合函数() from 表名 group by 分组 having 分组后条件
​			where在分组前条件过滤，不能使用聚合函数
​			having在分组后条件过滤，可以使用聚合函数

### 排序

​		select ... from 表名 order by 排序列 [asc | desc]
​			asc 升序 默认值
​			desc 降序

### 限制结果

​		select ... from 表名 where  ....  limit 个数（取结果前几个）

### 分页

​		select ... from 表名 limit 开始行数,检索行数





