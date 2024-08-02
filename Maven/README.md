# Maven是什么？

Apache软件基金会下的一款用于构建java项目的开源软件
常见构建java项目的软件
		Ant
		Gradle





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

