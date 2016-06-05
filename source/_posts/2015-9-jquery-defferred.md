---
title: Jqurey   deferred对象学习
date: 2015-09-08 00:09:26
tags: [javascript,jquery]
---
[jQuery的deferred对象详解](http://www.ruanyifeng.com/blog/2011/08/a_detailed_explanation_of_jquery_deferred_object.html)

[JS魔法堂：jsDeferred源码剖析](http://www.cnblogs.com/fsjohnhuang/p/4141918.html)


## deferred 对象，让异步程序有了链式写法

* 写法一：
> 优势：更加原生
```
var wait = function(dtd){
var dtd = $.Deferred(); //在函数内部，新建一个Deferred对象
　　　　var tasks = function(){
　　　　　　alert("执行完毕！");
　　　　　　dtd.resolve(); // 改变Deferred对象的执行状态
　　　　};

　　　　setTimeout(tasks,5000);
　　　　return dtd.promise(); // 返回promise对象
　　};
$.when(wait())
　　.done(function(){ alert("哈哈，成功了！"); })
　　.fail(function(){ alert("出错啦！"); });
```
## 写法二：
> 优势：更加简单
```
function wait(dtd) {　　　　
  var tasks = function() {　　　　　　
    alert("执行完毕！");　　　　　　
    dtd.resolve(); // 改变Deferred对象的执行状态
  };
  setTimeout(tasks, 3000);
};　　
$.Deferred(wait)
  .done(function() {
    alert("哈哈，成功了！");
  })
  .fail(function() {
    alert("出错啦！");
  });
```
## 写法三：
> 优势：用promise方法部署deferred对象，让程序更加顺畅
```
// 部署开始
var dtd = $.Deferred(); // 生成Deferred对象
　　var wait = function(dtd){
　　　　var tasks = function(){
　　　　　　alert("执行完毕！");
　　　　　　dtd.resolve(); // 改变Deferred对象的执行状态
　　　　};
　　　　setTimeout(tasks,5000);
　　};
dtd.promise(wait);
// 部署结束
　　wait.done(function(){ alert("哈哈，成功了！"); })
　　.fail(function(){ alert("出错啦！"); });
　　wait(dtd);


```

