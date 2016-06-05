---
title: Q 入门
date: 2016-05-05 14:10:53
tags: [javascript]
---

## Q.fcall
> 把普通函数return 转化为 promise
```javascript
function read(text,callback){
        return text
}

Q.fcall(read,1,function(text){
//
}).then(function(res){
console.log(res)
}).catch(function(err){
alert(err)
})
```
## Q.denodeify
> 把符合node回调规则的函数转化为promise
```javascript
function read(a,callback){
    callback(null,a)
  }


  var Qread = Q.denodeify(read);
  Qread(1).then(function(res){
    console.log(res)
  }).catch(function(err){
    alert(err)
  })

```

## Q.defer 方式
```javascript
function read(text){
  var defferObj = Q.defer();
  if(text === 1){
    defferObj.resolve('this argument is 1')
  }else{
    defferObj.reject('this argument is not 1')
  }
  return defferObj.promise;
}
read(1).then(function(res){
  console.log(res)
}).catch(function(err){
  alert(err)
})
```
## Q.promise
```javascript
// standard
Q.Promise(function(resolve, reject){
setTimeout(function(){
  resolve(1)
},1000)
}).then(function(text){
console.log(text)
}).catch(function(err){
alert(err)
})
```

## 实例

```javascript
function qFoo(text){
    return Q.promise(function read(resolve,reject){
        resolve(text*2)
    })
}

function qBar(text){
    return Q.promise(function read(resolve,reject){
        resolve(text*text)
    })
}

qFoo(2)
    .then(function(res){
        return qBar(res)
    })
    .then(function(res){
    console.log(res)
    })

```


## Q.all
```javascript
Q.all([
  Q.promise(function(resolve, reject) {
    setTimeout(function() {
      resolve();
    }, 1000)
  }),
  Q.promise(function(resolve, reject) {
    setTimeout(function() {
      resolve();
    }, 2000)
  })
]).then(function(res) {
  console.log('都完成了')
}).catch(function(err){
  alert(err)
})
```

## Q.allSettled
> all成功后返回数组

## Q.()
>包装别函数提供的promise类库
```javascript
Q($.ajax())
```
