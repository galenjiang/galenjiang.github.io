---
title: line-height&vertical
date: 2016-05-11 15:02:41
tags: css
---
## line-height
[w3c标准](http://devdocs.io/css/line-height)

1. line-height确定line-box的高度
2. 同一行内，各line元素的line-height共同确定该行的line-boxes的高度
3. block元素没有定高度，由block元素内的block元素和inline元素共同确定该元素的高度。
```javascript
<div style="line-height:1.5; border:1px solid #34538b;font-size: 16px;">
    <span style="font-size:60px; border:1px solid #a0b3d6; vertical-align: baseline; line-height: 100px;">大大的文字</span>
    后面是静止的文字。
</div>
```

## vertical-align
[w3c标准](http://devdocs.io/css/vertical-align)

```vertical-align``` ```bottom```和```top``` 从标准看焉语不详，个人感觉是整个内部其他```vertical-algin```对齐方式先根据自己的基础对齐后，确定```entire line``` ```top```和```bottom```后再做两个对齐/或者说是取出这两个对齐方式中最高的元素，先把这个元素与```entire line```做对齐，之后再短的接上对齐。

## vertical-algin & line-height
[w3c标准](http://www.zhangxinxu.com/wordpress/2015/08/css-deep-understand-vertical-align-and-line-height/)
