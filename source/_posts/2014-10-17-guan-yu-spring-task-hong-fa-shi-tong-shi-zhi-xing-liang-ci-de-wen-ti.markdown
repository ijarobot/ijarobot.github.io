---
layout: post
title: "关于Spring Task 触发时同时执行两次的问题"
date: 2014-10-17 15:29
comments: true
categories: java,spring,task,troubleshooting
---
【摘要 软件环境dubbo+mybatis+spring, 在使用Spring task 每1分钟执行do something时，却发现do something执行了两次】

say-event-provider.xml

```xml
    <beans xmlns="http://www.springframework.org/schema/beans"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xmlns:context="http://www.springframework.org/schema/context"
	xmlns:dubbo="http://code.alibabatech.com/schema/dubbo"
	xmlns:jdbc="http://www.springframework.org/schema/jdbc" 
	xmlns:tx="http://www.springframework.org/schema/tx"
	xmlns:aop="http://www.springframework.org/schema/aop"
	xmlns:task="http://www.springframework.org/schema/task" 
	xsi:schemaLocation="
	http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans-3.2.xsd
	http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context-3.2.xsd
	http://www.springframework.org/schema/jdbc http://www.springframework.org/schema/jdbc/spring-jdbc-3.2.xsd
	http://www.springframework.org/schema/tx http://www.springframework.org/schema/tx/spring-tx-3.2.xsd
	http://www.springframework.org/schema/aop http://www.springframework.org/schema/aop/spring-aop-3.2.xsd
	http://www.springframework.org/schema/task http://www.springframework.org/schema/task/spring-task-3.2.xsd
	http://code.alibabatech.com/schema/dubbo http://code.alibabatech.com/schema/dubbo/dubbo.xsd">
	
	<dubbo:registry address="zookeeper://127.0.0.1:2181" />
	
	<bean id="eventService" class="com.say.event.provider.EventServiceImpl" />
	<dubbo:service interface="com.say.event.EventService" ref="eventService" />
	<bean id="eventMomentService" class="com.say.event.provider.EventMomentServiceImpl" />
	<dubbo:service interface="com.say.event.EventMomentService" ref="eventMomentService" />
	
	<dubbo:reference id="pushService" interface="com.say.user.PushService" />
	
	<context:component-scan base-package="com.say.event"/>
	<task:annotation-driven/>.....
```
xxx.java

```java
    @Component
    @Transactional
    public class EventServiceImpl implements EventService {
	final static Logger logger = Logger.getLogger(EventServiceImpl.class);
        ....
	@Scheduled(cron="0 0/1 * * * ?")   //每分钟触发一次 
	public void test(){
		System.err.println(this +" === "+ new Date() +" === "+ Thread.currentThread().getId() +" === "+ Thread.currentThread().getName() );
	}	
```
执行结果:

![在此输入图片描述][1]

上图中看到在同一时间点执行了两次。

同时，查以通过划红色下划红的结果：

com.say.event.provider.EventServiceImpl**@20fc40ae**

com.say.event.provider.EventServiceImpl**@19aa5882**

可以看出他们不是同一个实例，由于可以看出是*EventServiceImpl* 的两个不同实例的*test()*方法分别被执行了一次，加来共为两次。


为什么执行了两次, 或者说什么会产两个实例？，Spring Bean的scope 默认可是singleton的哦...

原因就出在**say-event-provider.xml**的
	

```xml

    <bean id="eventService" class="com.say.event.provider.EventServiceImpl" />
```
和 **xxx.java**的第一行代码 **@Component**注解。它们两个会使用Spring 在初始化的过程中分别产生一个EventServiceImpl的实例。所以导致以上的结果。


  [1]: http://static.oschina.net/uploads/space/2014/1017/151310_gmCu_556928.jpg

