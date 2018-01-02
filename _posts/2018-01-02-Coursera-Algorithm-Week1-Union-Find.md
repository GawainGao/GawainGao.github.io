---
layout: post
title: "Coursera Algorithm (Week1-Union-Find)"
date: 2018-01-02 08:32:17
categories: Coursera
tag: Human
---

* content
{:toc}




Coursera_Algorithm_Week1_Union-Find_Assignment
----





Q1 Social network connectivity
----
Q1: **Social network connectivity**. Given a social network containing n members and a log file containing m timestamps at which times pairs of members formed friendships, design an algorithm to determine the earliest time at which all members are connected (i.e., every member is a friend of a friend of a friend ... of a friend). Assume that the log file is sorted by timestamp and that friendship is an equivalence relation. The running time of your algorithm should be mlogn or better and use extra space proportional to n.

**Note**: these interview questions are ungraded and purely for your own enrichment. To get a hint, submit a solution.


Hint 01
----
Hint: union−find.


A1
-----
Use the weighted QU method, since the worst-case time is N + M log N, the time can be accepted.
Use the union method to deal with two people, when at timestamps the two people became friends, connect team. Use the weighted QU method so that if all the people know each other by friends means, this tree will have only one root. So check the root number every time finish connected.
Since checking the root number also will time consuming, we can set a count number as the total root number. If the union method happened, this number decrease one. When this count number become 1, the social network is finished.
So we can have the timestamps, every time input a pair or people {a, b}, set root number N.
Method-1: To find "a" is connecting with "b" or not. If not, method-2, else, pass.
Method-2: To union "a" with "b" && decrease root number for one.
Method-3: Check root number, if reach to 1, finished.






Q2 Union-find with specific canonical element
----


Q2: **Union-find with specific canonical element**. Add a method 𝚏𝚒𝚗𝚍() to the union-find data type so that 𝚏𝚒𝚗𝚍(𝚒) returns the largest element in the connected component containing i. The operations, 𝚞𝚗𝚒𝚘𝚗(), 𝚌𝚘𝚗𝚗𝚎𝚌𝚝𝚎𝚍(), and 𝚏𝚒𝚗𝚍() should all take logarithmic time or better.

**For example**, if one of the connected components is {1,2,6,9}, then the 𝚏𝚒𝚗𝚍() method should return 9 for each of the four elements in the connected components.



Hint 02
----
Hint: maintain an extra array to the weighted quick-union data structure that stores for each root 𝚒 the large element in the connected component containing 𝚒.






A2
----
Use the weighted QU method, define a new way called "SetRoot", this method is used to change the position between insert element and the root, which one is bigger, set it at the root position.
Since each time we will get the root is biggest's tree, so when we do weighted combine, just compare the two root number is enough. This need one time compare in each connection.





Q3 Successor with delete
-----
Q3: **Successor with delete**. Given a set of n integers S={0,1,...,n−1} and a sequence of requests of the following form:

* Remove x from S
* Find the successor of x: the smallest y in S such that y≥x.

design a data type so that all operations (except construction) take logarithmic time or better in the worst case.



Hint 03
----
Hint: use the modification of the union−find data discussed in the previous question.



A3
-----
Set a array to show a number is removed or not.

Set a array to show the max node in "i"-root-tree. If the "i" is removed, search the max node is "i+1"-tree.

