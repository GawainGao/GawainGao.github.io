---
layout: post
title: "Markdown Keywords(1)"
data: 2017-12-22 15:17:50 +0900
categories: Markdown
tag: Markdown
---

* content
{:toc}


Some special in this theme      {#Special}
==========================================
+ Can make a list
------------------------------------------
		+ Can make a list

+ We need the [link](http://github.com/)
------------------------------------------
		[Github](https://github.com/)

+ We can deep the 'words'
------------------------------------------
		'Deep in the heart'

+ We can make textfile
------------------------------------------
		Two tab can make it.

```bash
This way also can achieve. Use the bash, and this can start from the initial of one line.
```

+ We need some method to jump [Jump](#jump)
------------------------------------------

<span id=jump>
```bash		
[Jump](#jump2)
<span id=jump2>
```
+ We can add the image
------------------------------------------
<img src="{{ '/assets/umaru2.jpg' | prepend: site.baseurl }}" alt="Umaru" width="310" />
		<img src="{{ '/route' | prepend: site.baseurl }}" alt="message" width="big?" />




