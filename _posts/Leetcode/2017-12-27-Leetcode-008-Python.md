
---
layout: post
title: "Leetcode 008 | String to Integer (atoi)"
date: 2017-12-27 22:46:33 +0900
categories: Leetcode
tag: Python
---

* content
{:toc}



String to Integer (atoi)
-----------
Implement atoi to convert a string to an integer.

Hint: Carefully consider all possible input cases. If you want a challenge, please do not see below and ask yourself what are the possible input cases.

Notes: It is intended for this problem to be specified vaguely (ie, no given input specs). You are responsible to gather all the input requirements up front.




Python code
---------

```
class Solution(object):
    def myAtoi(self, str):
        """
        :type str: str
        :rtype: int
        """
        if not str:
            return 0
        str = str.strip()
        s = 0
        flag = 1
        if len(str) == 1:
            if str[0] >='0' and str[0]<='9': return ord(str[0])-ord('0')
            else: return 0
        if str[0] == '-':
            str = str[1:]
            flag = -1
        elif str[0] == '+':
            str = str[1:]
        for c in str:
            if c >='0' and c<='9':
                s = 10 * s + ord(c) - ord('0')
            else:
                break
        s = s * flag
        s = s if s <=2147483647 else 2147483647
        s = s if s >=-2147483648 else -2147483648
        return s
```