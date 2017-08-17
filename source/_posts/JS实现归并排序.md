---
title: JS实现归并排序
date: 2017-07-26 10:45:12
tags:
- 算法
- 归并排序
categories: [算法]
---
<p></p>
<!-- more -->
## JS实现归并排序 ##
代码如下:
```javascript
function merge(arr, left, mid, right){
    let tempArr = [];
    for(let i =left;i <= right ;i++){
        tempArr[i] = arr[i];
    }
    let i = left,
        j = mid+1,
        index = left;
    while(i <= mid && j <= right){
        if(tempArr[i] <= tempArr[j]){
            arr[index++] = tempArr[i++];
        }else{
            arr[index++] = tempArr[j++];
        }
    }
    while(i <= mid){
        arr[index++] = tempArr[i++];
    }
    while(j <= right){
        arr[index++] = tempArr[j++];
    }
}

function mergeSort(arr, left, right){
    if(left < right){
        var left = left,
        right = right,
        mid = parseInt((left + right)/2);
        //数组分为2半，对每部分进行归并排序后，再对这整个数组排序
        mergeSort(arr, left, mid);
        mergeSort(arr, mid+1, right);
        merge(arr, left, mid, right);
    } 
}

var arr  = [2,1,33,2,4,5,0,3,9,1];
var arr1 = [1,2,3,4,5,6,7,8,9,10];

console.time("归并排序耗时");
mergeSort(arr, 0 ,arr.length-1);
console.timeEnd("归并排序耗时");
console.log(arr);

console.time("归并排序耗时");
mergeSort(arr1, 0 ,arr1.length-1);
console.timeEnd("归并排序耗时");
console.log(arr1);

```


代码耗时:
![](http://ostqsmxg6.bkt.clouddn.com/17-7-26/63400502.jpg)

时间复杂度分析:
平均情况: O(nlogn)
最优情况: O(n)  
最差情况: O(nlogn)

空间复杂度O(n)
是一种稳定的排序算法
