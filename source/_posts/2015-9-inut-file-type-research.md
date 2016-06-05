---
title: input  file类型研究
date: 2015-09-08 00:01:04
tags: [javascript]
---

```<input id="file"type="file" name="file"/>```

属性值有以下几个比较常用：
* accept：表示可以选择的文件MIME类型，多个MIME类型用英文逗号分开，常用的MIME类型见下表。
* multiple：是否可以选择多个文件，多个文件时其value值为第一个文件的虚拟路径。
```<input id="file"type="file" name="file"/>```


选取元素var file =  document.getElementById("file")
元素内容var content = file.files   数组
事件变化file.onchange = function(){}



* 图片预览
```
<body>
<form class="" action="index.html" method="post" id="form">
  <input type="file" name="name" value="" id="file">
  <input type="submit" name="name" value="提交">
  <button type="button" name="button" id="btn2">获取对象</button>
</form>
<div class="" id="div">

</div>
</body>
<script type="text/javascript">
window.onload = function(){
  var file = document.getElementById("file");
  var btn2 = document.getElementById("btn2");
  var form = document.getElementById("form");
  var div = document.getElementById("div");
  btn2.onclick = function(){
    console.log(window.URL.createObjectURL(file.files[0]));
    var img = new Image();
    img.src = window.URL.createObjectURL(file.files[0]);
    div.appendChild(img);
  }
}
</script>
```