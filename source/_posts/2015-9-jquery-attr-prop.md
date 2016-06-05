---
title: jquery中attr和prop的区别分析
date: 2015-09-08 00:14:44
tags: [javascript, jquery]
---


在高版本的```jquery```引入```prop```方法后，什么时候该用```prop```？什么时候用```attr```？它们两个之间有什么区别？这些问题就出现了。
关于它们两个的区别，网上的答案很多。这里谈谈我的心得，我的心得很简单：
• 对于HTML元素本身就带有的固有属性，在处理时，使用```prop```方法。

• 对于HTML元素我们自己自定义的DOM属性，在处理时，使用```attr```方法。
上面的描述也许有点模糊，举几个例子就知道了。
复制代码代码如下:

```javascript
<a href="http://www.baidu.com" target="_self" class="btn">百度</a>
```


 这个例子里```<a>```元素的DOM属性有```href```、```target```和```class```，这些属性就是```<a>```元素本身就带有的属性，也是W3C标准里就包含有这几个属性，或者说在IDE里能够智能提示出的属性，这些就叫做固有属性。处理这些属性时，建议使用```prop```方法。
复制代码代码如下:

```
<a href="#" id="link1" action="delete">删除</a>
```
这个例子里```<a>```元素的DOM属性有```href```、```id```和```action```，很明显，前两个是固有属性，而后面一个```action```属性是我们自己自定义上去的，```<a>```元素本身是没有这个属性的。这种就是自定义的DOM属性。处理这些属性时，建议使用```attr```方法。使用```prop```方法取值和设置属性值时，都会返回```undefined```值。
再举一个例子：

复制代码代码如下:

```
<input id="chk1" type="checkbox" />是否可见 <input id="chk2" type="checkbox" checked="checked" />
```
是否可见
像```<checkbox>```，```<radio>```和```<select>```这样的元素，选中属性对应```checked```和```selected```，这些也属于固有属性，因此需要使用```prop```方法去操作才能获得正确的结果。
复制代码代码如下:
```
$("#chk1").prop("checked") == false $("#chk2").prop("checked") == true
```
如果上面使用```attr```方法，则会出现：
复制代码代码如下:
```
$("#chk1").attr("checked") == undefined
$("#chk2").attr("checked") == "checked"
```
全文完。
