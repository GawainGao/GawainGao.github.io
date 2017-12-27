---
layout: post
title: "Leetcode 004"
date: 2017-12-22 15:01:50 +0900
categories: Leetcode
tag: Python
---

* content
{:toc}





Question
-------------------
The origianl question is as follow.

There are two sorted arrays nums1 and nums2 of size m and n respectively.

Find the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).

		Example 1:
		nums1 = [1, 3]
		nums2 = [2]

The median is 2.0
		Example 2:
		nums1 = [1, 2]
		nums2 = [3, 4]

The median is (2 + 3)/2 = 2.5

--------------------
This problem is the first complicated problem in Leetcode. But if you have read the books about algrithome. This is very similar to the binary sereach. Each time just remove the N/2 elements from the initial array and decrease the order of the target number. The time cosuming is log(N)



		class Solution(object):
		    def findMedianSortedArrays(self, nums1, nums2):
		        """
		        :type nums1: List[int]
		        :type nums2: List[int]
		        :rtype: float
		        """
		        lenA = len(nums1); lenB = len(nums2)
		        if (lenA + lenB) % 2 == 1: 
		            return self.findKth(nums1, nums2, (lenA + lenB)/2 + 1)
		        else:
		            return (self.findKth(nums1, nums2, (lenA + lenB)/2) + self.findKth(nums1, nums2, (lenA + lenB)/2 + 1)) * 0.5 
		    
		    
		    
		    def findKth(self, nums1, nums2, k):
		        if len(nums1) == 0:
		            return nums2[k-1]
		        if len(nums2) == 0:
		            return nums1[k-1]
		        if len(nums2) > len(nums1):
		            return self.findKth(nums2,nums1,k)
		        if k == 1:
		            return min(nums1[0],nums2[0])
		        p = min(k / 2, len(nums2))
		        if nums1[p-1] < nums2[p-1]:
		            return self.findKth(nums1[p:],nums2,k-p)
		        else:
		            return self.findKth(nums1,nums2[p:],k-p)







            