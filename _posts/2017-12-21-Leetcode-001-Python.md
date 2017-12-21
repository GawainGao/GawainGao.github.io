---
layout: post
title: "Leetcode 001"
data: 2017-12-21 17:31:50 +0900
categories: Leetcode
tag: Python
---

* content
{:toc}

This data structure is about dictrionary.
-------------------
The origianl question is as follow.

Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

*Example*

		Given nums = [2, 7, 11, 15], target = 9,

		Because nums[0] + nums[1] = 2 + 7 = 9,
		return [0, 1].

This can be solved by checking all the situation and the time consuming is N square.

This is my solution.

		class Solution(object):
 		   def twoSum(self, nums, target):
   		     """
		        :type nums: List[int]
		        :type target: int
		        :rtype: List[int]
		        """

		        for i in range(len(nums)):
		            for j in range(i+1,len(nums)):
		                if nums[i]+nums[j] == target:
		                      return [i,j] 


            