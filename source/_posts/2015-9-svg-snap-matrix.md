---
title: svg matrix
date: 2015-09-08 00:24:11
tags: [svg]
---
# Matrix
*[引用：张鑫旭Snap.svg Matrix方法](http://www.zhangxinxu.com/GitHub/demo-Snap.svg/demo/basic/Matrix.add.php)*
 ```javascript
eg:
var svg = Snap("#svg");
// 画个圈圈
var c = svg.paper.circle(50, 50, 40);
// 当前矩阵
var m1 = new Snap.Matrix(1,0,0,1,20,20);
// 圈圈应用矩阵变换 - 位移(20, 20)
c.transform(m1.toTransformString());

// 事件
if (document.addEventListener) {
document.querySelector("#button").addEventListener("click", function() {
    // 矩阵组合
    m1.add(1,0,0,1,-20,-20);
    // 圈圈再次应用矩阵变换 - 位移(-20, -20)
    c.transform(m1.toTransformString());
});
}
```

> 矩阵定义
```
var matrix = new Snap.Matrix(1,0,0,1,20,20)
```
> 矩阵用法
```
el.transform(matrix.toTransformString())
```

> 矩阵加法
```
matrix.add()
```
> 矩阵克隆
```
var m2 = matrix.clone()
```
>  矩阵反转
```
matrix.invert()
```
> 矩阵旋转
```
matrix.rotate(value, refX, refY)
```
> 矩阵旋转
```
matrix.scale(x, y)
```
> 矩阵平移
```
matrix.translate(x, y)
```
> 返回矩阵变化后的给定点的x坐标
```
matrix.x(x, y)
```
> 返回矩阵变化后的给定点的y坐标
```
matrix.y(x, y)
```
> 分割矩阵为基本变换
```
console.log(matrix.split())
```












