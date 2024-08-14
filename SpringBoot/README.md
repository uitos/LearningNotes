# Tomcat

下载

[Apache Tomcat](https://tomcat.apache.org/)

# Servlet







# SpringBoot

[SpringBoot 官网](https://spring.io/projects/spring-boot)

## 查看SpringBoot依赖的JDK版本

1.打开Sprint官方网站

进入Sprint官方网站[spring.io](https://spring.io/)，点击菜单Projects->Sprint Boot->LEARN

![image-20240814210233177](images/image-20240814210233177.png)



**版本标识的意义**

**CURRENT**：代表了当前版本，最新发布版本，里程碑版本。

**GA**：通用正式发布版本，同release。

**SNAPSHOT**：快照版本，可用但非稳定版本。

**PRE**：预览版本。

**M版本：**M1,M2,M3中的M是milestone的简写，这个单词是里程碑的意思。

**Alpha**：也被称为内部测试版或预览版，这些版本通常不会对外部用户公开，因为它们可能包含许多尚未修复的漏洞和不完整的功能。通常只有开发团队和其他内部相关人士才能访问和使用 Alpha 版本。

**Beta**：是一种公开测试版，位于 Alpha 版本之后。这个阶段的版本通常会加入新功能，并且相较于 Alpha 版本来说会更加稳定。Beta 版本主要面向特定的用户群体进行测试，如合作伙伴、潜在客户或早期采用者。

2.查看Reference Doc（参考文档）

比如查看3.2.8，点击Reference Doc.

![image-20240814210451890](images/image-20240814210451890.png)

3.点击左侧的 Getting Started

![image-20240814210801730](images/image-20240814210801730.png)

3.接着点击左侧的System Requirements

![image-20240814211012223](images/image-20240814211012223.png)



Spring Boot 3.2.8 requires [Java 17](https://www.java.com/) and is compatible up to and including Java 22. [Spring Framework 6.1.11](https://docs.spring.io/spring-framework/reference/6.1/) or above is also required.

> Spring Boot 3.2.8 要求使用 Java 17，并且兼容直至包括 Java 22。还需要 Spring Framework 6.1.11 或更高版本



## 创建SprintBoot工程

在线创建

打开[ https://start.spring.io/](https://start.spring.io/)



## IDEA新建项目

IDEA->New Project



![image-20240814204604788](images/image-20240814204604788.png)

![image-20240814200236773](images/image-20240814200236773.png)

![image-20240812180925546](images/image-20240812180925546.png)



![image-20240812180943703](images/image-20240812180943703.png)

![image-20240812180958887](images/image-20240812180958887.png)

![image-20240812181033775](images/image-20240812181033775.png)

## 初始化项目

配置Maven



![image-20240814201409545](images/image-20240814201409545.png)

配置properties文件编码为UTF-8

![image-20240814200720453](images/image-20240814200720453.png)