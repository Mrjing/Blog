---
title: 前端面试 JS部分 Ajax
date: 2017-07-07 19:15:03
tags: 
- JS
categories: [JS]
---
<p></p>
<!-- more -->
## 基础知识 ##

### Ajax ###


*知识点*

** XMLHttpRequest **
```
var xhr = new XMLHttpRequest()
xhr.open("GET", "/api", false)
xhr.onreadystatechange = function(){//异步执行的函数
  if(xhr.readyState == 4){
    if(xhr.readyState == 4){
      if (xhr.status == 200){
        alert(xhr.responseText)
      }
    }
  }
}
xhr.send(null)
```

** 状态码说明 **
readyState定义
*  0-(未初始化)还没有调用send()方法
*  1-(载入)已调用send()方法，正在发送请求
*  2-(载入完成)send()方法执行完成，已经接收到全部响应内容
*  3-(交互)正在解析响应内容
*  4-(完成)响应内容解析完成，可以在客户端调用

status定义
*  2xx-表示成功处理请求，如200
*  3xx-需要重定向，浏览器直接跳转
*  4xx-客户端请求错误，如404
*  5xx-服务端错误

** 跨域 **

*什么是跨域*
* 浏览器有同源策略，不允许ajax访问其他域接口
* 跨域条件: 协议，域名，端口，有一个不同就算跨域

*可以跨域的三个标签及其使用场景*
```
<img src=xxx>  用于打点统计，统计网站可能是其他域
<link href=xxx>  可以使用CDN,CDN的也是其他域
<script src=xxx>  可以用于CDN, JSONP
```

*跨域注意事项*
*  所有的跨域请求都必须经过信息提供方允许
*  如果未经允许即可获取，那是浏览器同源策略出现漏洞

*JSONP*
```
<script>
window.callback = function(data){//提前定义好的函数，当之后返回的
  console.log(data)//跨域得到的信息
}
</script>
<script src="http://xxx.xx.xx/xx.js"></script>//假设访问服务器上这个js资源的
//时候, 服务器返回内容为callback({x:100, y:200})
```

*服务端设置http header*



*题目*

*  手动编写一个ajax,不依赖第三方库
*  跨域的几种实现方式
*  对于一个无限下拉加载图片的页面，如何给每个图片绑定事件 (运用代理)





