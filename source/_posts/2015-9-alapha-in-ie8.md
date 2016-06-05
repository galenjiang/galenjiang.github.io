---
title: 半透明背景  IE兼容 最佳实践
date: 2015-09-08 00:03:56
tags: [css]
---
[IE8下实现兼容rgba](http://segmentfault.com/a/1190000002485299)

```
sub{
    background: rgba(0,0,0,0);
    background: url("../../images/space.png") 0 0 repeat;
    &:hover{
      background: rgba(0,0,0,.3);
      filter: progid:DXImageTransform.Microsoft.gradient(startColorstr=#4c000000,endColorstr=#4c000000);
    }
```

元素内文字，加filter：alpha（opacity=0）opcity: 0 做兼容

