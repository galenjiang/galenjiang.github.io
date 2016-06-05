---
title: layout的妙用
date: 2016-06-05 14:05:47
tags: [html]
---

获取元素高度，触发layout，刷新classList，避免和后面**同时添加**的class一起刷新。

```javascript
element.classList.add('next');
// trigger layout
var x = element.clientHeight;
```

