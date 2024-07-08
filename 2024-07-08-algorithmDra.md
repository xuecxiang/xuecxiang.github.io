---
layout:     post
title:      "Hello 2024/7/9"
subtitle:   " \"Hello World, Hello Blog\""
date:       2024-07-08 14:00:00
author:     "xuecxiang"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - Meta
---

> “Yeah It's on. ”

算法学习笔记记录：
二分查找(Binary search)：

##正文
`
//二分查找
    public static boolean exsit(int[] arr, int num){
        if(arr == null || arr.length == 0){
            return false;
        }
        int l = 0, r = arr.length - 1, m = 0;
        while(l <= r){
            //更加安全的写法，意思是l向r移动了一般的位置
            m = l + (r - l) / 2;
            //m = l + ((r - l) >> 1);
            if(arr[m] == num){
                return true;
            }else if(arr[m] > num){
                //...........150........
                //            m
                // ..........r............
                r = m - 1;
            }else{
                l = m + 1;
            }
        }
        return false;

    }
`

找大于num的最左侧的数
`
 public static int findleft(int[] arr, int num){
        int l = 0, r = arr.length - 1, m = 0;
        int ans = -1;
        while(l <= r){
            m = l + ((r - l) >> 1);
            if(arr[m] >= num){
                ans = m;
                r = m - 1;
            }else{
                r = m + 1;
            }
        }
        return ans;
    }
`

找小于num的最右侧的数
`
public static int findRight(int[] arr, int num){
        int l = 0, r = arr.length - 1, m = 0;
        int ans = -1;
        while(l <= r){
            m = l + ((r - l) >> 1);
            if(arr[m] <= num){
                //满足记下ans，往右二分
                l = m + 1;
                ans = m;
            }else{
                //不满足不记ans，往左二分
                r = m - 1;
            }
        }
        return ans;
    }
`

