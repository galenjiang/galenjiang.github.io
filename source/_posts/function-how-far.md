---
title: function how far
date: 2016-05-12T09:46:54.000Z
tags:
  - javascript
---

# 最原始的fastClick

```javascript
var oDiv = document.getElementById('div1'),
    fastClick = true;

function click() {

    setTimeout(function(){
        fastClick = true;
    },1000)
    console.log('点击了');

}

oDiv.addEventListener('click',function(){

    if(fastClick){
        fastClick = false;
        click();
    }

},false);
```

# 面向对象方式进行包装

```javascript
function $(el){

    var oEl = document.getElementById(el);
    this.fastClick = true;

}

$.prototype.add = function(type, callback){

    document.addEventListener(type, function(){

        if(this.fastClick){
            this.fastClick = false;
            callback();
            setTimeout(function(){
                this.fastClick = true;
            }.bind(this),1000)
        }

    }.bind(this),false);

}

function click(){

    console.log('点击了');

}


var oDiv1 = new $('div1');
oDiv1.add('click',click)
```

### 面向函数版

```javascript
var oDiv = document.getElementById('div1');

function delay(callback){

    var fastClick = true;
    return function(){

        if(fastClick){
            fastClick = false;
            callback();
            setTimeout(function(){
                fastClick = true;
            },1000)
        }

    }

}

function click(){

    console.log('点击了');

}

oDiv.addEventListener('click',delay(click),false);
```

### 如何扩展 Promise

```javascript

var oDiv = document.getElementById('div1');

function delay(callback){
    var status = 'resolve';
    return function(){
        if(status === 'pending'){
            return false;
        }else{
            status = 'pending'
            callback().then(function(){
                status = 'resolve'
            })
        }
    }
}

function click(msg){
    return new Promise(function(resolve, reject){
        console.log('刚点击消息还没回来')
        setTimeout(function(){
            console.log('消息：' + msg)
            resolve();
        },1000)
    })

}

oDiv.addEventListener('click',delay(click.bind(null,'hello')),false)

```


# 各种畅想~

```
underscore lodash Rxjs
```
