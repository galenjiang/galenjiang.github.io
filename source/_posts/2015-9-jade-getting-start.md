---
title: jade 入门
date: 2015-09-08 00:20:58
tags: [node]
---


```
doctype
head
    meta(charset="utf-8")
    title jade study
body
    h2  文档声明和头尾标签
    h2  标签语法
    section
        div
            div
                ul
                p
    h2 元素标签
    #id.class1(class='class2')
    div#id.class1.class2
        a(href="http://imooc.com", target="_black") link
    h2 注释
    h3 单行注释
    //h3.title(id="title", class="title3") imooc
    h3 非缓冲注释
    //- #id.classname
    h3 块注释
    //-
        p
            a(href="#", data-uid="100")
            input(name="course", type="text", value="jade")
    h3 混排的大段文本(两种： 1.    | 竖线加空格，2. 标签后加点)
    p
        | 1.aa
        strong 11
        | 2.bb
        span 12
    style.
        body{color: #fff}
    script.
        var i = "abc";
    - var course = "jade"//变量，全局访问
    div #{course.toUpperCase()}
    - var data = "text"
    - var htmldata = "<script>xxxxx</script>"
    p #{data}
    p #{htmldata}  //  安全转义
    p !{htmldata}     // 非转义
    p= data   //等同P!{xxx}    非转义
    p \#{}  //输出本身
    p \!{}   //输出本身

    input (value=#{xxxx})   //没有值会输出undefined   ==>  写成input (value=xxxx)

遍历循环
    - for (var k in json)
        p= json[k]

    each value, key in json
        p #{key}: #{value}


嵌套循环
    - var sections = [{id:1, items: ["a", "b"]},{id:2, items: ["c", "d"]}]
    dl
        each section insections
            dt= section.id
            each item in section.items
                dd= item

    -var n = 0
    ul
        while n <4
            li= n++

    h3 if else
    h3 unless  和if倒着来
    h3 case

    case name
        when "java": p hi
        default "node": p hi node

mixin student
    p no content

mixin student(xxx)
    p xxxxxx


+mixin(xxx)

内联mixin
mixin()
    if block
        block
    else
        p no team


 +mixin()
    p content

extend ....

block

include


```


```
定义标签：

 #id.class1(class='class2')


1. 大段文字重排
行首加|（可以有选择性） 或标签后加.

2. 变量
定义
- var string = "hello world"

调用
p #{string}
p !{string}
p= string

混合调用
-var s ='world'
p hello #{s}
p='hello'+ s
3. if语句
- if (表达式)
    div1
- else
    div2

简写
if 表达式
    div1
else
    div2
enless 语句  和if语句反过来的

4. for each循环
- var arr = [1,2,3](适用于arr)
      - for (var i = 0; i < arr.length; i++){
        li #{arr[i]}
      - }
each val, index in arr  (省略-)（适用于json,arr）
        li hello #{val} #{index}

5. mixin 模块
- var json= {"taxi":　100,"bus": 10, "plane": 3000}
定义
mixin list(json)
    ul
        each val, index in json
            li #{index}#{json}

调用
+list(json)

外部传入模块
mixin div()
    div
        if block
            block
        else
            p    "这里没有东西"
+div
外部传入属性
mixin link(href, name)
      a(class!=attributes.class, href=href)=name

    +link('/foo', 'foo')(class="btn")

6. 外部包含模板
定义包含模板
includes/head.jade
head
  title 我的网站
  script(src='/javascripts/jquery.js')
  script(src='/javascripts/app.js')

引用包含模板
index.jade
doctype html
html
  include includes/head
body
  h1 我的网站
  p 欢迎来到我的网站。
  include includes/foot
7. 引用模板

定义引用模板
includes/head.jade
extends ../index
block head
head
  title 我的网站
  script(src='/javascripts/jquery.js')
  script(src='/javascripts/app.js')
引用引用模板
index.jade
doctype html
html
  block head
body
  h1 我的网站
  p 欢迎来到我的网站。
  include includes/foot


```



























