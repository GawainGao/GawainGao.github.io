---
layout: post
title: "Linux 学习笔记（3） | Linux Basic（3）"
date: 2017-12-30 01:18:52 +0900
categories: Study
tag: Linux
---

* content
{:toc}



目录操作
------
* cd
* pwd -P
* pwd
* mkdir
* mkdir -p
* mkdir -m 711
* rmdir -p
* rmdir
* echo $PATH
* PATH="${PATH}:/root"
* PATH中的执行有先后的顺序
* ls -al ~
* ls -alF --color=never ~
* ls -al --full-time ~
* cp [目录1] [目录2]
* cp -i [目录1] [目录2]
* cp -a
* cp -l
* rm
* mv
* basename
* dirname


文档操作
-----
* head
* tail
* nl
* cat
* umask 用来设定权限。不同的用户有不同的预设的umask，可以在 bashrc 里面进行修改
* chattr 设定属性
* lsattr 查阅隐藏属性
* file
* which
* whereis 可以进行小范围搜寻