---
title: gulp使用指南
date: 2015-09-25 14:27:39
tags: [node, gulp]
---
[gulp 入门指南](https://github.com/nimojs/gulp-book)
node.js环境下：
```
npm install -g gulp  //全局安装
```
```
npm install —-save-dev gulp  //本地安装
```
```
gulp  --save-dev //--save保存至package.json -dev 部署到开发环境，不加入生产环境
```
```
npm install gulp-uglify   //本地安装uglify
```
* 压缩js  gulp-uglify  示例
```
var gulp = require("gulp");
var uglify = require("gulp-uglify");
```
* 手动执行压缩任务
```
gulp.task("script",function(){
  //1. 找到文件
  gulp.src("js/*.js")
      .pipe(uglify())
      .pipe(gulp.dest("dist/js"));
});
gulp.task("auto",function(){
```
* 监听文件修改，当文件被修改时执行操作
```
  gulp.watch("js/*.js",["script"]);
})
gulp.task("default",["script","auto"])
```
```
cmd
gulp //回车执行。
```


sass模块
```
npm install gulp-ruby-sass
```
* 获取 gulp
```
var gulp =require('gulp')
```
* 获取 gulp-ruby-sass 模块
```
var sass = require('gulp-ruby-sass');
```

* 编译sass// 在命令行输入 gulp sass 启动此任务
```
gulp.task('sass', function() {
    return sass('sass/')
    .on('error', function (err) {
      console.error('Error!', err.message);
   })
    .pipe(gulp.dest('dist/css'))
});
```

* 在命令行使用 gulp auto 启动此任务
```
gulp.task('auto', function () {
    // 监听文件修改，当文件被修改则执行 images 任务
    gulp.watch('sass/**/*.scss', ['sass'])
});
```
* 使用 gulp.task('default') 定义默认任务// 在命令行使用 gulp 启动 sass 任务和 auto 任务
```
gulp.task('default', ['sass', 'auto'])
```


