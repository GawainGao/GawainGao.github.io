---
layout: post
title: "CSS studying"
date: 2017-12-24 03:53:26 +0900
categories: Front
tag: CSS
---

* content
{:toc}









CSS
-----
CSS is used for set some style which will be used by all the pages.
If a part is defined by many different kind styles, they will be in order.

1. The inline sytle will be the most strong.
2. Browser setting.
3. Outside style.
4. Inside style.

It always use such a method to write.

```
selector { declaration: value }
```

Sometimes we can use contextual selectors to set the style. 

* `li strong{}` can be the contextual selectors.
* `h1 + p {}` can be selected by the adjacent sibling selector.
* Use the `#` to define the special id selector.
* Use the `.` to define the class selector.
* Use `.fancy td` as a derive selector.
* Use the `[lang = en]` as the property selector.

CSS settings
----
If you want to set a background.

```
a.radio {backgorund-image: url();
		   background-repeat: repeat-y;
		   background-position:center;
		   background-attachment:fixed;
		}
```

If you want to set the text style.

```
text-indent: 5em;
padding-left: 5em;
text-align:left;
word-spacing: 30px;
letter-spacing: 20px;
text-transform: uppercase;
text-decoration: underline;
white-space: normal;
```



