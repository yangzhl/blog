---
layout:     notebook
title:      vps change time zone
author:     yangzhl
tags: 		vps timezone
subtitle:   change timezone in your vps
---

1. 先登陆你的ssh，命令：date 看下时间是不是北京时间，如果不是我们把他改成北京时间。
2. 命令：
rm -rf /etc/localtime
ln -s /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
应该就OK了！用date瞅瞅系统时间已经变成北京了吧
上海和北京时区一样的，时区的配置文件在/usr/share/zoneinfo 里面

如果此时你的vps时间已经改成北京时间就不用看下面了，如果此时你的vps时间还没有修改好。再试下命令：
ntpdate stdtime.sinica.edu.tw（如果不行，就换这个ntpdate us.pool.ntp.org）
使用ntpdate stdtime.sinica.edu.tw 时候如果提示这个命令，先安装 ntpdate就可以了。
 
```
centos 系统的vps用命令：
yum -y install ntpdate ntp
Ubuntu系统的：
sudo apt-get install -y ntpdate ntp
```
安装完毕再试这个命令，如果还不可以的话，一般情况就是母鸡做了设置不让修改你vps的时间了，vpsma没有想到好的办法，可以写信或者发ticket给你的vps商，告诉他你的时区。看下他们可以帮忙把你vps修改成北京时间吗。
Linux linode vps将时间改成北京时间