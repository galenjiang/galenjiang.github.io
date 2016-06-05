---
title: sass入门
date: 2015-09-05 14:21:00
tags: [sass]
---
## 选择器嵌套：
```css
a{
    color: red;
        header & {
        color: green;
        }
}
```
## 属性嵌套：
```css
.box{
    border: {
        top: 1px solid red;
        bottom: 1px solid green;
    }
}
```
## 伪类嵌套：
```css
.clearfix{
    &:after{
        content: "";
    }
}
```
## 简单混合宏
```css
@mixin display($type: flex){
    display: -webkit-$type;
    display: $type;
}
//引用
div{
    @include display(flex);
}
```
## 不定参宏
```css
@mixin box-shadow($shadows...){
  @if length($shadows) >= 1 {
    -webkit-box-shadow: $shadows;
    box-shadow: $shadows;
  } @else {
    $shadows: 0 0 2px rgba(#000,.25);
    -webkit-box-shadow: $shadow;
    box-shadow: $shadow;
  }
}
```
## 继承
```
@extend
.btn1 {
    color: red;
}
.btn2{
    background: green;
}
```
## %占位符
不会被编译到css
```css
%mt5 {
  margin-top: 5px;
}
```
混合宏会造成代码冗余，但可以传参；继承能合并代码，但不能传参

## 插值表达式
只能用于@extend或者普通作用域中。（插入 ```.class``` 和 ```%placeholder```）
```css
$properties: (margin, padding);
@mixin set-value($side, $value) {
    @each $prop in $properties {
        #{$prop}-#{$side}: $value;
    }
}
.login-box {
    @include set-value(top, 14px);
}
```
举个栗子2
```css
%updated-status {
    margin-top: 20px;
    background: #F00;
}
.selected-status {
    font-weight: bold;
}
$flag: "status";
.navigation {
    @extend %updated-#{$flag};
    @extend .selected-#{$flag};
}
```

## @import
```css
@import "url"引用
```

