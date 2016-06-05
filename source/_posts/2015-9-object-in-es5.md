---
title: es5中的object对象
date: 2015-09-13 14:29:12
tags: [javascript]
---
[全面理解面向对象的 JavaScript](http://blog.jobbole.com/38614/)
[ECMAScript 5.1简介](http://www.zhangxinxu.com/wordpress/2012/01/introducing-ecmascript-5-1/)


对象属性的操作和获取


返回对象obj的名为propName的自身属性(非继承来的)的属性描述符.如果没有这个自身属性,则返回undefined.
```
Object.getOwnPropertyDescriptor(obj, propName)
```
获取原型
```
Object.getPrototypeOf(obj)
```
是否有属性
```
obj.hasOwnProperty("string")
```
for,keys受枚举属性影响不可被枚举
```
for (var x in obj)
Object.keys(obj)
```
获取所有自有属性，不受枚举影响
```
Object.getOwnPropertyNames()
```
操作自有属性
```
Object.defineProperty(obj, propName, desc)
```