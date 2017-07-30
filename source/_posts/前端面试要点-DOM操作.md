---
title: 前端面试 JS部分 DOM操作
date: 2017-07-08 19:15:03
tags: 
- JS
categories: [JS]
---
<p></p>
<!-- more -->
## 基础知识 ##

### DOM操作 ###


*知识点*

** DOM本质 **
浏览器拿到html代码，结构化一个浏览器能识别并且JS可操作的一个模型

** DOM节点操作 **
*  获取DOM节点
```
var div1 = document.getElementById('div1')//元素
var divList = document.getElementsByTagName('div')//集合
console.log(divList.length, divList[0])

var containerList = document.getElementsByClassName('.container')//集合
var pList = document.querySelectorAll('p')//集合
```

*  property
property指的是js对象的属性
```
var pList = document.querySelectorAll('p')
var p = pList[0]
console.log(p.style.width)//获取样式
p.style.width = '100px'//修改样式
console.log(p.className) //获取class
p.className = 'p1'//修改class

//获取nodeName 和nodeType
console.log(p.nodeName)
console.log(p.nodeType)

```

*  attribute
attribute指的是html标签中的属性
```
var pList = document.querySelectorAll('p')
var p = pList[0]
p.getAttribute('data-name')//data-name代指html标签中的属性
p.setAttribute('data-name', 'imooc')
p.getAttribute('style')
p.setAttribute('style', 'font-size:30px')
```

** DOM结构操作 **
*  新增节点
```
var div1 = document.getElementById('div1')
//添加新节点
var p1 = document.createElement('p')
p1.innerHTML = 'this is p1'
div1.appendCHild(p1)//添加新创建的元素
//移动已有节点
var p2 = document.getElementById('p2')
div1.appendChild(p2)//移动而非新增
```
*  获取父元素
```
var div1 = document.getElementById('div1')
var parent = div1.parentElement//获取父元素(即最近的祖先元素)
```

*  获取子元素
```
var child = div1.childNodes//获取子元素(子节点，如果子元素间有换行的话会产生
  //text节点(nodetype为3，元素标签的nodetype为1))
div1.removeChild(child[0])//移除子节点
```
*  删除节点

*题目*

*  DOM是哪种基本的数据结构
   树
*  DOM操作的常用API有哪些
*  DOM节点的attribute和property有何区别




