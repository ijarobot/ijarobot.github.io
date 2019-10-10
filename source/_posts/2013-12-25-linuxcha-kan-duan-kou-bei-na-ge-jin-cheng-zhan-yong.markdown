---
layout: post
title: "Linux 命令个人收集(慢慢更新)"
date: 2013-12-25 11:18
comments: true
categories: Linux
---
[摘要 记录在使用AWS　EC2 使用ubuntu.记录自己平时使用，而不熟悉的命令]

-进程相关
----

查看详细系统进程信息
----------

ps -aux


查看端口被哪个进程占用
-----------

	lsof -i:2181

结果:

COMMAND   PID   USER   FD   TYPE  DEVICE SIZE/OFF NODE NAME

java      778 ubuntu  100u  IPv4 6162328      0t0  TCP localhost:52957->localhost:2181 (ESTABLISHED)

java     7655 ubuntu  100u  IPv4 5329958      0t0  TCP localhost:52651->localhost:2181 (ESTABLISHED)

java     8040 ubuntu  110u  IPv6 1482106      0t0  TCP localhost:50071->localhost:2181 (CLOSE_WAIT)

java    12997 ubuntu   19u  IPv6  360248      0t0  TCP *:2181 (LISTEN)


查看某个进程详情
--------

(如下结果结果可能得出2181端口被zookeeper所占用)
<!--more-->
	ps 12997

结果:

  PID TTY      STAT   TIME COMMAND
  
12997 ?        Sl    36:37 java -Dzookeeper.log.dir=. -Dzookeeper.root.logger=INFO,CONSOLE -cp /home/ubuntu/soft/zookeeper-3.4.5/bin/../build/classes:/home/ubuntu/soft/zookeeper-3.4.5/bin/../build/lib/*.jar:/home/ubuntu/soft

ubuntu@ip-172-31-8-33:~/soft/event-service/say-service-event-provider-0.0.1-SNAPSHOT/bin$ 




-时间\时区相关
----
查看时间
--------
	date

修改时区
--------
原理，替换/etc/localtime文件，不需要重启

	sudo cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
