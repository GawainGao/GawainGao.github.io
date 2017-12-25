---
layout: post
title: "Leetcode 005"
date: 2017-12-26 03:44:23 +0900
categories: Leetcode
tag: Python
---

* content
{:toc}





Longest Palindromic Substring
-----
Given a string s, find the longest palindromic substring in s. You may assume that the maximum length of s is 1000.

**Example:**

```
Input: "babad"

Output: "bab"

Note: "aba" is also a valid answer.
```
**Example:**

```
Input: "cbbd"

Output: "bb"
```

My Solution
-----
There is two situation, odd number result and even number result.
I set a middle number, and search from the middle number to the two side. If the result is terminal max, memorize into the `cache` and renew the `start node` and the `end node`.

The code is divide into two parts, odd number result and even number result.



```
class Solution(object):
    def longestPalindrome(self, s):
        """
        :type s: str
        :rtype: str
        """
        if s[0] == None:
            return None
        cache = s[0]
        m = 1
        l = len(s)
        start,end = 0,0
        for i in range(l):
            for k in range(min((l-i-1),i)+1):
                if k == 0:
                    pass
                elif s[i-k] == s[i+k]:
                    start = i - k
                    end = i + k
                    if m < (2*k + 1):
                        m = 2*k + 1
                        cache = s[start:end+1]
                else:
                    break
        for i in range(l-1):
            if s[i] == s[i + 1]:
                if m == 1:
                    m = 2
                    cache = s[i:i+2]
                for k in range(min(i,(l-i-2))+1):
                    if k == 0:
                        pass
                    elif s[i-k] == s[i+1+k]:
                        start = i - k
                        end = i + k + 1
                        if m < (2*k+2):
                            m = 2*k+2
                            cache = s[start:end+1]
                    else:
                        break

        return cache
```