---
title: gulp高级指南
date: 2015-09-08 00:34:02
tags: [gulp]
---
[参考网址](https://github.com/nimojs/gulp-book/blob/master/chapter7.md)

传统检测由于侦测到更改所有文件都进行编译，导致性能问题低下，策略改为根据变动路径更改相关文件

```javascript
gulp-watch-path

var watchPath =require('gulp-watch-path')

gulp.task('watchjs', function () {
    gulp.watch('src/js/**/*.js', function (event) {
        var paths = watchPath(event, 'src/', 'dist/')
        /*        paths            { srcPath: 'src/js/log.js',              srcDir: 'src/js/',              distPath: 'dist/js/log.js',              distDir: 'dist/js/',              srcFilename: 'log.js',              distFilename: 'log.js' }        */
        gutil.log(gutil.colors.green(event.type) +''+ paths.srcPath)
        gutil.log('Dist '+ paths.distPath)

        gulp.src(paths.srcPath)
            .pipe(uglify())
            .pipe(gulp.dest(paths.distDir))
    })
})

gulp.task('default', ['watchjs'])
```

编辑文件时，如果文件中有语法错误时，```gulp``` 会终止运行并报错。
```javascript
stream-combiner2

var combined = combiner.obj([
            gulp.src(paths.srcPath),
            uglify(),
            gulp.dest(paths.distDir)
        ])
combined.on('error', handleError)
// 代替
gulp.src(paths.srcPath)
.pipe(uglify())
.pipe(gulp.dest(paths.distDir))

```

压缩后的代码不存在换行符和空白符，导致出错后很难调试，好在我们可以使用 sourcemap 帮助调试
```javascript
var sourcemaps =require('gulp-sourcemaps')
// ...var combined = combiner.obj([
    gulp.src(paths.srcPath),
    sourcemaps.init(),
    uglify(),
    sourcemaps.write('./'),
    gulp.dest(paths.distDir)
])
// ...
```

