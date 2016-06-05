---
title: js 异步调用研究
date: 2015-09-08 00:04:47
tags: [javascript]
---
```
function A(fn){
    console.log("a");
    setTimeout(function(){
      fn();
    },1)
  }
  function B(){
    console.log("b");
  }
  (function C(){
    A(B);
    console.log("c");
  })()
```

* setTimeout  会对队列栈进行重拍。

下个例子，函数c用时很长，b在0.1秒后执行，然而b还是在c执行完之后再执行了
```
  function A(fn){
        console.log("a");
        setTimeout(function(){
          fn();
        },0.01)
      }
  function B(){
    console.log("b");
  }
  (function C(){
    A(B);
    // setTimeout(function(){
    for(var i = 0 ; i < 1000000000; i++){
      var j = i*i;
    }
      console.log("c");
    // },1)
  })()
  ```