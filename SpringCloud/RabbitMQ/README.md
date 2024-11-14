# RabbitMQ

RabbitMQ是基于Erlang语言开发的开源消息通信中间件，官网地址：[https://www.rabbitmq.com/](https://www.rabbitmq.com/)，

它基于AMQP（Advanced Message Queue 高级消息队列协议）协议实现的消息队列，是一种应用程序之间的通信方法。

RabbitMQ 基本架构图：

![画板](images/1728908448229-4bc77193-da6d-4476-a176-80c644eafb0a.jpeg)

+ **Publisher**：生产者->发送消息的一方
+ **Consumer**：消费者->消费消息的一方
+ **queue**：队列->储存消息。生产者投递的消息会暂存在消息队列中，等待消费者处理
+ **exchange**：交换机->扶着消息路由。生产者发送的消息有交换机决定投递到哪个队列
+ **VirtualHost**：虚拟主机->起到数据隔离的作用。每个虚拟主机相互独立，有各自的 exchange、queue

# RabbitMQ的五种基本模式

## 简单模式（Hello World!）

![](images/1728909596780-02e5cb0a-7ff8-4d47-9e05-7b1ed201d9e7.png)

一个生产者一个消费者

## 工作队列模式（Work Queues）

![](images/1728909588592-7a932e53-9dc3-452d-8026-63051e5e3804.png)

## 发布订阅模式（Publish/Subscribe）

![](images/1728909607919-0430e86f-8599-47df-b723-cc2c7da927d7.png)

## 路由模式（Routing）

![](images/1728909623489-abdb17d3-2aaa-4373-9b97-5c070f99019c.png)

## 主题模式（Topics）

![](images/1728909632027-19a7a3da-1880-440b-ad51-e91ce1fdbef4.png)

