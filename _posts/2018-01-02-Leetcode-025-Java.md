---
layout: post
title: "Leetcode 025 | Reverse Nodes in k-Group"
date: 2018-01-03 18:20:52 +0900
categories: Leetcode
tag: Java
---

* content
{:toc}


Reverse Nodes in k-Group
-----

Given a linked list, reverse the nodes of a linked list k at a time and return its modified list.

k is a positive integer and is less than or equal to the length of the linked list. If the number of nodes is not a multiple of k then left-out nodes in the end should remain as it is.

You may not alter the values in the nodes, only nodes itself may be changed.

Only constant memory is allowed.

__For example__,
Given this linked list: `1->2->3->4->5`

For k = 2, you should return: `2->1->4->3->5`

For k = 3, you should return: `3->2->1->4->5`



Method
-----
This is very difficult. Describe a new fuction used for reverse one group and return the last node of this gourp, then set the prev node at this node. Use a counter start from 1 to k, when 1 to k-1, just move the head node to after one, when reach to k, do the reverse, set the next prev node and the new head node.



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
    public ListNode reverseKGroup(ListNode head, int k) {
        if(head == null || k == 1) return head;
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode pre = dummy;
        int i = 0;
        while(head != null){
            i++;
            if(i % k ==0){
                pre = reverse(pre, head.next);
                head = pre.next;
            }else {
                head = head.next;
            }
        }
        return dummy.next;
        
    }
    private static ListNode reverse(ListNode pre, ListNode next){
        ListNode last = pre.next;
        ListNode cur = last.next;
        while(cur != next){
            last.next = cur.next;
            cur.next = pre.next;
            pre.next = cur;
            cur = last.next;
        }
        return last;
    }
    
}
```