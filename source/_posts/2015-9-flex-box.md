---
title: css3 盒模型
date: 2015-09-08 00:22:05
tags: [css]
---

## 老属性
```
display: box;
display: -webkit-box;
-webkit-box-align: center(...);
-webkit-box-pack: center(...);
```

## 新属性
[Flex 布局教程：语法篇](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html?utm_source=tuicool)
```css
//父元素
display: flex;
flex-flow: row/column/nowrap/wrap // 简写flex-direction & flex-wrap
justify-content: flex-start/flex-end/center/space-between/space-around
align-items: flex-start/flex-end/center/stretch(不写高度或auto自动拉伸)/baseline
//子元素
flex: 1;
```
