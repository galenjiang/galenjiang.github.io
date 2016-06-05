---
title: 背景透明度 兼容IE
date: 2015-09-08 00:32:46
tags: [css]
---



* 背景透明度
```css
background:url("../images/space.gif") 0 0 repeat; filter:progid:DXImageTransform.Microsoft.gradient(startColorstr=#BF000000,endColorstr=#BF000000);}
```
* 渐变
```css
filter:progid:DXImageTransform.Microsoft.gradient(startColorstr=#BF000000,endColorstr=#BF000000);
```
[参考网址](http://segmentfault.com/a/1190000002485299)

* 透明度
```css
-ms-filter: "progid:DXImageTransform.Microsoft.Alpha(opacity=60)"; /* for IE8 in IE7 mode */

filter: alpha(opacity=60); /* for IE6-IE8 */
```

* 兼容圆角
[http://css3pie.com/](http://css3pie.com/)