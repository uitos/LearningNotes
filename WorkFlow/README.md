# 什么是工作流

​	使用编程语言完成一套固定的审批流程
​		例如请假审批流程
​		订单配送流程
​		入职，辞职审批流程
​	使用场景
​		业务类：合同审批流程、订单处理流程、出入库审批流程等。
​		行政类：请假流程、出差流程、用车流程、办公用品申请流程等。
​		财务类：报销流程、支付流程等。
​		客户服务类：售后跟踪、客户投诉等。

常见软件
		尤其在OA，ERP，CRM软件中使用较多
			OA
				办公自动化（Office Automation）
			ERP
				企业资源计划即 ERP (Enterprise Resource Planning)
			CRM
				客户关系管理（Customer Relationship Management）

# 工作流中的核心三要素

​	流程名称
​	流程绑定业务id
​	各流程负责人

# 官网

​	https://www.activiti.org/

# activiti

​	Activiti 是一个开源的工作流引擎，它实现了BPMN 2.0规范，可以发布设计好的流程定义，并通过api进行流程调度
​	BPM，Business Process Management 即业务流程管理） 的创建者 Tom Baeyens 离开 JBoss 之后建立的项目
​	BPMN 2.0其实也是一种类似于xml和html的一种标记语言，就是使用bpmn的规范来定义画流程图，最终形成一个bpmn文件



# Springboot集成Activiti

​	父工程pom下添加
​		 <dependency>
​            <groupId>org.activiti</groupId>
​            <artifactId>activiti-spring-boot-starter</artifactId>
​            <version>7.1.0.M6</version>
​        </dependency>
​		<dependency>
​            <groupId>org.springframework.boot</groupId>
​            <artifactId>spring-boot-starter-security</artifactId>
​        </dependency>
​	注意： activiti7与spring security 强耦合因此两个依赖 必须都得引入
​	yml中spring节点下增加配置

```
spring:
#  activiti与spring security 深度耦合，排除SpringSecurity的自动配置
  autoconfigure:
    exclude:
      - org.springframework.boot.autoconfigure.security.servlet.SecurityAutoConfiguration
  activiti:
    #是否让activiti自动创建所有的历史表
    history-level: full
    #是否需要使用历史表,默认false不使用,而配置true是使用历史表 第一次使用为false
    db-history-used: true
    #流程自动部署，关闭，需要手动部署流程 服务启动的时候自动检查resources目录下的bpmn文件 如果为true自动部署流程
    check-process-definitions: false
    #关闭启动服务自动框架部署
    deployment-mode: never-fail

```





# Activiti开发流程



1.画流程图模型
	遵守BPMN的流程规范，使用BPMN的流程定义工具，通过 流程符号 把整个业务流程定义出来，将流程定义文件字节流保存到模型数据表中（Model）。每一个流程图都是一个.bpmn文件
2.部署流程定义
	加载画好的流程定义文件，将它转换成流程定义数据（ProcessDefifinition），保存到流程定义数据表中
3.启动流程
	生成流程实例数据（ProcessInstance），生成第1个节点的任务数据(Task)
4.处理人审批流程节点任务
	完成任务审批，生成审批结果，生成下一节点任务数据。直至满足条件，流程走到结束节点。



# 流程图模型中的各种符号



事件event符号
	 开始事件（Start Event）：表示流程的起点，通常用于触发流程的启动。 
	 中间事件（Intermediate Event）：发生在流程中间的事件，可以根据需要划分为多种类型，如定时器事件、消息事件、信号事件等。
	  结束事件（End Event）：表示流程的结束点，通常用于触发流程的结束。 
	

活动activity符号
	任务（Task）是最基本的活动类型，表示一个简单的、可执行的工作单元
	常见符号

		1. 用户任务（User Task）：表示需要由具体用户来执行的任务。在流程中，当流程执行到用户任务节点时，会生成一个待办任务，需要指定具体的执行人来完成任务。
		2. 服务任务（Service Task）：通过调用外部服务或执行业务逻辑来完成任务的一种任务类型。可以调用Java类、Web服务、REST接口等来执行具体的任务操作。
		3. 接收任务（Receive Task）：表示等待外部触发的任务，当接收到外部的信号或消息时，流程会继续执行下一步。可以用于等待外部系统的通知或事件触发。
		4. 发送任务（Send Task）：表示发送消息或触发事件的任务类型。可以发送消息给外部系统或触发特定的事件，用于与外部系统进行交互。
		5. 业务规则任务（Business Rule Task）：表示执行业务规则来完成任务的一种任务类型。可以通过规则引擎执行事先定义好的业务规则，用于根据特定条件做出决策。
