---
layout: post
title: "Leetcode 080 | Remove Duplicates from Sorted Array II"
date: 2018-01-02 22:41:33 +0900
categories: Leetcode
tag: Java
---

* content
{:toc}








Remove Duplicates from Sorted Array II
------------
Follow up for "Remove Duplicates":
What if duplicates are allowed at most twice?

For example,
Given sorted array nums = [1,1,1,2,2,3],

Your function should return length = 5, with the first five elements of nums being 1, 1, 2, 2 and 3. It doesn't matter what you leave beyond the new length.






Method
----
Use two node.


Solution
-----
```
class Solution {
    public int removeDuplicates(int[] A) {
		if (A == null || A.length == 0)
			return 0;
 
		int pre = A[0];
		boolean flag = false;
		int count = 0;
 
		// index for updating
		int o = 1;
 
		for (int i = 1; i < A.length; i++) {
			int curr = A[i];
 
			if (curr == pre) {
				if (!flag) {
					flag = true;
					A[o++] = curr;
 
					continue;
				} else {
					count++;
				}
			} else {
				pre = curr;
				A[o++] = curr;
				flag = false;
			}
		}
 
		return A.length - count;
    }
}
```