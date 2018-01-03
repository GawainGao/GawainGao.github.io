---
layout: post
title: "JavaScript studying"
data: 2017-12-24 17:35:50 +0900
categories: Study
tag: JavaScript
---

* content
{:toc}





JavaScript
-----
JavaScript is slight language and can be insert into the HTML.

* `document.write`
* `onclick`
* `document.getElementById()`
* `x.innerHTML`
* `x.style.color`
* `if isNaN(x)`
* `/* */`
* `//`
* `var`
* `new Array()`
* `var objective{name:value}`

JavaScript Object
-----
Like python, JavaScript is also a language with object. Maybe it can also be called as OOP language. Each object have itself method and property.

* `variablename=(condition)?value1:value2`
* JS also have `if`, `case`, `for`, `in`, `while`, `do`
* `break` and `countinue` also can be used to jump to a label.
* JS also can do `try`, `catch` and `throw`

JavaScript HTML DOM
----
* `x.getElementsByTagName("p")`
* `x=document.getElementById("intor")`
* `<body onload="checkCookies()">`
* `onmouseover`, `onmouseout`, `onmousedown`, `onmouseup`, `onclick`

If you want to add some element. You must first use create node to generate some element, then add into the parent. If you want to delete some element, use the same way.

JavaScript OOP
----
We can use the same method as python to generate the object inside the function. 

The `this` is like the `self` inside python. And when you want to generate new object, please use the `new` keyword.

JavaScript Window
-----
* `window.open()`
* `window.innerWideth`
* `document.body.clientWidth`
* `window.close()`
* `window.moveTo()`
* `window.resizeTo()`
* `screen.availHeight`
* `screen.availWidth`
* `location.hostname`
* `location.pathname`
* `location.port`
* `location.protocol`
* `location.herf`
* `location.assign()`
* `history.back()`
* `history.foward`
* `setTimeout("JS sentense",ms)


JavaScript Set Cookie
----

```
function setCookie(c_name, value, expiredays)
{
var exdate = new Date()
exdate.setDate(exdate.getDate()+expiredays)
document.cookie=c_name+"="escape(value)+((expiredays==null)?"":";expires="exdate.toGMTString())
}
```

