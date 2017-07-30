---
title: 前端面试 JS部分 BOM操作
date: 2017-07-08 19:15:03
tags: 
- JS
categories: [JS]
---
<p></p>
<!-- more -->
## 基础知识 ##

### BOM操作 ###


*知识点*

** navigator  ** 
```
var ua = navigator.userAgent
var isChrome = ua.indexOf('Chrome')
console.log(isChrome)
```
** screen **
```
console.log(screen.width)
console.log(screen.height)
```

** location **
```
console.log(location.href)//地址
console.log(location.protocal)//协议
console.log(location.host)//域名
console.log(location.pathname)//路径
console.log(location.search)//查询字符串
console.log(location.hash)//#后面的hash值
```

** history **
```
history.back()
history.forward()
```

*题目*

*  如何检测浏览器的类型
*  拆解url的各部分





