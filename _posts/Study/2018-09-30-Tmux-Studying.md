---
layout: post
title: "Tmux 的配置"
date: 2018-09-30 16:56:26 +0900
categories: Study
tag: Tum
---

* content
{:toc}




Tmux 的好处
-----------------
* 可以分割窗口实现多进程
* 更为方便的SSH
* 可以快速新建自定义窗格
* 可以配合插件保存上一次的工作成果

Tmux 的配置
------------------
`sudo apt-get install tmux` 可以进行 tmux 的安装。可以快速新建自定义窗格
tmux 的配置文件是`~/.tmux.conf`。

如果不存在的话应该新建，第一件事就是改变热键的位置，从不方便你的 C+b 改成 C+a，需要加入`set -g prefix C-a`的同时`unbind C-b`。

之后改成前缀加 r 来更新配置文件，使用语句`bind r source-file ~/.tmux.conf \; display "    Reloaded!"。或者其他你喜欢的输出的语句也好。`

之后很重要的就是改变切换窗口位置和 vim 一样， 用一样的语句，`bind-key k select-pane -U    `等一些列语句。

Tmux 的快捷键
-------
`tmux new -s session` 新建一个会话。
`tmux attach -t session` 进入会话

tmux 分为三个等级的窗口分别是 session，window 和 pane。这个三个等级从高到低，分别对应了一个新建的项目，项目里面的众多窗口以及每个窗口界面分割出的并行操作界面。
可以使用 prefix+" 或者 prefix+%来进行窗口的分割，以及通过 vim 的形式在设置快捷键以后进行窗口之间的移动。
可以使用 prefix+数字来进行 window 之间的切换，以及使用 prefix+a 加 c 来进行新的 window的创建。
可以使用 prefix+new 来创建新的 session。


Tmux 的插件系统
---------
```
mkdir ~/.tmux
cd ~/.tmux
git clone http://github.相应的 plugin
```
之后添加`run-shell ~/.tmux/tmux-resurrect/resurrect.tmux`来使得差价可以运行。
这个插件是用来做 sl 大法，回复已经存储的工作状态，分别使用 C+s 和 C+r 来触发保存和读取。而另外一个插件 continuum 可以自动的按照设定的时间进行保存。









