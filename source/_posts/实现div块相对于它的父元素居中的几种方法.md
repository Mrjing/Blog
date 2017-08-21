---
title: div块相对于父元素垂直水平居中的方法
date: 2017-08-17 14:26:39
tags:
- css
categories: [css]
---
<p></p>
<!-- more -->
### 如何实现div块相对于它的父元素垂直水平居中  ###
css布局中经常会遇到居中布局的问题，现在总结一下可以实现垂直水平居中的方法
## 父子元素定宽高的情况 ##
在父子元素定宽高的情况下，实现子块垂直水平居中方法比较多，如下:

*  子元素相对于父元素绝对定位，并且left,top设为父元素宽高的一半，margin-left,margin-top设为子元素自身宽高一半
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        .parent{
            width:500px;
            height:500px;
            position: relative;
            background: red;
        }
        .child{
            width:200px;
            height:200px;
            position: absolute;
            left: 50%;
            top: 50%;
            margin-left: -100px;
            margin-top: -100px;
            background: green;
        }x
    </style>
</head>
<body>
    <div class="parent">
        <div class="child">
        </div>
    </div>
</body>
</html>
```

*  子元素相对于父元素绝对定位，并设margin:auto,left,right,top,bottom均为0，将上下左右边距(相对于父元素边缘)均设为0，使浏览器自动推算出外边距的上下，左右应该相等
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        .parent{
            width:500px;
            height:500px;
            background: red;
            position: relative;
        }

        .child{
            width:200px;
            height:200px;
            background: green;
            margin: auto;
            bottom: 0;
            left: 0;
            top: 0;
            right: 0;
            position: absolute;
        }


    </style>
</head>
<body>
    <div class="parent">
        <div class="child">
        </div>
    </div>
</body>
</html>

```

* 父元素设置display:table-cell,vertical-align:middle即可，子元素设置margin:auto
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        .parent{
            width: 500px;
            height: 500px;
            background: green;
            display: table-cell;
            vertical-align: middle; 
        }

        .child{
            width: 200px;
            height: 200px;
            background: yellow;
            margin: auto;
        }
    </style>
</head>
<body>
    <div class="parent">
        <div class="child">
        </div>
    </div>
</body>
</html>
```

*  类似于第一种，不过是css3的写法，子元素使用了transform: translate(-50%, -50%);
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        .parent{
            width:500px;
            height:500px;
            background: red;
            position: relative;
        }

        .child{
            width: 200px;
            height: 200px;
            background: green;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
        }
    </style>
</head>
<body>
    <div class="parent">
        <div class="child">
        </div>
    </div>
</body>
</html>
```

## 父元素定宽高，子元素不定宽高的情况  ##
*  子元素相对于父元素绝对定位，且设left,right和top, bottom分别相等的百分比
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        .parent{
            width: 500px;
            height: 500px;
            background: red;
            position: relative;
        }

        .child{
            background: green;
            position: absolute;
            left: 30%;
            right: 30%;
            top: 40%;
            bottom: 40%;
        }
    </style>
</head>
<body>
    <div class="parent">
        <div class="child">
        </div>
    </div>
</body>
</html>
```

## 父元素不定宽高，子元素定宽高的情况   ##

*  父元素设置display:flex;justify-content:center;align-items: center;后面两个属性作用分别是设置水平居中(默认的主轴是水平轴)和垂直居中
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        .parent{
            display: flex;
            justify-content: center;/* 水平居中，主轴是水平轴  */
            align-items: center; /* 垂直居中 */
            background: red;
        }

        .child{
            width:200px;
            height:200px;
            background: green;
        }
    </style>
</head>
<body>
    <div class="parent">
        <div class="child">
        </div>
    </div>
</body>
</html>
```