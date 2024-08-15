8.使用MySQL中的索引需要注意什么？
9.数据库的左连接和右连接有什么区别？
10.ArrayList与LinkedList有什么区别？
1.自我介绍，介绍项目做了什么
2.JAVA集合框架有哪些
3.ArrayList和LinkedLIst区别
4.ArrayList扩容
4.HashSet方法怎么实现的
5.HashSet怎么检查重复
6.HashMap底层数据结构
7.Spring和SpringBoot有什么区别
8.Bean的生命周期
9.IOC和AOP概念
10.Interceptor和Filter区别
10.MyBatis接口实现原理
11.JVM运行时数据区域
12.对象创建过程
13.对象内存布局
14.线程怎么创建
15.线程池重要参数
16.MySQL索引有哪些
17.回表是什么意思
18.MyISAM和InnoDB区别
19.创建表应该怎么设计字段
20.联合索引的最左匹配原则
21.MVCC实现原理
22.SpringBoot怎么解决循环依赖的

switch 中可以使用 String 吗？

Switch中使用String需要注意一下几点:

**在 Java 7之前，实现基于字符串的条件流的唯一方法是使用 if-else 条件。 但是 Java 7也改进了 switch case 来支持 String。**

1.switch能够取代 if-else-if条件链使得代码更加简洁易读
2.switch比较的时候区分大小写,输出的例子也说明了这一点
3.Java中switch是通过String.equals 方法来比较传递值和case值，所以请确保添加 NULL 检查以避免 NullPointerException
4.java 编译器为 Switch 语句中的字符串生成比链式 if-else-if 条件语句更有效的字节码
5.Java switch case String只能在Java7或更高的版本中使用，否则它会抛出异常

String str = new String("abc");创建了几个对象，为什么？



