---
layout: post
title: "Leetcode 002"
date: 2017-12-21 17:49:50 +0900
categories: Leetcode
tag: Python
---

* content
{:toc}




This data structure is about linked list.

-------------------
The origianl question is as follow.

You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

*Example*

		Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
		Output: 7 -> 0 -> 8
		Explanation: 342 + 465 = 807.

This can be solved by setting the flag to count if a number is carry or not.
We should judge the length of the two list. A good method is looping the two list together. Which stop faster means the list is shorter.

This is my solution.

		# Definition for singly-linked list.
		# class ListNode(object):
		#     def __init__(self, x):
		#         self.val = x
		#         self.next = None

		class Solution(object):
		    def addTwoNumbers(self, l1, l2):
		        """
		        :type l1: ListNode
		        :type l2: ListNode
		        :rtype: ListNode
		        """
		        flag = 0
		        if l1 == None: return l2
		        if l2 == None: return l1
		        dummy = ListNode(0); res = dummy
		        while l1 and l2:
		            res.next = ListNode((l1.val+l2.val+flag) % 10)
		            flag = (l1.val+l2.val+flag) / 10
		            l1 = l1.next
		            l2 = l2.next 
		            res = res.next
		            
		        if l2:
		            while l2:
		                res.next = ListNode((l2.val+flag) % 10)
		                flag = (l2.val+flag) / 10
		                l2 = l2.next
		                res = res.next
		        if l1:
		            while l1:
		                res.next = ListNode((l1.val+flag) % 10)
		                flag = (l1.val+flag) / 10
		                l1 = l1.next
		                res = res.next
		                
		        if flag == 1: res.next = ListNode(1)
		        return dummy.next

            