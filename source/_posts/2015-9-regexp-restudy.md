---
title: 重学正则
date: 2015-09-08 00:10:46
tags: [reg]
---

## 两种正则不同写法

* javascript写法reg = new RegExp("规则"，"选项")   用于字符串拼接

规则在new的时候特殊情况，需要转义
eg: new RegExp("\\d") 一个数字

* perl写法reg = /a/
选项：
+多个    \d 数字    \b边界    |或    ^行首    $行尾   -范围    \s空格
```
[\u4e00-\u9fa5] //中文
/^(0[1-9]\d{1,2}-)?[1-9]\d{6,7}$/ //电话
/^\w+@[a-z0-9\-]+(\.[a-z]{2,6}){1,2}$/i //邮箱
1[3578]\d{9} //手机
```
* 选项：
i(忽略大小写)    m(多行)    g(全局找)


## 用法
1. search
str.search(re) ;// 找到 返回index  没找到 返回 -1
2. match
str.match(re)  匹配 返回一个数组（符合正则）
3. replace
屏蔽关键字
eg1:    str = str.replace(/Chrome/g,function(s){
 var str = "";
 for(var i = 0; i < s.length; i++){
  str += "*";
 }
eg2:    document.write(str.replace(/a/g,function(s){
 return "+";
}));
document.write(str.replace(/a/g,"+"));等同于
4. test唯一特殊
reg.test(str)

## 应用
* trim函数 首尾去空格
```
function trim(str){
 return str.replace(/^\s+|\s+$/g,"");
}
```
* class取dom
```
function getByClass(oParent,sClass){

 if(oParent.getElementsByClassName){
  return oParent.getElementsByClassName(sClass);
 }

 var result = [];

 var re = new RegExp("\\b" + sClass + "\\b");
 var aEle = oParent.getElementsByTagName("*");
 for(var i = 0; i < aEle.length; i++){

  if(re.test(aEle[i].className)){
   result.push(aEle[i]);
  }
 }

 return result;
}
```