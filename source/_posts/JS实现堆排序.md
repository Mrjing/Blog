---
title: JS实现堆排序
date: 2017-07-27 10:29:12
tags:
- 算法
- 堆排序
categories: [算法]
---
## JS实现堆排序 ##
代码如下:
```javascript
//维护堆的性质
function heapify(arr, index, length){
    var left = index*2 + 1;
    var right = index*2 + 2;
    var largest = index;
    var temp;
    if(left < length && arr[left] > arr[largest]){
        largest = left;
    }
    if(right < length && arr[right] > arr[largest]){
        largest = right;
    }
    if(largest !== index){//最大值索引不是初始的索引时
        temp = arr[index];
        arr[index] = arr[largest];
        arr[largest] = temp;
        //继续解决交换过来的节点对堆造成的影响
        heapify(arr, largest, length);
    }

}

//堆排序
function heapSort(arr){
    console.time("堆排序耗时");
    var length = arr.length;
    var temp;
    //首先对这个无序数组构建最大堆
    for(var i = parseInt(length/2) - 1;i >= 0;i--){
        heapify(arr, i, length);
    }

    // console.log(arr);
    //堆排序,每次选中堆顶与当前堆的最后一个元素交换，并维护当前堆的性质
    for(var j = length - 1;j > 0;j--){
        temp = arr[j];
        arr[j] = arr[0];
        arr[0] = temp;
        heapify(arr, 0, --length);
    }
    console.timeEnd("堆排序耗时");
}

var arr = [2,1,33,2,4,5,0,3,9,1];
heapSort(arr);
console.log(arr);

var arr1 = [10,9,8,7,6,5,4,3,2,1];
heapSort(arr1);
console.log(arr1);

```

代码耗时:
![](http://ostqsmxg6.bkt.clouddn.com/17-7-27/35913870.jpg)


时间复杂度分析:
平均情况: O(nlogn)
最优情况: O(nlogn) 
最差情况: O(nlogn) 

