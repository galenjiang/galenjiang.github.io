---
title: webpack配置 注意点
date: 2015-09-08 00:11:39
tags: [webpack]
---
* 获取绝对路径
```
path.resolve(__dirname, "js") 拼接字符串
```
* 同步获取文件夹下文件
```
fs.readdirSync(dirs) 返回数组
```

* 不加g,返回数组，一个为匹配值，后面为子正则（括号内）的匹配项
```str.match(/正则/)```
```/(.+)\.js$/```


* 安装plugin
```npm install commons-chunk-plugin –save-dev```
