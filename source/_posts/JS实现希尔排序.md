---
title: JS实现希尔排序
date: 2017-07-24 10:45:12
tags:
- 算法
- 希尔排序
categories: [算法]
---
<p></p>
<!-- more -->
## JS实现希尔排序 ##
代码如下:
```javascript
function shellSort(arr){
    console.time("希尔排序耗时");
    var length = arr.length;
    var h = 0;
    while(h <= length){//h 为步长
        h = h*3 + 1;
    }
    while(h >= 1){
        for(let i = h;i < length;i++){
            var temp = arr[i];
            let j = i - h;
            while(j >= 0 && arr[j] > temp){
                arr[j+h] = arr[j];
                j = j - h;
            }
            arr[j+h] = temp;
        }
        h = parseInt((h-1)/3);
    }
    console.timeEnd("希尔排序耗时");
}

var arr  = [2,1,33,2,4,5,0,3,9,1];
var arr1 = [1,2,3,4,5,6,7,8,9,10];

shellSort(arr);
console.log(arr);

shellSort(arr1);
console.log(arr1);


```


代码耗时:
![](http://ostqsmxg6.bkt.clouddn.com/17-7-26/77049104.jpg)

时间复杂度分析:
希尔排序的时间复杂度与步长有关

| 步长序列        | 最坏情况下复杂度|
|---------------|:-------------:|
| n/(2^i)      | O(n^2) |
| 2^i - 1      | O(n^1.5)      |


