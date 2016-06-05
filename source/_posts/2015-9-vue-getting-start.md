---
title: vue 入门
date: 2015-09-15 14:26:20
tags: [javascript,vue]
---

```
 v-bind:href 缩写
：href
v-on:click 缩写
@click

class指令
v-bind:class=""
对象语法
v-bind:class="json"
json = {'classA': true, 'classB':false }
v-bind:class="{ 'classA': isA, 'classB':isB  }"
data: {
isA: true,
isB: false
}
数组语法
v-bind:class="[ classA, classB ]"
data: {
classA: 'class-a',
classB: 'class-b'
}
v-bind:class="[classA, isB ? classB : '']"
isB: true

v-bind:style=""
对象语法
<divv-bind:style="{ color: activeColor, fontSize: fontSize + 'px' }"></div>
数组语法
<divv-bind:style="[styleObjectA, styleObjectB]">

组件
var mytemplate = Vue.extend({
  template: "<div class='div'></div>"
})
Vue.component("my-component", mytemplate);


父子组件

标准写法

var child = Vue.extend({
  template: "<div class='child'></div>"
})
var parent = Vue.extend({
  template: "<div class='parent'><child></child></div>",
  components: {
    "child": child
  }
})
Vue.component("parent", parent);

简单写法
Vue.component("parent", {
  template: "<div class='parent'><child></child></div>",
  components: {
    "child": {
      template: "<div class='child'></div>"
    }
  }
});

子组件用父组件的数据

var child = Vue.extend({
  props: ['a'],
  template: "<div class='child'>{{ a }}</div>",
  data: function(){
    return
    // {
    //   a: "child's data"
    // }
  }
})
var parent = Vue.extend({
  template: "<div class='parent'><child v-bind:a='a' ></child></div>",
  components: {
    "child": child
  },
  data: function(){
    return {
      a: "parent's data"
    }
  }
})

模板

      <!--  父组件-->
  <script type="x-template" id="parent">
    <div class='parent'>
      <child></child>
      <child></child>
    </div>
  </script>
  <!--  子组件-->
  <script type="x-template" id="child">
    <div class='child'>{{ a }}</div>
  </script>
定义
var child = Vue.extend({
  template: "#child",
  data: function(){
    return {
      a: "child's data"
    }
  }
})
var parent = Vue.extend({
  template: "#parent",
  components: {
    "child": child
  },
  data: function(){
    return {
      a: "parent's data"
    }
  }
})
// Vue.component("child", child)
Vue.component("parent", parent);

props 数据往子组件传递

props 为对象时，作为组件验证

$.on()  监听自定义事件
$.emit()触发，$.dispath() 向上冒泡  $.broadcast() 向下传递

过滤器  2.0废弃

{{ msg | filter }}
第一个字大写
capitalize
全部大写
uppercase
全部小写
lowercase
货币化
currency “￥”默认 $
复数
pluralize "item"
pluralize "st" "nd" "rd" "th"  再往后以最后面一个为准
源代码
json 4  缩进为4 default：2
延迟执行
debounce 500   default:300
@keyup="onKeyup | debounce 500"
限制循环
limitBy n m
n:限制几位 m:限制从m位开始，0为第一位
过滤
<input v-model="index" type="text" name="name" >
        <ul>
          <li v-for="item in msg | filterBy index in 'name' ">{{ item.name }} {{ item.age }} {{ item.sex }}</li>
        </ul>

多字段搜索
<liv-for="user in users | filterBy searchText in 'name' 'phone'"></li>

插值表达式
{{}}
{{*value}}只更新一次

增加v-cloak属性，防止闪烁
[v-cloak]{ display: none }
数据遍历之前 用v-show  防止显示不正常数据

v-for 在tr里面不正常



组件：

1. 一般定义
<div id="example">
<my-component></my-component>
</div>

// 定义
var MyComponent = Vue.extend({
  template: '<div>A custom component!</div>'
})

// 注册
Vue.component('my-component', MyComponent)

// 创建根实例
new Vue({
  el: '#example'
})
2.局部注册
var Child = Vue.extend({ /* ... */ })

var Parent = Vue.extend({
  template: '...',
  components: {
// <my-component> 只能用在父组件模板内
'my-component': Child
  }
})
3. 简化注册 注册语法糖
// 在一个步骤中扩展与注册
Vue.component('my-component', {
  template: '<div>A custom component!</div>'
})

// 局部注册也可以这么做
var Parent = Vue.extend({
  components: {
'my-component': {
      template: '<div>A custom component!</div>'
    }
  }
})

利用模板穿的属性来构造模板
Vue.component('child', {
// 声明 props
  props: ['msg'],
// prop 可以用在模板内
// 可以用 `this.msg` 设置
  template: '<span>{{ msg }}</span>'
})
props 驼峰写法如：myMsg  在模板外属性应该写成 my-msg

v-bind:my-msg="abc"  可以简写为：my-msg="abc
:my-msg="1" 数字1作为一个属性来传递的，用：my-msg

冒泡事件“child-msg” 父组件接受事件function(msg){}对参数进行处理

this.$dispatch('child-msg', this.msg)
获取子组件的方式:     在自组件上定义 v-ref属性    用$refs属性获取自组建
<div id="parent">
<user-profile v-ref:profile></user-profile>
</div>
var parent = new Vue({ el: '#parent' })
// 访问子组件
var child = parent.$refs.profile

第一个程序
<divid="app">
  {{ message }}
</div>
new Vue({
  el: '#app',
  data: {
    message: 'Hello Vue.js!'
  }
})
双向绑定 v-model
<divid="app">
<p>{{ message }}</p>
<inputv-model="message">
</div>
new Vue({
  el: '#app',
  data: {
    message: 'Hello Vue.js!'
  }
})

todo

<divid="app">
<ul>
<liv-for="todo in todos">
      {{ todo.text }}
</li>
</ul>
</div>
new Vue({
  el: '#app',
  data: {
    todos: [
      { text: 'Learn JavaScript' },
      { text: 'Learn Vue.js' },
      { text: 'Build Something Awesome' }
    ]
  }
})
综合案例
<div id="app">
      <input v-model="newtodo" v-on:keyup.enter="addtodo" type="text" name=""  >
      <ol>
        <li v-for="todo in todos">
          {{todo.text}}
          <button v-on:click="removetodo($index)" type="button" name="button">X</button>
        </li>
      </ol>
    </div>
    <script type="text/javascript">
      new Vue({
        el: "#app",
        data: {
          newtodo: "",
          todos: [
          ]
        },
        methods: {
          addtodo: function(){
            var text = this.newtodo.trim();
            if(text){
            this.todos.push({text: text});
            this.newtodo = "";
            }
          },
          removetodo: function(index){
            this.todos.splice(index,1);
          }
        }
      })
    </script>


插值表达式 {{}}  {{* msg }}单次不更新

指令 v-*

循环
v-for="item in items"
<div>{{ $index($key) }}: {{ item }}</div>

<div>
<spanv-for="n in 10">{{ n }} </span>
</div>

methods

计算属性
computed

v-model
双向绑定



```


