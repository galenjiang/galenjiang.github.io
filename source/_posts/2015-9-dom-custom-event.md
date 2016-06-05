---
title: DOM 自定义事件，观察者模式
date: 2015-09-07 14:22:52
tags: [javascript]
---
[漫谈js自定义事件、DOM/伪DOM自定义事件](http://www.zhangxinxu.com/wordpress/2012/04/js-dom%E8%87%AA%E5%AE%9A%E4%B9%89%E4%BA%8B%E4%BB%B6/)

一部分代码
```
$(function() {
  var div1 = document.getElementById("div1");
  div1.addEventListener("todo", function() {
    alert("todo")
  });
  // 创建
  var evt = document.createEvent("HTMLEvents");
  // 初始化
  evt.initEvent("todo", false, false);
  // 触发, 即弹出文字
  div1.dispatchEvent(evt);
})
```