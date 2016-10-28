---
layout:     post
title:      jekyll 搭建github个人网站
author:     yangzhl
tags: 		jekyll bug github
subtitle:  	record something when I use jekyll to set up my blog

---
<!-- Start Writing Below in Markdown -->


# 目录

* TOC
{:toc}


# jekyll、github 搭建个人博客方法
（以Windows为例）

因为Windows平台下配置环境最为的复杂，Linux和OSX环境下搭建比较简单。

## 安装Ruby 配置环境变量

## 安装RubyGems环境

## 安装jekyll 

## Github结合使用

### 使用方法

### 使用过程中出现的问题

#### 本地测试出现的问题
本地测试中可能遇到路径找不到的问题。这主要看是否更改了_config.yml配置文件夹中的baseurl。

如果你的文件放在github上是作为根目录，例如网站源文件全部放在username.github.io下，则在本地jekyll server 启动后，只要baseurl默认还是"/"，那默认在本地浏览器中输入http://127.0.0.1:4000/就可以查看网页效果。

如果你的文件是作为project page放在你的某个仓库例如blog下，想作为gh-pages 项目，那么本地需要将_config.yml中的baseurl修改为baseurl="/blog/",启动jekyll server后可能出错"/"not found. 因为默认将此文件夹作为根目录。现在作为子目录后，自然就出错了。解决办法：在本地浏览器中打http://127.0.0.1:4000/blog/ 就可以在本地查看效果。

#### project page路径问题

# jekyll目录结构

