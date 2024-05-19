# Docker

Docker官网地址  <https://www.docker.com/>

### Docker命令

#### 启动

```
systemctl start docker
```

#### 查看本地镜像

```shell
docker images
```

### 删除容器

Docker 提供了多种删除容器的指令，以下是一些常用的指令：

#### 删除单个容器

```html
docker rm <container_id>
```

这个指令用于删除指定的容器，其中 `<container_id>` 是容器的唯一标识符。你可以使用 `docker ps -a` 命令查看所有容器的列表及其对应的标识符。

#### 强制删除容器

```html
docker rm -f <container_id>
```

有时候，容器可能处于运行状态或者被其他容器所依赖，此时使用 `docker rm` 指令会报错。你可以使用 `-f` 参数来强制删除容器。

#### 删除所有停止的容器

```html
docker container prune
```

如果你想一次性删除所有停止的容器，你可以使用 `docker container prune` 命令。这个命令会删除所有已停止的容器，但是会保留正在运行的容器。

# Docker实例

### Docker安装Redis

#### 取最新版的 Redis 镜像

```shell
docker pull redis:latest
```

#### 查看本地镜像

docker images

#### 运行容器

docker run -itd --name redis -p 6379:6379 redis

#### 安装成功

docker ps命令查看容器运行情况

通过redis-cli连接测试使用redis服务

docker exec -it redis /bin/bash

![](Docker.assets/20240403125316.png)

exit退出容器

![](Docker.assets/20240403125425.png)

### Docker安装mysql:5.7

```shell
docker pull mysql:5.7

mkdir -p /home/mysql/mysql/logs
mkdir -p /home/mysql/mysql/data
mkdir -p /home/mysql/mysql/conf
#  CentOS 7 不建议用这个命令
docker run --name mysql5.7 \
--privileged=true \
-p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 \
-v /home/mysql/mysql/data:/var/lib/mysql \
-v /home/mysql/mysql/conf:/etc/mysql/conf.d \
-v /home/mysql/mysql/logs:/var/log/mysql \
-d mysql:5.7
```

### Docker安装mysql:8.0

```shell

#下载mysql8.0镜像
docker pull mysql:8.0
#创建映射路径
mkdir -p /home/mysql/mysql8.0/log
mkdir -p /home/mysql/mysql8.0/data
mkdir -p /home/mysql/mysql8.0/conf
#配置my.cnf
cd /home/mysql/mysql8.0/conf/
vi my.cnf
[client]
default-character-set=utf8mb4
[mysql]
default-character-set=utf8mb4
[mysqld]
# 设置东八区时区
default-time_zone = '+8:00'

#启动容器
docker run -p 3306:3306 --name mysql8.0 --restart=always --privileged=true \
-v /home/mysql/mysql8.0/log:/var/log/mysql \
-v /home/mysql/mysql8.0/data:/var/lib/mysql \
-v /home/mysql/mysql8.0/conf:/etc/mysql/conf.d \
-v /etc/localtime:/etc/localtime:ro \
-e MYSQL_ROOT_PASSWORD=123456 -d mysql:8.0
```

## Docker安装nginx

```shell
#拷贝文件
docker run -d -p 80:80 --name nginx nginx
cd /home/nginx/nginx_cq/conf/
docker container cp nginx:/etc/nginx/nginx.conf .
docker container cp nginx:/etc/nginx/conf.d ./conf.d
docker container cp nginx:/etc/nginx/mime.types .
docker rm -f nginx
#下载镜像
docker pull nginx:latest

#创建映射路径
mkdir -p /home/nginx/nginx_cq/html
#启动容器
docker run -p 80:80 --name nginx_cq --restart=always \
-v /home/nginx/nginx_cq/html:/usr/share/nginx/html \
-v /home/nginx/nginx_cq/conf:/etc/nginx \
-v /home/nginx/nginx_cq/logs:/var/log/nginx \
-d nginx:latest
```

