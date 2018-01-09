---
layout: post
title: "KMP Algorithm"
date: 2018-01-09 14:51:26 +0900
categories: Algorithm
tag: Java
---

* content
{:toc}










KMP method
----------
KMP method is a algorithm in String match. Since searching a short length string in a long length string, traditional method is test all the alphabat, it is time consuming.

KMP method set a new array called 'next'. This array showes how many same of the matching array's prefixes and suffixes. So that the matching array can move more than one position each time and decrease the total time cosuming.

In worse situation, is the matched array is M size and the matching array is N size. The time is M*(N-1).



Traditional Java code
------
```
class Solution {
    public int strStr(String haystack, String needle) {
        if(needle.length()==0){return 0;}
        for(int i=0;i<haystack.length();i++){
            if(haystack.length()-i+1<needle.length()){return -1;}
            int k = i;
            int j = 0;
            while(k<haystack.length()&&j<needle.length()&&haystack.charAt(k)==needle.charAt(j)){
                j++;
                k++;
                if(j==needle.length()){return i;}
            }
        }
        return -1;
    }
}
```


'next' array generation
-----
The longest common profixes and suffixes.


BM Algorithm
-----
Two rules:
* If not matched and bad letter, push to the letter after the bad letter.
* Good suffixes rule, if the same letter inside the matching string, move this range.

The time consuming is N.



Sunday Algorithm
-----
Two rules:
* If it is not matched, push the matching string to the next letter outside the string, if first outside letter is not inside the matching string, remove the top of the matching string to the next of the first outside letter
* If it is not matched, but the first outside letter is inside the matching letter, move them together.

This is the most fast.











