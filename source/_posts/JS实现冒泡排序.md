---
title: JS实现冒泡排序
date: 2017-07-24 10:45:12
tags:
- 算法
- 冒泡排序
categories: [算法]
---
## JS实现冒泡排序 ##
代码如下:
```
function bubbleSort(arr) {
    var temp;
    console.time("冒泡排序耗时");
    for(var i = arr.length - 1;i >= 0;i--){
        var flag = false;
        for(var j = 0;j < i;j++){
            if(arr[j] > arr[j+1]){
                flag = true;
                temp = arr[j];
                arr[j] = arr[j+1];
                arr[j+1] = temp;
            }
        }
        if(!flag){
            break;
        }
    }
    console.timeEnd("冒泡排序耗时");
}


var arr = [2,1,33,2,4,5,0,3,9,1];
var arr1 = [1,2,3,4,5,6,7,8,9,10];

bubbleSort(arr);
console.log(arr);

bubbleSort(arr1);
console.log(arr1);
```

![](http://ostqsmxg6.bkt.clouddn.com/17-7-24/59367892.jpg)
