---
title: src资源请求
date: 2017-06-23 15:13:39
tags:
- bug
- 资源请求
categories: [bug记录]
---
## 由src资源请求导致的一次bug ##
在用node实现一个电影信息展示的网站后台时，遇到了由静态资源发出的请求产生的bug
*产生过程如下*
1. 首先存储了新的电影信息，然后向对应的详情页跳转
```javascript
res.redirect('/movie/' + movie._id);
```
2. 跳转到详情页路由后，用收到的movie数据进行页面的渲染(其中有一项是显示
电影的预告片)
```javascript
src="#{movie.flash}"
```
3. 此时bug出现，因为测试时填的flash(预告片这一项随便写的，
比如fkjksfka,而不是http://这种)，于是src会发出一个请求本地资源的请求,此时的页面地址是http://localhost:3000/movie/596dd2558520761ec83864b5，src发出的请求地址为http://localhost:3000/movie/fkjksfka，而这刚好又匹配了详情页路由，只不过带的不是movie的id，而是它的flash属性，这时查询数据库就直接报错









