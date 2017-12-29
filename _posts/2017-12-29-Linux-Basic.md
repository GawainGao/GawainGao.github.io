---
layout: post
title: "Linux 学习笔记 | Linux Basic"
date: 2017-12-29 16:04:20 +0900
categories: Linux
tag: Linux
---

* content
{:toc}



Linux 学习笔记
--------
记录一些常用的 Linux 下的操作。

date | 日期
-------
* date
* date +%Y/%m/%d
* date +%H/%M

cal | 日历
------
* cal
* cal 2015
* cal [month][year]

bc | 计算器
------
* scale=3
* quit

[tab][tab] | 补全
-----
* 命令补全
* 档案补全

[Ctrl]
------
* [Ctrl]-c | 终止
* [Ctrl]-d | 退出

[shift]
------
* [shift]-{[Page UP][Page Down]}

--help
-------
* date --help
* man date
* `space` to next page && `q` to quit
* `/word`
* `?string` then `n` & `N`
* `man -f man`
* `man -k man`

mandb
-----
* `whatis []`
* `apropos []`

info
-----
* `info info`
* 光标在`*`上时按下`enter`
* `b`egin
* `e`nd
* `n`ext
* `p`revious
* `u`pper
* s(/)
* `q`uit

nano
------
* `nano + 文件名`

Status
------
* who 用户
* netstat -a 网络连接状态
* ps -aux 背景执行程序
* sync 资料写入
* shutdown 关机
* reboot
* halt
* poweroff

Shutdown
------
* -h now
* -h 20:25
* -h +10
* -r now
* -r +30 'The system will reboot'
* systemctl reboot
* systemctl poweroff





