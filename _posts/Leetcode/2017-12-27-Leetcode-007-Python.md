---
layout: post
title: "Leetcode 007 | Reverse Integer"
date: 2017-12-27 22:27:33 +0900
categories: Leetcode
tag: Python
---

* content
{:toc}







Reverse Integer
---------

Given a 32-bit signed integer, reverse digits of an integer.

Note:
Assume we are dealing with an environment which could only hold integers within the 32-bit signed integer range. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.




Method
--------
Pay attention to the number limited.






Python Code
--------------


```
class Solution(object):
    def reverse(self, x):
        """
        :type x: int
        :rtype: int
        """
        minus = 0
        if x < 0:
            x = -x
            minus = 1
        res = 0
        flag = 0
        while x:
            flag = x % 10
            x = x / 10
            res = res * 10 + flag
        if minus:
            res = -res
        if res <= 0x7fffffff and res >= -0x7fffffff-1:
            return res
        else:
            return 0
```