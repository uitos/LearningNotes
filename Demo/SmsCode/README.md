

![image-20250106151255086](images/image-20250106151255086.png)

![image-20250106151105448](images/image-20250106151105448.png)

![image-20240814201409545](images/image-20240814201409545.png)

![image-20240814200720453](images/image-20240814200720453.png)

![image-20250106151653407](images/image-20250106151653407.png)

添加基础Maven依赖

```xml
<dependencies>
		<!-- 添加Spring Boot Web模块依赖，用于创建Web应用程序 -->
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-web</artifactId>
		</dependency>
		
		<!-- 添加MyBatis Spring Boot启动器依赖，用于集成MyBatis框架 -->
		<dependency>
			<groupId>org.mybatis.spring.boot</groupId>
			<artifactId>mybatis-spring-boot-starter</artifactId>
			<version>3.0.4</version>
		</dependency>
		
		<!-- 添加MySQL数据库连接器依赖，用于在运行时与MySQL数据库通信 -->
		<dependency>
			<groupId>com.mysql</groupId>
			<artifactId>mysql-connector-j</artifactId>
			<scope>runtime</scope>
		</dependency>
		
		<!-- 添加Spring Boot配置处理器依赖，用于辅助配置元数据的生成 -->
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-configuration-processor</artifactId>
			<optional>true</optional>
		</dependency>
		
		<!-- 添加Lombok依赖，用于简化代码编写，如自动getter和setter等 -->
		<dependency>
			<groupId>org.projectlombok</groupId>
			<artifactId>lombok</artifactId>
			<optional>true</optional>
		</dependency>
		
		<!-- 添加Spring Boot Redis数据模块依赖，用于集成Redis数据库 -->
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-data-redis</artifactId>
		</dependency>
		
		<!-- 添加Spring Boot测试模块依赖，用于进行单元测试和集成测试 -->
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-test</artifactId>
			<scope>test</scope>
		</dependency>
		
		<!-- 添加MyBatis Spring Boot测试启动器依赖，用于测试MyBatis集成情况 -->
		<dependency>
			<groupId>org.mybatis.spring.boot</groupId>
			<artifactId>mybatis-spring-boot-starter-test</artifactId>
			<version>3.0.4</version>
			<scope>test</scope>
		</dependency>
    
	</dependencies>
```

添加阿里云短信Maven依赖

```xml
<dependency>
  <groupId>com.aliyun</groupId>
  <artifactId>dysmsapi20170525</artifactId>
  <version>3.1.0</version>
</dependency>
```

添加yml配置

```yaml
# 配置服务器端口
server:
  port: 8080           # 设置HTTP服务器的监听端口为8080
# Spring框架相关配置
spring:
  # MySQL 数据库连接配置
  datasource:
    driver-class-name: com.mysql.cj.jdbc.Driver
    url: jdbc:mysql://localhost:3306/sms_code_demo?useUnicode=true&characterEncoding=UTF-8&serverTimezone=Asia/Shanghai
    username: root
    password: 123456
  # Redis 缓存配置
  data:
    redis:
      host: localhost
      port: 6379
      #password:                  # 如果Redis设置了密码，请在此处填写
      lettuce:
        pool:
          max-active: 8          # 设置Redis连接池的最大活跃连接数
          max-wait: -1           # 设置Redis连接池获取连接的最大等待时间，-1表示无限等待
          max-idle: 8            # 设置Redis连接池的最大空闲连接数
          min-idle: 0            # 设置Redis连接池的最小空闲连接数
  # Jackson配置，用于JSON序列化和反序列化
  jackson:
    date-format: yyyy-MM-dd HH:mm:ss  # 设置日期格式
    time-zone: Asia/Shanghai          # 设置时区

# MyBatis框架配置
mybatis:
  type-aliases-package: com.example.demo.entity  # 设置实体类包路径
  mapper-locations: classpath*:mapper/*.xml      # 设置Mapper XML文件路径
  configuration:
    map-underscore-to-camel-case: true           # 开启下划线到驼峰命名的自动转换

# 日志配置
logging:
  level:
    root: info          # 设置全局日志级别为info
    org.springframework.web: debug  # 设置Spring Web的日志级别为debug
    com.example.demo: debug         # 设置项目自身的日志级别为debug
  file:
    name: logs/sms-codedemo.log     # 设置日志文件路径和名称
```

添加阿里云配置

```yaml
aliyun:
  sms:
    accessKeyId: "****5tBMw44ydJPF3****"
    accessKeySecret: "*****xJKruVxcLJs5b7d****"
    signName: "短信接口"
    templateCode: "SMS_476795235"
```



阿里云官方示例代码[阿里云官方示例代码地址](https://help.aliyun.com/zh/sms/developer-reference/using-the-openapi-example?spm=a2c4g.11186623.help-menu-44282.d_4_4_0.44af5634O5Mi5f&scm=20140722.H_2411226._.OR_help-T_cn~zh-V_1)

```java
package com.aliyun.sample;

import com.aliyun.teaopenapi.models.Config;
import com.aliyun.dysmsapi20170525.Client;
import com.aliyun.dysmsapi20170525.models.SendSmsRequest;
import com.aliyun.dysmsapi20170525.models.SendSmsResponse;
import static com.aliyun.teautil.Common.toJSONString;

public class Sample {
    public static Client createClient() throws Exception {
        Config config = new Config()
                // 配置 AccessKey ID，请确保代码运行环境设置了环境变量 ALIBABA_CLOUD_ACCESS_KEY_ID。
                .setAccessKeyId(System.getenv("ALIBABA_CLOUD_ACCESS_KEY_ID"))
                // 配置 AccessKey Secret，请确保代码运行环境设置了环境变量 ALIBABA_CLOUD_ACCESS_KEY_SECRET。
                .setAccessKeySecret(System.getenv("ALIBABA_CLOUD_ACCESS_KEY_SECRET"));
        
        // 配置 Endpoint
        config.endpoint = "dysmsapi.aliyuncs.com";

        return new Client(config);
    }

    public static void main(String[] args) throws Exception {
        // 初始化请求客户端
        Client client = Sample.createClient();

        // 构造请求对象，请填入请求参数值
        SendSmsRequest sendSmsRequest = new SendSmsRequest()
                .setPhoneNumbers("1390000****")
                .setSignName("阿里云")
                .setTemplateCode("SMS_15305****")
                .setTemplateParam("{\"name\":\"张三\",\"number\":\"1390000****\"}");

        // 获取响应对象
        SendSmsResponse sendSmsResponse = client.sendSms(sendSmsRequest);

        // 响应包含服务端响应的 body 和 headers
        System.out.println(toJSONString(sendSmsResponse));
    }
}
```

