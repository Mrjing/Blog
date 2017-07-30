---
title: JS实现插入排序
date: 2017-07-24 10:45:12
tags:
- 算法
- 插入排序
categories: [算法]
---
<p></p>
<!-- more -->
## JS实现插入排序 ##
代码如下:
```javascript
function insertSort(arr){
    console.time("插入排序耗时");
    if(arr.length > 1){//一个数时不必要排序
        for(let i = 1;i < arr.length;i++){
            let temp = arr[i];//暂存arr[i]的值，因这个值可能被前面的值覆盖
            let j = i - 1;
            for(;j >= 0;j--){
                if(arr[j] > temp){
                    arr[j+1] = arr[j];
                }else{
                    break;
                }
            }
            arr[j+1] = temp;

        }
    }
    console.timeEnd("插入排序耗时");
}

var arr = [2,1,33,2,4,5,0,3,9,1];
var arr1 = [1,2,3,4,5,6,7,8,9,10];

insertSort(arr);
console.log(arr);

insertSort(arr1);
console.log(arr1);
```

代码耗时:
![](http://ostqsmxg6.bkt.clouddn.com/17-7-25/61978275.jpg)

```
function binaryInsertionSort(arr){
    console.time("二分查找插入排序耗时");
    if(arr.length > 1){
        for(let i = 1;i < arr.length;i++){
            let temp = arr[i];
            let left = 0,
                right = i - 1,
                index = i;
            while(left <= right){
                let mid = parseInt((left + right)/2);
                if(arr[mid] == temp){
                    index = mid;
                    break;
                }else if(arr[mid] < temp){
                    left = mid + 1;
                }else{
                    right = mid - 1;
                }
            }
            if(index == i){//没找到时，取right+1处
                index = right+1;
            }   
            if(index < i){
                for(let j = i-1;j >= index;j--){//将index至i - 1处的值向后一位
                    arr[j+1] = arr[j];
                }
                arr[index] = temp;
            }   
        }
    }
    console.timeEnd("二分查找插入排序耗时");
}

var arr = [2,1,33,2,4,5,0,3,9,1];
var arr1 = [1,2,3,4,5,6,7,8,9,10];

insertSort(arr);
console.log(arr);

insertSort(arr1);
console.log(arr1);
```

![](http://ostqsmxg6.bkt.clouddn.com/17-7-25/6907862.jpg)

比较了之后，发现数据量较小时，二分查找插入反而耗的时间比较多，特别是对于已排好序的序列，直接插入只需要遍历一遍，而二分查找插入仍然需要在每一轮进行二分查找，耗时明显增大

时间复杂度分析:
平均情况: O(n^2)
最优情况: O(n) (已排好序的数组只需要遍历一次)  
最差情况: O(n^2) (反序的话花费时间最长)

