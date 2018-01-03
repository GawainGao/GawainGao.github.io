---
layout: post
title: "Leetcode 024 | Swap Nodes in Pairs"
date: 2018-01-03 17:18:52 +0900
categories: Leetcode
tag: Java
---

* content
{:toc}


Swap Nodes in Pairs
-----

Given a linked list, swap every two adjacent nodes and return its head.

__For example__,
Given`1->2->3->4`, you should return the list as `2->1->4->3`.

Your algorithm should use only constant space. You may not modify the values in the list, only nodes itself can be changed.




Method
-----
Basic node.



Java Solution
-------

```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode swapPairs(ListNode head) {
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode pre = dummy;
        while (pre.next!=null && pre.next.next!=null){
            ListNode flag = pre.next.next;
            pre.next.next = flag.next;
            flag.next = pre.next;
            pre.next = flag;
            pre = flag.next;  
        }
        return dummy.next;
    }
}
```