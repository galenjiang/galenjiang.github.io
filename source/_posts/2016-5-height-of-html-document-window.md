---
title: 网页中的window,html,document,body各种高度
date: 2016-05-26 15:27:14
tags:
---



* 选取document,html,body
```javascript
document //选取文档

document.documentElement // html

document.querySelector('body) // body
```

* window 的高度 屏幕尺寸
```javascript
window.innerHeight
```
> html body会塌缩
```
clientHeight // 视窗大小
scrollHeight //滚动高度
scrollTop // 滚动上边距高度
getBoundingClientRect // 相对视窗的 top, left
```

* 图片懒加载用到原理

```javascript
var oClass = document.querySelector('.class1');
oBody = document.querySelector('body');
var rect = oClass.getBoundingClientRect();
// var clientHeight = document.documentElement.clientHeight;
var height = oBody.scrollTop;

console.log(height,window.innerHeight);
window.addEventListener('scroll', function(){
    if(oBody.scrollTop + window.innerHeight + 20 > rect.top){
        console.log(1)
    }
})
window.addEventListener('scroll', function(){
    if(oBody.scrollTop + window.innerHeight + 20 > rect.top){
        console.log(2)
    }
})
```
