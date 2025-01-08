# Maven介绍



## Maven是什么？

Apache软件基金会下的一款用于构建java项目的开源软件
常见构建java项目的软件
		Ant
		Gradle

## 生命周期 Lifecycle

1. clean
   目的：清除之前构建产生的输出文件，如编
2. 译后的 .class 文件或打包后的 .jar 文件。
   命令：`mvn clean`
3. validate
   目的：验证项目是否正确设置并准备好构建。
   这个阶段通常用于执行一些检查，以确保项目的构建环境是正确的。
   命令：`mvn validate`
4. compile
   目的：编译项目的源代码。
   命令：`mvn compile`
5. test
   目的：运行项目的单元测试。
   这个阶段通常会跳过失败的测试，但不会阻止构建继续进行。
   命令：`mvn test`
6. package
   目的：将编译后的代码打包成可部署的格式，如 JAR 或 WAR 文件。
   命令：`mvn package`
7. verify
   目的：运行任何检查以验证包的有效性和完整性。
   这个阶段通常用于确认包的质量，例如通过运行集成测试。
   命令：`mvn verify`
8. install
   目的：将打包后的项目安装到本地仓库，供其他项目作为依赖使用。
   命令：`mvn install`
9. site
   目的：生成项目文档网站。
   这个阶段通常用于生成项目报告和其他文档。
   命令：`mvn site`
10. deploy
      目的：将打包后的项目部署到远程仓库，供其他开发人员或项目使用。
      命令：`mvn deploy`

# Maven 的下载安装

官网下载

http://maven.apache.org/download.cgi

最新版本

![image-20240808121507592](images/image-20240808121507592.png)

历史版本

![image-20240808121642691](images/image-20240808121642691.png)



![image-20240808121722443](images/image-20240808121722443.png)

# Maven仓库

新网址https://central.sonatype.com/

旧网址https://mvnrepository.com/

```xml
<build>
    <plugins>
        <!-- -->
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-jar-plugin</artifactId>
            <version>2.4</version>
            <configuration>
                <archive>
                    <manifest>
                        <addClasspath>true</addClasspath>
                        <!--设置了JAR文件的主类，也就是程序的入口点 -->
                        <mainClass>com.itheima.Test</mainClass>
                    </manifest>
                </archive>
            </configuration>
        </plugin>
    </plugins>
</build>
```



```xml
<!--        mybatis分页插件 主要提供三个功能
            1.自动计算分页
            2.自动执行计算总数的sql
            3.提供统一的分页类（PageInfo）-->
<dependency>
    <groupId>com.github.pagehelper</groupId>
    <artifactId>pagehelper-spring-boot-starter</artifactId>
    <version>2.1.0</version>
</dependency>
```



```xml
<!--    SprintBoot优雅参数校验-->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-validation</artifactId>
    <version>3.3.2</version>
</dependency>
```



```xml
<!--        apache commons集合工具包-> 针对jdk中的集合框架提出的-->
<dependency>
    <groupId>org.apache.commons</groupId>
    <artifactId>commons-collections4</artifactId>
    <version>4.4</version>
</dependency>
```

```xml
<!--字符串处理：提供丰富的字符串操作方法，如 StringUtils 类。
数值处理：提供数值类型的操作方法，如 NumberUtils 类。
日期时间处理：提供日期和时间的操作方法，如 DateUtils 类。
对象操作：提供对象比较、哈希码生成等方法，如 ObjectUtils 类。
异常处理：提供异常处理的辅助方法，如 ExceptionUtils 类。
集合操作：提供集合相关的操作方法，如 ArrayUtils 和 CollectionUtils 类。-->
<dependency>
    <groupId>org.apache.commons</groupId>
    <artifactId>commons-lang3</artifactId>
</dependency>
```

```xml
<!--Java 应用中进行 JSON 数据的序列化和反序列化操作

JSON 序列化：将 Java 对象转换为 JSON 字符串。
JSON 反序列化：将 JSON 字符串转换为 Java 对象。
支持多种数据类型：可以处理复杂的对象结构、集合、数组等。
高性能：相比其他 JSON 库，fastjson2 在性能上有显著优势。-->
<dependency>
    <groupId>com.alibaba.fastjson2</groupId>
    <artifactId>fastjson2</artifactId>
    <version>2.0.52</version>
</dependency>
```





如何使用Maven把项目导入到本地仓库中
	Maven生命周期
		clean
		compile
		test
		package
		install 使用java -jar启动jar包
		deploy
	使用步骤
		先跳过test
		再执行install

Maven继承
	子项目可以继承父项目中pom依赖,这样多个子项目如果同时都用到相同的依赖,可以将其直接放在父项目pom当中
		简化子项目依赖配置
	实现步骤
		第一步
			设置父项目打包方式为pom
		第二步
			在子项目pom加入`<parent></parent>`标签指定继承的父项目的Maven坐标
		第三步
			`<relativePath></relativePath>`指定父项目的pom文件位置