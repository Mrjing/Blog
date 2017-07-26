---
title: JS实现快速排序
date: 2017-07-24 10:45:12
tags:
- 算法
- 归并排序
categories: [算法]
---
## JS实现快速排序 ##
代码如下:
```javascript
function exchange(arr, i, j){//交换数组中索引为i,j的两元素
    var temp = arr[i];
    arr[i] = arr[j];
    arr[j] = temp;
}

function partition(arr, left, right){//找到枢纽元素在排好序的数组的位置，取值为arr[right]
    if(left < right){
        var pivot = arr[right];
        var i = left,
            j = right - 1;
        while(i < j){
            while(arr[i] <= pivot){
                i++;
            }
            while(arr[j] > pivot){
                j--;
            }
            if(i < j){
                exchange(arr, i, j);
            }else{
                break;
            }
        }
        exchange(arr, j+1, right);
        return j+1;
    }

}

function quickSort(arr, left, right){
    var partitionIndex = partition(arr, left, right);
    if(partitionIndex !== undefined){
        quickSort(arr, left, partitionIndex-1);
        quickSort(arr, partitionIndex+1, right);
    }
}

var arr  = [2,1,33,2,4,5,0,3,9,1];
var arr1 = [1,2,3,4,5,6,7,8,9,10];

console.time("快速排序耗时");
quickSort(arr, 0, arr.length-1);
console.timeEnd("快速排序耗时");
console.log(arr);

console.time("快速排序耗时");
quickSort(arr1, 0, arr.length-1);
console.timeEnd("快速排序耗时");
console.log(arr1);

```

代码耗时:
![](http://ostqsmxg6.bkt.clouddn.com/17-7-26/32185227.jpg)

网上有人写的更加简单的快排如下：
```
var quickSort2 = function(arr) {
    if (arr.length <= 1) {
        return arr;
    }　　
    var pivotIndex = Math.floor(arr.length / 2);　　
    var pivot = arr.splice(pivotIndex, 1)[0];　　
    var left = [];　　
    var right = [];　　
    for (var i = 0; i < arr.length; i++) {　　　　
        if (arr[i] < pivot) {　　　　　　
            left.push(arr[i]);　　　　
        } else {　　　　　　
            right.push(arr[i]);　　　　
        }　　
    }
    return quickSort2(left).concat([pivot], quickSort2(right));
};
```



时间复杂度分析:
平均情况: O(nlogn)
最优情况: O(nlogn)  
最差情况: O(n^2)

是一种不稳定的排序算法
