---
title: vue.extend 实例化
date: 2016-06-03 15:24:02
tags: [vue]
---

## 直接生成模板  免去components注册组件这一步

```javascript
<div id="div1"></div>



var template = Vue.extend({
            template: '<span>{{attr}}</span>'
})

new template({
    el: "#div1",
    data: {
        attr: 123
    }
})

```