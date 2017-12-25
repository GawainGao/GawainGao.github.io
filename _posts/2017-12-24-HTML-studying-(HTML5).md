---
layout: post
title: "HTML studying(HTML5)"
date: 2017-12-24 00:38:26 +0900
categories: Front
tag: HTML5
---

* content
{:toc}











HTML5 New mothod
----

```
Today's menu:

* Eggs rice
* Fried dumplings
* Chocolate cake for birthday
* Fried shrimps


Which one do you want to eat? Come and find your favourite.

Yanagifuro street 303 tiger's restaurant at 7:00.
```
From HTML to HTML5, the language is getting much more breif, many semantics becoming shorter and easy to be use.

Some special rules you can choose to follow or not, but keep in good rules will be better. For example, the space is leagle. But space-less is easier to read and groups entities better together.

HTML5 Canvas
----
First set the height and the width of the canvas.

```
<canvas id="myCanvas" width="200" height="100"> </canvas>
```

Then use the JavaScript to draw something inside the canvas.

```
<script type="text/javascript">
var c=document.getElementById("myCanvas");
var cxt=c.getContext("2d");
cxt.fillStyle="#FF0000";
cxt.fillRect(0,0,150,75);
</script>
```

We can also use `moveTo` to choose the start point, then use `lineTo` to draw a line. 

If you want to change the color of the filled. You can use the `cxt.createLinearGradient(0,0,175,50)` and then use the `grd.addColorStop` to increase the different colors.


HTML5 inline SVG
------
SVG is scalable vector graphics. Compare with JPEG and GIF is can be changed, searched, flexible and printed.

HTML5 local storage
------
localStorage can store the item without the limit of the time.

```
localStorage.setItem("lastname","Gates");
document.getElementById("result").innerHTML = localStorage.getItem("lastname")

localStorage.removeItem("lastname")
```

HTML5 Manifest
-----
If you want to use the cache, you should put the manifest property into the html tag. Such as

```
<html manifest="demo.appcache">
</html>
```

Manifest file is consist of three part, cache manifest, network and fallback.



