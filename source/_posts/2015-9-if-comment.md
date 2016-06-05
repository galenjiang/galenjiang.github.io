---
title: 条件注释
date: 2015-09-08 00:13:48
tags: [html]
---
```
<!--[if IE]>
<h1>您正在使用IE浏览器</h1>
<![endif]-->
<!--[if IE 5.5]>
<h1>版本 5.5</h1>
<![endif]-->
<!--[if IE 6]>
<h1>版本 6</h1>
<![endif]-->
<!--[if IE 7]>
<h1>版本 7</h1>
<![endif]-->
```
下面的代码是在非IE浏览器下运行的条件注释
```
<!--[if !IE]><!-->
<h1>您使用不是 Internet Explorer</h1>
<!--<![endif]-->
```
最终在非IE和特殊的IE浏览器下起作用
(或者使用 lte lt 或者 gt gte来判断，如：
```
<!--[if lte IE 6]>
在IE 6下显示的信息
<![endif]-->
).
<!--[if IE 6]><!-->
<h1>您正在使用Internet Explorer version 6<br />
或者 一个非IE 浏览器</h1>
<!--<![endif]-->
```
## 条件注释简介
1. IE中的条件注释（Conditional comments）对IE的版本和IE非IE有优秀的区分能力，是WEB设计中常用的hack方法。
2. 条件注释只能用于IE5以上。
3. 如果你安装了多个IE，条件注释将会以最高版本的IE为标准。
4. 条件注释的基本结构和HTML的注释(<!– –>)是一样的。因此IE以外的浏览器将会把它们看作是普通的注释而完全忽略它们。
5. IE将会根据if条件来判断是否如解析普通的页面内容一样解析条件注释里的内容。
## 条件注释属性
gt : greater than，选择条件版本以上版本，不包含条件版本
lt : less than，选择条件版本以下版本，不包含条件版本
gte : greater than or equal，选择条件版本以上版本，包含条件版本
lte : less than or equal，选择条件版本以下版本，包含条件版本
! : 选择条件版本以外所有版本，无论高低

1、Css if hack条件语法
```
< !--[if IE]> Only IE <![endif]-->
```
仅所有的WIN系统自带IE可识别
```
< !--[if IE 5.0]> Only IE 5.0 <![endif]-->
```
只有IE5.0可以识别
```
< !--[if gt IE 5.0]> Only IE 5.0+ <![endif]-->
```
IE5.0包换IE5.5都可以识别
```
< !--[if lt IE 6]> Only IE 6- <![endif]-->
```
仅IE6可识别
```
< !--[if gte IE 6]> Only IE 6/+ <![endif]-->
```
IE6以及IE6以下的IE5.x都可识别
```
<!--[if lte IE 7]> Only IE 7/- <![endif]-->
```
仅IE7可识别
```
< !--[if gte IE 7]> Only IE 7/+ <![endif]-->
```
IE7以及IE7以下的IE6、IE5.x都可识别
```
<!--[if IE 8]> Only IE 8/- <![endif]-->
```
仅IE8可识别
```
<!--[if IE 9]> Only IE 9/- <![endif]-->
```
仅IE9可识别

注：在 if  后加 lt gte有不同效果 （参加其它参数同理）
```
<!–[if IE 8]> = IE8 仅IE8可识别
<!–[if lt IE 8]> = IE7或更低版本
<!–[if gte IE 8]> = 高于或者等于IE8版本
```
下面的代码是在非IE浏览器下运行的条件注释
```
<!--[if !IE]><!-->
```
您使用不是 Internet Explorer
```
<!--<![endif]-->
<!--[if IE 6]><!-->
```
您正在使用Internet Explorer version 6或者 一个非IE 浏览器
```<!--<![endif]-->

    <!DOCTYPE html>
    <html>
    <head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <title>DIV IF条件实例</title>
    </head>
    <body>
    你正在使用：
    <!--[if IE 7]>
    <h2>IE7</h2>
    <![endif]-->
    <!--[if IE 6]>
    <h2>IE6</h2>
    <![endif]-->
    <!--[if IE 8]>
    <h2>IE8</h2>
    <![endif]-->

    <!--[if IE 9]>
    <h2>IE9</h2>
    <![endif]-->
    <br><br>
    <strong>说明</strong>：如果你的浏览器版本为多少即会显示IE多少，针对IE6-IE9实验</body>
    </html>
```