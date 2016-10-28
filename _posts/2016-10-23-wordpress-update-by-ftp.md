---
layout:     notebook
title:      update wordpress on vps 
author:     yangzhl
tags: 		vps wordpress 
subtitle:    show you how to update wordpress on vps
---

wordpress 更新版本，插件以及主题
- - -


* 更新版本


1. 备份你的WordPress数据及文件
2. 下载wordpress的最新安装包到你的本地，并解压
3. (deactivate)停用所有的插件对你的WordPress网站。
4. 登陆你的主机或者空间，删除掉wp-includes和wp-admin目录下的文件
5. 之前下了的最新版本wordpress解压后，除了wp-content目录外的所有文件都上传并覆盖到你博客主机相对应的位置。遇到是否覆盖时，选择全部覆盖就是了。
6. 覆盖完后，运行 http://你的博客地址/wp-admin/upgrade.php，执行升级。好了，按照以上方法


- - -
* 更新插件


1. 下载插件的压缩包到本地，解压
2. 利用ftp登录你的网站，文件上传到WordPress的wp-content中的plugins
3. update httpd,然后刷新的的网站

- - -

* 更新主题


    与上面更新插件类似

- - -
参考文献：
[Upgrading WordPress - Extended Instructions](http://https://codex.wordpress.org/Upgrading_WordPress_-_Extended_Instructions)