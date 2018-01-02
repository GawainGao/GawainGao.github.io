---
layout: post
title: "Leetcode 026 | Remove Duplicates from Sorted Array"
date: 2018-01-02 22:42:33 +0900
categories: Leetcode
tag: Java
---

* content
{:toc}


Remove Duplicates from Sorted Array
-----

Given a sorted array, remove the duplicates in-place such that each element appear only once and return the new length.

Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.

**Example**:
```
Given nums = [1,1,2],

Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively.
It doesn't matter what you leave beyond the new length.
```


Java code
---------

```
class Solution {
    public int removeDuplicates(int[] nums) {
        int j = 0;
        if (nums.length < 2){
            return nums.length;
        }
        for (int i = 1; i < nums.length; i++)
            if (nums[i] != nums[j]){
                j ++;
                nums[j] = nums[i];
            }
        return j + 1;
        
    }
}
```