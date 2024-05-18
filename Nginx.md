# Nginx负载均衡

目的：提升吞吐率，提高请求性能，提高高容灾

### 负载均衡的几种方式

1. 轮询（默认）

```conf
#每个请求按时间顺序逐一分配到不同后端服务器
upstream server_list{
    server localhost:8080;
    server localhost:9999;
}
```
2. weight加权轮询
```conf
#weight代表权重，默认为1，权重越高被分配的客户端越多
#指定轮询几率，weight和访问比率成正比，用于后端服务器性能不均的情况
upstream server_list{
    server localhost:8080 weight=5;
    server localhost:9999 weight=1;
}
```
4. ip_hash
```conf
#每个请求按照ip的hash值分配，这样每个访问的客户端会固定访问一个后端服务器，可以解决会话Session丢失问题
#不管刷新多少遍，始终访问的是同一台tomcat服务器
upstream backserver { 
		ip_hash; 
		server 127.0.0.1:8080; 
		server 127.0.0.1:9090; 
}
```
5. url_hash

```conf
按照访问URL的hash结果分配
upstream backserver { 
		hash $request_uri;
		server 127.0.0.1:8080; 
		server 127.0.0.1:9090; 
}
```

6. 最少连接
```conf
#web请求会被转发到连接数最少的服务器上
upstream backserver { 
		least_conn;
		server 127.0.0.1:8080; 
		server 127.0.0.1:9090; 
}
```

### Nginx负载均衡调度策略

| 调度算法     | 概述                                                         |
| ------------ | :----------------------------------------------------------- |
| 轮询         | 逐一轮询，默认方式                                           |
| weight       | 加权轮询，weight越大，分配的几率越高                         |
| ip_hash      | 按照访问IP的hash结果分配，会导致来自同一IP的请求访问固定的一个后台服务器 |
| url_hash     | 按照访问URL的hash结果分配                                    |
| least_conn   | 最少链接数，那个服务器链接数少就会给分配                     |
| hash关键数值 | hash自定义的key                                              |