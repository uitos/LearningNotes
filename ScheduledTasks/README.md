```
//执行定时任务的技术
//1.jdk自带的定时任务线程
//2. Spring 自带的 @Scheduled 注解
//3. 使用强大的定时任务框架 Quartz
//4.使用国内定时任务软件 ->支持页面编辑定时任务 ->对定时任务进行增删改查，启动停止，不需要操作代码

```

# JDK自带的定时任务线程

```java
//JDK自带的定时任务
//无法设定复杂的定时任务时间点，只能以固定频率执行，每秒，每分，每小时等
//无法修改定时任务周期（需要停止程序修改代码）
//
//现在时间+10s
LocalDateTime now = LocalDateTime.now();
LocalDateTime future = now.plusSeconds(10);
ScheduledExecutorService executorService = Executors.newScheduledThreadPool(1);
executorService.scheduleAtFixedRate(()->{
    if (LocalDateTime.now().compareTo(future)>=0){
        System.out.println("预约过期");
    }else {
        System.out.println("等待你的光临");
    }
},0,3, TimeUnit.SECONDS);
/*
等待你的光临
等待你的光临
等待你的光临
等待你的光临
预约过期
预约过期
预约过期
...
*/
```

# Spring 自带的 @Scheduled 注解

@Scheduled需要配合`@EnableScheduling`使用。

使用时，将@Scheduled注解放在待定时的方法名上方，将 `@EnableScheduling`放在项目主启动类类名上方。

```java
@Target({ElementType.METHOD, ElementType.ANNOTATION_TYPE})
@Retention(RetentionPolicy.RUNTIME)
@Documented
@Repeatable(Schedules.class)
public @interface Scheduled {
    String CRON_DISABLED = "-";
    String cron() default "";
    String zone() default "";
    long fixedDelay() default -1L;
    String fixedDelayString() default "";
    long fixedRate() default -1L;
    String fixedRateString() default "";
    long initialDelay() default -1L;
    String initialDelayString() default "";
    TimeUnit timeUnit() default TimeUnit.MILLISECONDS;
}
```



|        参数        |                             说明                             |    示例    |
| :----------------: | :----------------------------------------------------------: | :--------: |
|        cron        |                     任务执行的cron表达式                     |   见下文   |
|        zone        | cron表达时解析使用的时区，默认为服务器的本地时区。 使用java.util.TimeZone#getTimeZone(String)方法解析 |  GMT-8:00  |
|     fixedRate      | 固定速率 上一次任务执行开始到下一次执行开始的间隔时间固定，单位为ms。 若在调度任务执行时,上一次任务还未执行完毕,会加入worker队列,等待上一次执行完成后，马上执行下一次任务 |    1000    |
|  fixedRateString   | 与fixedRate一致，只是间隔时间使用java.time.Duration#parse解析 | 1000或PT1S |
|     fixedDelay     | 固定延迟 上一次任务执行结束到下一次执行开始的间隔时间固定，单位为ms。 |    1000    |
|  fixedDelayString  | 与fixedDelay一致，只是间隔时间使用java.time.Duration#parse解析 | 1000或PT1S |
|    initialDelay    | 首次延迟多长时间后执行，单位ms。 之后按照fixedRate、fixedRateString、fixedDelay、fixedDelayString指定的规则执行，需要指定其中一个规则。 注意：不能和cron一起使用 |    1000    |
| initialDelayString | 与initialDelay 一致，只是间隔时间使用java.time.Duration#parse解析 | 1000或PT1S |

## cron表达式

[Cron - 在线Cron表达式生成器 (ciding.cc)](https://cron.ciding.cc/)

可以生成Cron表达式，同时，也可以反解析。还有一些程序员常用的工具。

```java
//cron表达式格式：
@Scheduled(cron = "{秒数} {分钟} {小时} {日期} {月份} {星期}")
```

各参数介绍：

| 单位 |                            允许值                            |  允许通配符   |
| :--: | :----------------------------------------------------------: | :-----------: |
| 毫秒 |                             0-59                             |    , - * /    |
| 分钟 |                             0-59                             |    , - * /    |
| 小时 |                             0-23                             |    , - * /    |
| 日期 |                             1-31                             | , - * / ? L W |
| 月份 |                  1-12或JAN-DEC(大小写均可)                   |   , - * / ?   |
| 星期 | 1-7或SUN-SAT(大小写均可)注：星期日为每周第一天，所以1-7表示周末到周六 | , - * / ? L # |

## cron通配符

| 符号 |                             含义                             |
| :--: | :----------------------------------------------------------: |
|  *   |     所有值,在秒字段上表示每秒执行,在月字段上表示每月执行     |
|  ？  | 不指定值，不需要关心当前指定的字段的值，比如每天都执行但不需要关心周几就可以把周的字段设为? |
|  -   |      区间或者范围,如秒的0-2 ,表示0秒、1秒、2秒都会触发       |
|  ,   | 指定值，比如在0秒、20秒、25秒触发,可以把秒的字段设为0,20,25  |
|  /   |  递增触发,比如秒的字段上设0/3 ,表示从第0秒开始,每隔3秒触发   |
|  L   | 最后，只允许在日字段或周字段上,在日字段上使用L表示当月最后一天,在周字段上使用3L表示该月最后一个周二 |
|  W   | 只允许用在日字段上,表示距离最近的该日的工作日,工作日指的是周一至周五 |
|  #   | 只允许在周字段上，表示每月的第几个周几，如2#3 , 每月的第3个周二 |