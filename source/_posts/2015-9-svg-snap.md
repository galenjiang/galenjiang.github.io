---
title: svg SNAP框架
date: 2015-09-08 00:23:02
tags: [svg]
---

# 深入学习Snap
----
    var svg = Snap("#el")
> 大写 绝对路径
> 小写 相对路径

### paper 属性

    var paper = svg.paper

* el 方法


    paper.el("type", {props...})


* g&group 方法


    paper.g(el1, el2)
    paper.g().add(el1, el2)
    paper.group()

* el 方法


    paper.circle(cx, cy, r)

* ellipse 方法


    paper.ellipse(cx, cy, rx, ry)


* filter 方法


    var gs = paper.filter ('<feGaussianBlur stdDeviation="2"/>')

    el.attr({filter: gs})


* gradient 方法


    var g1 = svg.paper.gradient("l(0, 0, 1, 1)#000-#f00:25-#fff");
    svg.paper.circle(50, 50, 40).attr({fill: g1});

> 绝对路径


    svg.paper.gradient("L(0, 0, 1, 1)#000-#f00:25-#fff");


> 编译为
> ![1450755763709.jpg][0]


> 辐射


    svg.paper.gradient("r(0, 0, 1, 1)#000-#f00:25-#fff");

* image 方法


    paper.image("src", x, y, width, height)

* line 方法


    paper.line(x, y, x, y)

* path 方法


    paper.path(M50 50 L100 50)

* polyline&polygon 方法


    paper.polyline(x1, y1, x2, y2)

    paper.polyline([ x1, y1, x2, y2 ])

     paper.polygon(x1, y1, x2, y2)

    paper.polygon([ x1, y1, x2, y2 ])

* rect 方法


    paper.rect(x1, y1, x2, y2, rx, ry)

* text方法


    paper.text(x, y, "text")

    paper.text(x, y, ["t"],["e"],["x"],["t"])

* toString 方法


    paper.toString()

### element 属性

****

* 选取元素


    el.select()

    el.selectAll()

    el.parent()



* 操作DOM


    el.clone()

    el1.after(el2) el2 排在el1后面

    el1.before(el2) el2 排在el1前面

    el1.append(el2) el2 插到el1里面最后面

    el1.prepend(el2) el2 插到里面最前面

    el.remove()

    el.toDefs()

    Snap.parse(string)字符串转化为svg对象，可供append

    el.data()

    el.removeData()

    el.toString() 转变为字符串

    el.transform() 转变为对象



* 标签


    el.use() 创建use标签，链接到对象

    el.pattern()

    el.marker(viewBoxX1, viewBoxY1, viewBoxX2, viewBoxY2,refX,refY )

* 获取属性


    el.adPX(attr)已px值返回属性值

    el.attr({})

    el.getBBox()返回元素边界框描述

* 高级操作


    el.getPointAtLength(lenght) 返回截取长度的点坐标

    el.getSubpath(start, end) 返回截取的子路径

    el.getTotalLength()返回元素的长度

* 事件

> click dbclick hover mousedown mousemove mouseout mouseover
> mouseup mousemove
> touchcancel touchend touchmove touchstart
> unclick undbclick undrag unhover unmousedown unmousemove
> unmouseout unmouseover unmouseup untouchcancel untouchend untouchmove untouchstart

### fragment 属性

### set 属性


    var set = svg.select("circle")


    set.clear()

    set.exclude(el)

    set.forEach(function(element, index){})

    set.push()

    set.pop()

    set.splice()

### Snap 属性


    var svg = Snap(x, y)

    new Snap.Matrix()

    Snap.ajax()

    Snap.load()

    Snap.angle(x1, y1, x2, y2)2个点，和3个点。没有懂

    Snap.rad(deg) 角度转换为弧度




* 颜色


    Snap.color("#123456")

    Snap.getRGB("red")

    Snap.rgb(255, 255, 255)

    Snap.hsb()

    Snap.hsb2rgb()

    Snap.rgb2hsb()

    Snap.hsl()

    Snap.hsl2rgb()

    Snap.rgb2hsl()

    Snap.deg(Math.PI)

* 滤镜


    方法1：

    svg.paper.filter(Snap.filter.blur())

    方法2：

    svg.paper.filter('<feGaussianBlur stdDeviation="2"/>')


> 滤镜种类：

    blur brightness constrast grayscale bueRotate?? invert saturate sepia shadow

* 根据字符串创建svg


    Snap.format() 模板拼接字符串

    Snap.fragment() 字符串生成svg

    Snap.parsePathString("M10 10")路径字符串转变为路径数组

    Snap.parseTransformString(TString)变换字符串转变为数组

