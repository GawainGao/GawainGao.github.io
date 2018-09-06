---
layout: post
title: "SQL 数据库知识"
date: 2018-06-08 16:54:26 +0900
categories: Study
tag: Python
---

* content
{:toc}




首先我们进行新的 sql 数据库的创建
-----------------

'''
show database ->
create database ->
use "database" ->
show tables ->
create table "table"
'''

CHAR 是不可变长度的，VARCHAR 是可变长度的。DATE 是时间数据类型。
之后可以用 show tables 和 describe mytable 进行查看表格。

可以使用 insert into mytable 命令以及 values 命令向表格当中插入数据。
'''
select a from b;
星号可以代表选取所有列
可以使用 DISTINCT 用来排除重复值
select a from b where 列 运算符 值
可以使用 and 和 or 进行并列
'''

如果要对表格中的数据进行排序。
'''
使用 order by 命令
如果有两个列可以一起进行排序。
如果使用 DESC 可以进行逆序。
'''

如果要插入新的值 或者 删除
'''
insert into a values；
insert into a（line1，line2） values（）；
update a set line = value where line2 = b;
delete from a where line = value
'''

高级语法
* 使用 select from where like 来进行关键词的选取
* not like 就是相反的意思
* 通配符包含%，_，[]可以作为 charlist。
* select from where in（）
* select from where between and 也可以使用 and 来取反
* select as from 用来别名
* select x.a，x.b，y.c from x，y where x.id = y.id 可以将两个表格进行关联。同样还可以使用 select x.a，x.b，y.c from x inner join y on x.id = y.id order by x.a；
* 其中 join 分为 join，left join，right join，full join 四种。
* union 或者 union all 语法用来组合相似的表格
* insert into select from 语句用来 copy table

创建 database 或创建 table
*