---
layout: post
title: "Leetcode 006 | ZigZag Conversion"
date: 2017-12-27 22:24:33 +0900
categories: Leetcode
tag: Python
---

* content
{:toc}







ZigZag Conversion
---------

The string "PAYPALISHIRING" is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)


```
P   A   H   N
A P L S I I G
Y   I   R
```


And then read line by line: "PAHNAPLSIIGYIR"
Write the code that will take a string and make this conversion given a number of rows:

```
string convert(string text, int nRows);
```


convert`("PAYPALISHIRING", 3)` should return `"PAHNAPLSIIGYIR"`.


Method
--------
Array the input, get the mode of the number.






Python Code
--------------


```
class Solution(object):
    def convert(self, s, numRows):
        """
        :type s: str
        :type numRows: int
        :rtype: str
        """
        if numRows <= 1 or numRows >= len(s):
            return s
        arr = [''] * numRows
        line, step = 0, -1
        for c in s:
            arr[line] += c
            if line % (numRows-1) == 0:
                step = - step
            line += step
        return ''.join(arr)
```