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

**M版本**：M1,M2,M3中的M是milestone的简写，这个单词是里程碑的意思。

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



下面的表格列出了SpringBoot版本、JDK版本的兼容性，以及兼容性的来源，都在spring-boot的各个版本的文档中，有链接、描述java版本的原文。

| **SpringBoot Versions** | **JDK Versions** | Froms                                                        |
| ----------------------- | ---------------- | ------------------------------------------------------------ |
| 0.0 -1.1                | 6+(6 or higher)  | https://docs.spring.io/spring-boot/docs/0.0.x/reference/html/getting-started-installing-spring-boot.html<br/>Spring Boot can be used with “classic” Java development tools or installed as a command line tool. Regardless, you will need Java SDK v1.6 or higher.<br/>https://docs.spring.io/spring-boot/docs/1.0.x/reference/html/getting-started-installing-spring-boot.html<br/>Spring Boot can be used with “classic” Java development tools or installed as a command line tool. Regardless, you will need Java SDK v1.6 or higher.<br/>https://docs.spring.io/spring-boot/docs/1.1.x/reference/html/getting-started-installing-spring-boot.html<br/>Spring Boot can be used with “classic” Java development tools or installed as a command line tool. Regardless, you will need Java SDK v1.6 or higher.<br/> |
| 1.2 - 1.5               | 6 - 7            | https://docs.spring.io/spring-boot/docs/1.2.x/reference/html/getting-started-system-requirements.html<br/>By default, Spring Boot 1.2.8.RELEASE requires Java 7 and Spring Framework 4.1.5 or above. You can use Spring Boot with Java 6 with some additional configuration.<br/>https://docs.spring.io/spring-boot/docs/1.3.x/reference/html/getting-started-system-requirements.html<br/>By default, Spring Boot 1.3.8.RELEASE requires Java 7 and Spring Framework 4.2.8.RELEASE or above. You can use Spring Boot with Java 6 with some additional configuration.<br/>https://docs.spring.io/spring-boot/docs/1.4.x/reference/html/getting-started-system-requirements.html<br/>By default, Spring Boot 1.4.7.RELEASE requires Java 7 and Spring Framework 4.3.9.RELEASE or above. You can use Spring Boot with Java 6 with some additional configuration.<br/>https://docs.spring.io/spring-boot/docs/1.5.x/reference/html/getting-started-system-requirements.html<br/>By default, Spring Boot 1.5.22.RELEASE requires Java 7 and Spring Framework 4.3.25.RELEASE or above. You can use Spring Boot with Java 6 with some additional configuration.<br/> |
| 2.0                     | 8 - 9            | https://docs.spring.io/spring-boot/docs/2.0.x/reference/html/getting-started-system-requirements.html<br/>Spring Boot 2.0.9.RELEASE requires Java 8 or 9 and Spring Framework 5.0.13.RELEASE or above.<br/> |
| 2.1                     | 8 - 12           | https://docs.spring.io/spring-boot/docs/2.1.x/reference/html/getting-started-system-requirements.html<br/>Spring Boot 2.1.18.RELEASE requires Java 8 and is compatible up to Java 12 (included).<br/> |
| 2.2 - 2.3               | 8 - 15           | https://docs.spring.io/spring-boot/docs/2.2.x/reference/html/getting-started.html#getting-started-system-requirements<br/>Spring Boot 2.2.13.RELEASE requires Java 8 and is compatible up to Java 15 (included).<br/>https://docs.spring.io/spring-boot/docs/2.3.x/reference/html/getting-started.html#getting-started-system-requirements<br/>Spring Boot 2.3.12.RELEASE requires Java 8 and is compatible up to Java 15 (included).<br/> |
| 2.4                     | 8 - 16           | https://docs.spring.io/spring-boot/docs/2.4.x/reference/html/getting-started.html#getting-started-system-requirements<br/>Spring Boot 2.4.13 requires Java 8 and is compatible up to Java 16 (included).<br/> |
| 2.5                     | 8 - 18           | https://docs.spring.io/spring-boot/docs/2.5.x/reference/html/getting-started.html#getting-started.system-requirements<br/>Spring Boot 2.5.15 requires Java 8 and is compatible up to and including Java 18.<br/> |
| 2.6                     | 8 - 19           | https://docs.spring.io/spring-boot/docs/2.6.x/reference/html/getting-started.html#getting-started.system-requirements<br/> |
| 2.7                     | 8 - 21           | https://docs.spring.io/spring-boot/docs/2.7.x/reference/html/getting-started.html#getting-started.system-requirements<br/>Spring Boot 2.7.18 requires Java 8 and is compatible up to and including Java 21.<br/> |
| 3.0 - 3.2               | 17 - 21          | https://docs.spring.io/spring-boot/docs/3.0.x/reference/html/getting-started.html#getting-started<br/>Spring Boot 3.0.13 requires Java 17 and is compatible up to and including Java 21.<br/>https://docs.spring.io/spring-boot/docs/3.1.x/reference/html/getting-started.html#getting-started<br/>Spring Boot 3.1.6 requires Java 17 and is compatible up to and including Java 21.<br/>https://docs.spring.io/spring-boot/docs/3.2.x/reference/html/getting-started.html#getting-started<br/>Spring Boot 3.2.0 requires Java 17 and is compatible up to and including Java 21.<br/> |
|                         |                  |                                                              |



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