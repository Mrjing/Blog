---
title: JS实现插入排序
date: 2017-07-24 10:45:12
tags:
- 算法
- 插入排序
categories: [算法]
---
## JS实现插入排序 ##
代码如下:
```
function selectionSort(arr) {
    console.time("插入排序耗时");
    
    console.timeEnd("插入排序耗时");
}


var arr = [2,1,33,2,4,5,0,3,9,1];
var arr1 = [1,2,3,4,5,6,7,8,9,10];

bubbleSort(arr);
console.log(arr);

bubbleSort(arr1);
console.log(arr1);
```

代码耗时:
![](http://ostqsmxg6.bkt.clouddn.com/17-7-24/25489042.jpg)

时间复杂度分析:
平均情况: O(n^2)
最优情况: O(n^2)  
最差情况: O(n^2)
无论原始数组是否排过序，都要花费O(n^2)时间复杂度

