---
layout: post
title: "URL route in CSS"
date: 2017-12-26 01:37:50 +0900
categories: Front
tag: CSS
---

* content
{:toc}




During insert the picture, the absolute url and the relative url both can be used. Since if you use the absolute url, there is a problem when you move the site, the absolute will changed. So it is better for us to use the relative url.

If you want to insert the background picture. You can use `background-image:url()` to insert a picture. The route of the picture should follow some rules.

If the css file position is: `Web/test/css/a.css`

If the picture file position is: `Web/Platform/images/icons/a.gif`

You should use `../` to show move to up folder.

```
background-image:url('../../Platform/images/icons/a.gif')
```

In this way we can set the background picture in the default file.
