---
layout:     notebook
title:      xshell 连接
author:     yangzhl
tags: 		xshell
subtitle:   xshell 连接
---
//安装sshd服务
$ sudo apt-get install openssh-server
//开启服务
$ /etc/init.d/ssh start
//关闭服务
$ /etc/init.d/ssh stop
//重启服务
$ /etc/init.d/ssh restart
CentOS上检设置：
1. 关闭防火墙
   service iptables stop
   chkconfig iptables off
2. 启动ssh服务
   service sshd start