网关Gateway符号
	用于处理流程中的决策
	

1. 排他网关（Exclusive Gateway）：也称为XOR网关或基于数据的排他网关，用于在流程中创建决策点。当执行到达排他网关时，所有出口顺序流会按照它们定义的顺序进行计算。条件计算为true的顺序流会被选择用于继续流程。
	相当于if-else只走一个分支
2. 包容网关（Inclusive Gateway）：也称为AND网关或包容性决策网关，用于在流程中创建平行的路径。当执行到达包容网关时，所有出口顺序流同时进行计算，并且至少要有一个条件计算为true的顺序流被选择用于继续流程。
	只需要满足一个条件
3. 综合网关（Complex Gateway）：用于模拟复杂的同步行为。通过表达式激活条件描述精确的行为。
4. 基于事件的网关（Event-based Gateway）：基于事件的网关代表流程中的一个分支点，其中遵循网关的替代路径基于发生的事件，而不是使用流程数据对表达式的评估。
5. 并行网关（Parallel Gateway）：用于同步（组合）并行流并创建并行流。

# 具体流程

​	部署流程
​		把xml文件和图片写入到数据库当中
​		Java类
​			RepositoryService
​				创建部署
​					createDeployment
​				删除部署
​					deleteDeployment
​		涉及表
​			ACT_RE_PROCDEF 新增数据: 流程定义数据
​			ACT_RE_DEPLOYMENT 新增数据: 流程部署数据 
​			ACT_GE_BYTEARRAY 新增数据：将当前流程图绑定到此流程定义部署数据上 
​			ACT_RE_MODEL 更新部署id
​	启动流程
​		读取部署好到表中的流程数据开启流程，创建流程审批模板
​		Java类
​			RuntimeService
​				startProcessInstanceByKey(String processDefinitionKey, String businessKey)
​					参数：
​						部署好的流程名称
​						唯一业务主键
​		涉及到的表
​			●  act_hi_actinst     流程实例执行历史 
​			●  act_hi_identitylink  流程的参与用户历史信息 
​			●  act_hi_procinst      流程实例历史信息 
​			●  act_hi_taskinst       流程任务历史信息 
​			●  act_ru_execution   流程执行信息 
​			●  act_ru_identitylink  流程的参与用户信息 
​			●  act_ru_task         任务信息
​	操作流程
​		Java类
​			TaskService
​		负责人查询待办任务
​			TaskService
​				查询单条代办查询
​					singleResult
​				查询全部代办任务
​					list
​				分页查询代办任务
​					listPage
​				条件查询
​					根据流程名称查询
​						processDefinitionKey
​					根据负责人查询
​						taskAssignee
​					根据流程绑定业务id查询
​						processInstanceBusinessKey
​				模糊查询
​					方法中带like
​				精确查询
​					方法中带equals
​				范围查询
​					方法中带after，before，group，in，between等
​		完成
​			TaskSercive
​				complete(String taskId, Map<String,Object> variables, boolean localScope)
​					可结束当前节点流程，标记为已完成，并且流程会自动开启下一个节点的任务。同时在结束时还可以把填写的数据，作为流程变量传递到下一个流程中
​					参数
​						任务id
​						携带变量
​						是否为全局变量，是则为全流程可见
​		拒绝
​			RuntimeService
​				deleteProcessInstance(String processInstanceId, String deleteReason);
​			TaskSercive
​				deleteTask
​		查询历史
​			HistoryService
​				processInstanceBusinessKey(String processInstanceBusinessKey)
​				taskId(String taskId)
​				taskAssignee(String taskAssignee)  | taskAssigneeLike(String taskAssignee)
​				finished()
​				unfinished()
​				orderByHistoricTaskInstanceEndTime().desc()
​				taskName(String var1)  |  taskNameLike(String var1)
​				includeProcessVariables()
​				processVariableValueEquals(String variableName, Object variableValue)
​				processVariableValueNotEquals(String variableName, Object variableValue)
​				processVariableValueGreaterThan(String name, Object value)
​				processVariableValueLessThan(String name, Object value)
​				createHistoricTaskInstanceQuery
​					list()