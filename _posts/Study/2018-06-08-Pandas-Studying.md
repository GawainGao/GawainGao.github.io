---
layout: post
title: "Pandas in Python"
date: 2018-06-08 15:59:26 +0900
categories: Study
tag: Python
---

* content
{:toc}



Pandas 库的使用
----------
之前我们在 Plotly 库使用的文章里简单介绍了如何使用 Pandas 库进行数据的索引。现在我们了解更多的该库的使用方法。




apply 和 applymap 函数的使用
-----------
我们可以先撰写一个函数，然后使用`.apply(function)`的方法对这个函数进行调用。比如

```
# Applying a function to a column
def base_year(year):
    base_year = year[:4]
    base_year= pd.to_datetime(base_year).year
    return base_year

df['year'] = df.water_year.apply(base_year)
df.head(5)
```

我们先定义一个函数，叫做`base_year`，在这个函数中我们将会返回一个包含月份与年份的数据中的年份部分。

之后对于这个函数我们针对一个列进行调用，就可以实现函数的功能。



groupby 函数的使用
---------
如果我们需要对数据进行分组的时候，我们可以用这个函数。
```
# Grouping by multiple columns
decade_rain = df.groupby([df.year // 10 * 10, df.rain_octsep // 1000 * 1000])[['outflow_octsep','outflow_decfeb', 'outflow_junaug']].mean()
decade_rain
```
首先这个函数可以实现将相同的数据进行分组。按照括号内的规则进行分组，这里我们进行了两重的分组。在调用完毕后我们可以在后面再调用一个函数，实现组内数据数据的提取。


unstack 函数
----------
我们可以在使用`groupby`函数以后，使用`unstack`函数对结果中的组进行展开。


pivot 函数
---------------
我们可以使用这个函数对数据进行轴向的旋转。
`.fillna('')` 函数可以用填充 Nan 的数据。

merge 函数
-----------
如果两个数据集有相同的标签，可以使用这个标签对两个数据集进行合并。


Plot
------
快速作图。


to_csv 函数
-------
保存到 csv 供下次使用。