---
title: 对象属性设置器
date: 2015-09-08 00:29:54
tags: [javascript]
---

## 定义对象，多属性 defineProperties

> 访问器属性 数据属性
```javascript
var book = {};
    Object.defineProperties(book, {
      _year: {
        value: 2004
      },
      edition: {
        value: 1,
        writable: true
      },
      year: {
        get: function() {
          return this._year;
        },
        set: function(newValue) {
          if (newValue > 2004) {
            this._year = newValue;
            this.edition += newValue - 2004;
          }
        }
      }
    });
    book.edition = 2;
    console.log(book.edition)
```
获取对象属性特性 ```getOwnPropertyDescriptor```
