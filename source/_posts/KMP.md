---
title: KMP模版
date: 2023-02-21 09:25:00
author: Keyon
img: https://pic4.zhimg.com/v2-666eb28ba8e686a26ae7295cd6a2a47a\_r.jpg
top: false
cover: true
coverImg: https://pic4.zhimg.com/v2-666eb28ba8e686a26ae7295cd6a2a47a\_r.jpg
password: 8d969eef6ecad3c29a3a629280e686cf0c3f5d5a86aff3ca12020c923adc6c92
toc: true
mathjax: false
categories: Leetcode
summary: 2.21的leetcode
tags:
  - leetcode
---

``` java 
int [] next = new int [n];  
next[0] = 0;  
for(int i = 1, j = 0; i<n;i++){  
   while(j > 0 && needle.charAt(i) != needle.charAt(j)){  
      j = next[j - 1];  
   }  
   if(needle.charAt(i) == needle.charAt(j)){  
      j++;  
   }  
   next[i] = j;  
}  
for(int i = 0, j = 0; i < haystack.length();i++){  
   while(j > 0 && needle.charAt(j) != haystack.charAt(i)){  
      j = next[j - 1];  
  
   }  
   if(needle.charAt(j) == haystack.charAt(i)){  
      j++;  
   }  
   if(j == n){  
      return i - j + 1;  
   }  
  
}  
return -1;

``` 

使用不减一的next生成方法。

next中的值代表多少个前后缀匹配。
next生成
1. 初始化
2. 不匹配的时候跳转为前一个的next数组值
3. 匹配的时候j++