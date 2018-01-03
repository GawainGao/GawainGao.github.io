---
layout: post
title: "Java 学习笔记 | Java Basic"
date: 2018-01-02 18:18:52 +0900
categories: Study
tag: Java
---

* content
{:toc}




Java 修饰符
======

Java 修饰符分为访问修饰符和非访问修饰符。




Java 中可以使用访问控制符来保护访问
------

* default 在同一包内可见，子孙类不可见
* private 在同一类内可见，不能修饰类
* public 在所有类可见，子孙类不可见
* protected 同一包内类和子类可见，不可修饰类

private 用于隐藏类的实现细节以及保护类的数据

		设定一个 private， 再设置一个 getFormat 和 setFormat 保护数据

public 程序中的 main()方法必须设置为公有

protected 接口和类都不能被修饰成，一般用来子类重写。父类使用该访问修饰符，子类重写。我们只想让一个方法对其所在类的子类可见。

一些规则。父类声明为 public 子类必须为 public。 父类 private 不能被继承。父类 protected 的方法在子类中为 protected 或 public。


Java 的非访问修饰符
-----
* static 修饰类方法和类变量
* final 修饰类，方法和变量，不能被继承，不能被修改，不能被重新定义。
* abstract 创建抽象类和方法，抽象方法是一种没有任何实现的方法，由子类提供。







java 方法
========
方法包含于类或对象中。使程序变得简短而清晰。在命名的时候应该第一个单词以小写开头，后面大写开头。包含修饰符，返回值类型，方法名，参数类型和方法体。

如果方法返回值是 void， 可以用语句调用，如果返回值是一个值，一般通常作为一个值使用。


通过值传参数
-------


方法的重载
------
两个方法，参数类型不同或参数个数不同。



构造方法
------
对象被创建的时候，可以用构造方法来初始化对象。用来给一个类的实例变量赋初值。


可变参数
----
使用`...`在参数类型之后，来进行可变参数的定义。


finalize()方法
-------
`protected void finalize()`使用 protect 来限定不会被该类之外的方法调用。



Java Stream, File && IO
====
java.io 包几乎包含了所有和输入输出有关的类。 控制台输入由`System.in`完成,可以实现从键盘输入数据，可以包装在一个`BufferedReader`中。

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

之后我们就可以用 read（）方法和 readLine（）方法来读取。

		int read() throws IOException






