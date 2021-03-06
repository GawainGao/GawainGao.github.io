---
layout: post
title: "Wordpress建站"
date: 2018-09-07 02:26:26 +0900
categories: Study
tag: Network
---

* content
{:toc}


使用 Wordpress 建站
----------
在gitHub 的网站中写关于 wordpress 建站有一种奇怪的感觉。为了获得一个有独立域名的网站以及进一步学习 docker，我来学习一手服务器加域名加 wordpress 的建站方式。




AWS 和阿里云的域名
-----------
我选择了 AWS 亚马逊的服务器，使用信用卡的话第一年可以免费。似乎需要一个海外开通的信用卡，我刚好在日本工作就很顺利的成功了。系统装的是 Ubuntu16。

阿里云的域名如果买在海外的话，也是需要海外信用卡。比起腾讯的域名，在海外购买阿里云域名审查手续比较简单，所以我选择了这个。因为还是做学习用就买了个便宜的 `www.littlelwx.club` .

购买成功后需要开放服务器的80，22和3389端口用来进行 http 和 ip 通讯。很重要的一点是要去对域名进行域名解析。AWS 服务器有一个弹性 ip 相当于是服务器的 ip 地址，每次更换网络环境本地的 ip 可能会发生变化，所以必要的是将这个弹性 ip 和域名绑定起来。这样每次通过域名的后台进行管理的时候就可以访问到我们弹性 ip，如果我们登录了我们的服务器就可以对网站进行一些管理。（当然后续的一些管理并不需要登录服务器也可以完成）。

AWS 服务器主要支持 SSH 登陆，为了安全我没有开放用户名和密码登录的选项。还有很重要的是配置用户的安全组，这个都可以 google 实现。

拥有了 AWS 和阿里云，我们就可以将 wordpress 安装在 Ubuntu 里面。使用`apt-get` 命令和 `wdgt` 命令就可以简单的实现。 之后我们只要使用 `localhost/wp-admin` 就可以登录我们的 wordpress 管理后台啦。


Wordpress 的使用
-----------
wordpress 使用起来非常简单。
* `post` 主要用来管理发布的文章。这些文章可以有分类的 category
* `pages` 主要用来管理界面，和 post 的使用方法比较类似。
* `Appearance` 中的 themes 可以用来更换主题，widgets 可以用来安装一些边栏小插件。Menus 是导航很重要。


使用 scp 传文件
----------
这里有一个小技巧，可以使用
`scp -i key.pem usr-name@ip:/address /Users/..` 来进行文件的传输


插件安装不了的问题
-----------
因为 ftp 的访问权限原因以及文件夹的创建权限原因，当遇到不能安装插件的时候可以使用以下两个操作同时进行。
首先在 wp-conten 目录下创建于一个空的文件夹
`mkdir tmp`
`sudo chmod -R 777 tmp`
然后将权限修改为777.
第二步的操作，将 wp-config.php 文件用 scp 命令配上 ssh 传送到本地，在其中加入
```
define('WP_TEMP_DIR', ABSPATH.'wp-content/tmp');/* WordPress的临时目录。*/

define("FS_METHOD", "direct");  

define("FS_CHMOD_DIR", 0777);  

define("FS_CHMOD_FILE", 0777);  

```
四行代码进行定义，表明将下载下来的文件放入临时文件夹 tmp，然后对这个文件夹进行读取。
这样就可以正常安装插件了。


上传大小限制的问题
-----------
在我们上传一些 theme 活着文件的时候，遇到了2MB 以上的文件无法上传的问题，这是由于 ftp 的设置所导致的。我们可以使用 php.ini文件的修改来解决。

首先我们来到服务器的根目录，使用以下的方式
```
cd /etc/php/7.0/apache2
nano php.ini
upload_max_filesize = 16M
Ctrl+X
sudo service apache2 restart
```

就可以解决这个问题


推荐两个比较好用的模板
--------
用来做个人主页的StanleyWP和用来做电子商务的Woocommerce



