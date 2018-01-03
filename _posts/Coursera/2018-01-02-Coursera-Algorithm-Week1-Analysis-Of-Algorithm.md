---
layout: post
title: "Coursera Algorithm (Week1-Union-Find)"
date: 2018-01-02 08:39:17
categories: Coursera
tag: Human
---

* content
{:toc}




Coursera_Algorithm_Week1_Analysis-of-Algorithm_Assignment
----





Q1 3-SUM in quadratic time
----
Q1: 3-SUM in quadratic time. Design an algorithm for the 3-SUM problem that takes time proportional to n2 in the worst case. You may assume that you can sort the n integers in time proportional to n2 or better.

Note: these interview questions are ungraded and purely for your own enrichment. To get a hint, submit a solution.


Hint 01
----
Hint: given an integer 𝚡 and a sorted array 𝚊[] of n distinct integers, design a linear-time algorithm to determine if there exists two distinct indices 𝚒 and 𝚓 such that 𝚊[𝚒]+𝚊[𝚓]==𝚡.


A1
-----
Use the weighted QU method, since the worst-case time is N + M log N, the time can be accepted.
Use the union method to deal with two people, when at timestamps the two people became friends, connect team. Use the weighted QU method so that if all the people know each other by friends means, this tree will have only one root. So check the root number every time finish connected.
Since checking the root number also will time consuming, we can set a count number as the total root number. If the union method happened, this number decrease one. When this count number become 1, the social network is finished.
So we can have the timestamps, every time input a pair or people {a, b}, set root number N.
Method-1: To find "a" is connecting with "b" or not. If not, method-2, else, pass.
Method-2: To union "a" with "b" && decrease root number for one.
Method-3: Check root number, if reach to 1, finished.



Q2 Search in a bitonic array
----


Q2: Search in a bitonic array. An array is bitonic if it is comprised of an increasing sequence of integers followed immediately by a decreasing sequence of integers. Write a program that, given a bitonic array of n distinct integer values, determines whether a given integer is in the array.

Standard version: Use ∼3lgn compares in the worst case.
Signing bonus: Use ∼2lgn compares in the worst case (and prove that no algorithm can guarantee to perform fewer than ∼2lgn compares in the worst case).


Hint 02
----
Hints: Standard version. First, find the maximum integer using ∼1lgn compares—this divides the array into the increasing and decreasing pieces.

Signing bonus. Do it without finding the maximum integer.


A2
----
Use three binary search. First for peak and the other two search in increasing array and decreasing array individually.





Q3 Egg drop
-----
Q3: Egg drop. Suppose that you have an n-story building (with floors 1 through n) and plenty of eggs. An egg breaks if it is dropped from floor T or higher and does not break otherwise. Your goal is to devise a strategy to determine the value of T given the following limitations on the number of eggs and tosses:

Version 0: 1 egg, ≤T tosses.
Version 1: ∼1lgn eggs and ∼1lgn tosses.
Version 2: ∼lgT eggs and ∼2lgT tosses.
Version 3: 2 eggs and ∼2n√ tosses.
Version 4: 2 eggs and ≤cT‾‾√ tosses for some fixed constant c.



Hint 03
-----
Hints:

Version 0: sequential search.
Version 1: binary search.
Version 2: find an interval containing T of size ≤2T, then do binary search.
Version 3: find an interval of size n‾‾√, then do sequential search. Note: can be improved to ∼2n‾‾‾√ tosses.
Version 4: 1+2+3+…+t∼12t2. Aim for c=22‾‾√.


A3
-----
Version 0: Throw from 1-layer, each layer by each.
Version 1: Binary mode, throw at the middle each time.
Version 2: From 1 to 2 to 4 to 8.
Version 3: Throw at n square, if broken, then 1 to n square, else, i*n square.
Version 4: From 1 to 3 to 6 to 10...Then use the second one the check.

