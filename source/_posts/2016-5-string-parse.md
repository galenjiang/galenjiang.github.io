---
title: 字符串的转义
date: 2016-06-05 15:28:29
tags: [javascript]
---
## 字符串的转义

sad字段的值是对象。
```
var str1 = '{"asd":"123","sad":{\"ert\":123213}}';
JSON.parse(str1)
```
```
sad字段的值是字符串。（有趣的部分）
var str2 = '{"asd":"123","sad":"{\\"ert\\":123213}"}';
JSON.parse(str2) //sad为字符串，如何处理""部分
```
> 最外层str1字符串先处理一次
> sad字段的值表示的字符串再经过处理。

```
var reg = new RegExp("\\d")
```

> 同样做```\\d```作为字符串来先进行转义为```\d```。