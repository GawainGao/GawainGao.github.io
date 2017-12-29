---
layout: post
title: "Linux 学习笔记(2) | Linux Basic(2)"
date: 2017-12-29 16:04:20 +0900
categories: Linux
tag: Linux
---

* content
{:toc}



Linux 学习笔记（2）
-------
在 Linux 中有群组（Group），其他人（Others）和管理员（Root）的概念。

* `su -` 切换至管理员
* `ls -al` 显示所有用户


如何阅读权限
------
* 第一个字符为档案类型，`d` 为目录， `-` 为档案， `l` 为连接档， `b` 为可随机存取装置， `c` 为键盘鼠标等一次性读取装置。
* 后面三个为一组，第一组为档案拥有者具有的权限，第二组为 档案成员拥有的权限，第三组为其他人的权限
* `ls -l -full-time` 可以用来显示档案的完整时间


如何修改权限
------
* `chgrp [-R] dirname/filename` 
* `chown [-R] user filename`
* `chown .sshd filename`
* `chmod [-R] xyz`


绝对路径与相对路径
------
* `./` 当前目录
* `../` 上一级目录