* 获取元素


    Snap.getElementByPoint()根据坐标来获取元素

* 判断类型


    snap.is(??, type)


# Snap.path 属性

* bezierBBox方法


    返回贝塞尔曲线盒子 {width: ??, height: ??, x: ??, y: ??, x2: ??, y2: ??}
    path.bezierBBox(x1, y1, x2, y2, x3, y3, x4, y4)

* findDotsAtSegment 方法


    返回贝塞尔曲线参数位置点坐标  参数：0 < t < 1  返回t位置的点坐标
    Snap.path.findDotsAtSegment(p1x, p1y, c1x, c1y, c2x, c2y, p2x, p2y, t)


* Snap.path.getBBox 方法


    返回边界盒子：高度，宽度，开始一点，最后一点的坐标
    Snap.path.getBBox("M10,10L90,90");

* getPointAtLength 方法


    同findDotsAtSegment
    Snap.path.getPointAtLength(path, length)


* getSubpath 方法


    返回子路径字符串    path为路径字符串 from to 为像素长度
    Snap.path.getSubpath(path, from, to)


* getTotalLength 方法

    返回路径长度
    Snap.path.getTotalLength(path)


* intersection 方法


    判断两条路径是否交叉 返回坐标点参数 x y 坐标  t1 t2百分比
    Snap.path.intersection(path1, path2)


* isBBoxIntersect 方法


    判断盒子相交返回true
    Snap.path.isBBoxIntersect(bbox1, bbox2)


* isPointInsideBBox 方法


    给定点是否在盒子内部
    Snap.path.isPointInsideBBox(bbox, x, y)


* map 方法


    返回路径matrix变换后的路径字符串
    var path = 'M10,10L90,90', matrix = new Snap.Matrix(1,0,0,1,10,10);
    var pathTransform = Snap.path.map(path, matrix);
    if (window.console) {
        console.log(pathTransform);    // 结果是：[Array[3], Array[7], toString: function]
        console.log(pathTransform.toString());    // 结果是：M20,20C20,20,100,100,100,100
    }


* toAbsolute 方法


    转换路径坐标为绝对值
    var path = "M10,10L90,90";
    var absolute = Snap.path.toAbsolute(path);
    console.log(absolute);    // [Array[3], Array[3], toString: function]
    console.log(absolute.toString());    // "M10,10L90,90"

* toAbsolute 方法


    转化路径为贝塞尔曲线字符串，绝对路径？！
    var pathString = "m32,118c0,0 21,-100 78,-94c57,6 -78,94 -78,94z";
    var cubic = Snap.path.toCubic(pathString);
    console.log(cubic.toString());
    // 结果是：
    // M32,118C32,118,53,18,110,24C167,30,32
    18,32,118C32,118,32,118,32,118

* toRelative 方法


    转换路径坐标为相对路径
    var path = "M10,10L90,90";
    var relative = Snap.path.toRelative(path);
    console.log(relative);    // Array[2]
    console.log(relative.toString());    "M10,10l80,80"

* plugin 方法


    扩展插件
    Snap.plugin(function (Snap, Element, Paper, global) {
        Snap.newmethod = function () {};
        Element.prototype.newmethod = function () {};
        Paper.prototype.newmethod = function () {};
    });

* select 方法


    Snap.select(query)
    同 Snap("#svg").select(query)



* selectAll 方法


    Snap.selectAll(query)
    同 Snap("#svg").selectAll(query)

* snapTo 方法


    逐帧 一帧跳一帧
    Snap.snapTo(values, value, [tolerance])


### 动画



    方法1：Snap.animate(0, 20, function (val) {
                rect.attr({
                    x: val
                });
            }, 1000);

    方法2：rect.animate({x: 20}, 1000);


* 停止


    el.animate({},time, effect, function(){})

    el.stop()

### mina

    mina(a, A, b, B, get, set, [easing])

    var c = Snap("#svg").paper.circle(50,50,40).attr({ fill: "red" });
    document.getElementById("button").onclick = function() {
    var now = mina.time();
    var ani = mina(50, 150, now, now + 1000, mina.time, function(val) {
        c.attr({
            cx: val
        });
    }, mina.easeout);
    console.dir(ani);
};

* mina.time()
> 获取时间戳

* mina.backin(n)

* mina.backout(n)

* mina.bounce(n)

* mina.easein(n)

* mina.easeinout(n)

* mina.easeout(n)

* mina.elastic(n)

* mina.linear(n)

> 动画效果

* mina.getById(id)



