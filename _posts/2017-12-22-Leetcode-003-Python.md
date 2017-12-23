---
layout: post
title: "Leetcode 003"
data: 2017-12-22 14:58:59 +0900
categories: Leetcode
tag: Python
---

* content
{:toc}

This is about Hash method.

-------------------
Given a string, find the length of the longest substring without repeating characters.

**Examples:**

Given "abcabcbb", the answer is "abc", which the length is 3.

Given "bbbbb", the answer is "b", with the length of 1.

Given "pwwkew", the answer is "wke", with the length of 3. Note that the answer must be a substring, "pwke" is a subsequence and not a substring.




-------------------
In order to solve this problem. First I set a cache to store the brief part of the input, and use a node to judge if it is inside the cache. 

This is my first solution, but it is time exceded. Only the final input on Leetcode can not be passed. This time cosuming is N square and the space consuming is N.

		class Solution(object):
		    def lengthOfLongestSubstring(self, s):
		        """
		        :type s: str
		        :rtype: int
		        """
		        flag = 0
		        cache = []
		        big = 0
		        count = 0
		        longth = len(s)
		        if longth == 1:
		            return 1
		        while not count == longth:
		            flag = 0
		            for i in s[count:]:
		                if flag == 0:
		                    if i in cache:
		                        big = max(big,len(cache))
		                        cache = []
		                        flag = 1
		                    else:
		                        cache.append(i)
		            count = count + 1
		        return big
		            

In order to pass the exam. I try the second method.
This is my second solution. It use the slide space method.

		class Solution(object):
		    def lengthOfLongestSubstring(self, s):
		        """
		        :type s: str
		        :rtype: int
		        """
		        start = 0
		        end = 0
		        ans = 0
		        countDict = {}
		        for i in s:
		            end = end + 1
		            countDict[i] = countDict.get(i,0) + 1
		            while countDict[i] > 1:
		                countDict[s[start]] -= 1
		                start = start + 1
		            ans = max(ans,end - start)
		        return ans


            