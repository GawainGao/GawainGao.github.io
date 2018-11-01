---
layout: post
title: "Plotly in Python"
date: 2018-06-05 18:28:26 +0900
categories: Study
tag: Python
---

* content
{:toc}




Python 下使用 Plotly 进行数据可视化
------------
Plotly 库对于许多语言有支持，例如 R 语言，Python 和 Matlab 等。我今天使用 Python 中的 Plotly 的 API 进行使用，从而完成一个小的 Project。

Project的目标是，我们拥有一个图片集A，同时我们有另外的方法进行成像后得到的数据集 B，我们要对 A 和 B 的相关性进行比较。思想是从 A 中选取出全部的特征数据，形成一个和 B 相同的数据集，然后对两个数据集进行可视化的操作。


相关库的准备
-----------
我使用的是 Mac 操作系统，首先安装 Anaconda2，它自带 numpy 和 pandas 库让我们可以方便的进行开发。但是它不带 Plotly 的库。
我们使用 conda 命令进行安装，

```
conda install -c plotly plotly 
```

安装完毕后可以使用 `import plotly.plotly as pl`命令进行试验，如果成功我们就可以开始使用了。
因为是做数据的处理，我们可以使用 Anaconda2中的notebook，这样我们每一步对矩阵的操作can马上呈现出来。


Pandas 库对于数据的整理
-----------
在数据导入以及整理的过程中使用的是 Pandas 库。一些基本的 Pandas 库所要使用的语句是。
`data = pd.DataFrame(np.random.randn(a,b),index=,columns=)`
所有的 np 都是 `import numpys as np` 后的，所有的 pd 都是`import pandas as pd` 后的。

用这样的方式我们可以创建一个新的数据表，其中表的行列标题我们可以使用数组的形式导入。

因为是数据库的思想，所以不同列的数据类型可能不一样，不同行一般是同样的数据类型。
可以使用 `data.dtypes` 进行查找。

还有很多命令可以使用，例如 `head` `tail` `index` `columns` 用来索引需要的数据。

使用 `iloc` 和 `loc` 进行索引和切片是经常要用到的定位方法。

使用 `isin` 方法来进行查找也是很重要的方式。

Plotly 库进行数据可视化
------------
我们参考页面 `https://plot.ly/python/multiple-axes/` 
这是官方的对于 Plotly 如何再 Python 环境下进行使用的说明文档。而我展示的这个是为了创造一个双 Y 轴的图像。

```
# Create a trace
trace1 = go.Scatter(
    x = range(1,553),
    y = data_pic[6],
    name='yaxis data'
)

trace2 = go.Scatter(
    x = range(1,553),
    y = data_cmos[6],
    name='yaxis2 data',
    yaxis='y2'
)


data = [trace1,trace2]
layout = go.Layout(
    title='Double Y Axis Example',
    yaxis=dict(
        title='yaxis title'
    ),
    yaxis2=dict(
        title='yaxis2 title',
        titlefont=dict(
            color='rgb(148, 103, 189)'
        ),
        tickfont=dict(
            color='rgb(148, 103, 189)'
        ),
        overlaying='y',
        side='right'
    )
)
fig = go.Figure(data=data, layout=layout)
plot_url = pl.plot(fig, filename='multiple-axes-double')
```

在这段代码当中。首先创造了两个 trace 然后在这两个描绘中去画我们的散点图。注意需要创造一个 layout 来进行两个轴的绘制。
用这样的方法我们可以有效的对我们的数据进行可视化的处理。
















