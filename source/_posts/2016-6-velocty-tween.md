---
title: velocity 与 Tween
date: 2016-06-02 15:25:18
tags: [velocity]
---

* 参考
>[CSS3动画那么强，requestAnimationFrame还有毛线用？](http://www.zhangxinxu.com/wordpress/2013/09/css3-animation-requestanimationframe-tween-%E5%8A%A8%E7%94%BB%E7%AE%97%E6%B3%95/)
[Velocity](http://julian.com/research/velocity/)
[Tween](https://github.com/galenjiang/Tween)

```
.dummy {
        position: absolute;
        width: 100px;
        height: 100px;
        border-radius: 50%;
        background-color: red;
    }

<div class="dummy" id="dummy1"></div>
```

```javascript

// 自定义缓动
Velocity.Easings.myCustomEasing = function(p, opts, tweenDelta) {
    // easeIn: function(t, b, c, d)  t 当前时间, b 初始值, c 差值, d 时间
    return Tween.Bounce.easeOut(p* opts.duration ,0,tweenDelta,1*opts.duration)/tweenDelta;
    // return Tween.Bounce.easeOut(p,0,tweenDelta,1)/tweenDelta;
};


document.querySelector('#dummy1').addEventListener('click',function(){
    Velocity(document.querySelector('#dummy1'), {
        top: '300px'
    }, {
        easing: 'myCustomEasing',
        duration: 600
    })
})
```