# vue基础

官方文档：https://cn.vuejs.org/v2/guide/

## helloworld
引入：
```
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
```
html：
```
<div id="app">
  {{ message }}
</div>
```

js：
```
var app = new Vue({
  el: '#app',
  data: {
    message: 'Hello Vue!'
  }
})
```

## el
创建vue实例指定的el是挂载点，写法与css选择器完全相同。一般使用id选择器。
挂载点不能是body和html标签。

## data
创建vue实例指定的data数据对象，可以在html中直接取值，如果用js修改了数据，页面也会随之修改。
data可以是各种数据类型，字符串、数组、json等均可。

## v-text
可以在vue实例作用范围内的标签指定`v-text`属性，或者在文本节点写``{{ }}``，vue就会自动用data中的变量为其赋值。
v-text可以写变量、字符串拼接等各种表达式，有返回值即可。

## v-html
与v-text类似，但v-text会把html代码原封不动的展示出来，而v-html会解析html代码。

## v-show
写布尔表达式，为true时删除style中的`display: none`属性，将标签显示出来。否则添加`display: none`

## v-if
写布尔表达式，为真时标签才会显示出来。
与v-show的差别在于，v-if的值为false时，会删除标签，为true会添加标签。
v-id修改dom，v-show修改行内css。
对于需要频繁切换显示状态的应用，应该使用v-show，这样对性能的影响较小。
对于只需要修改一次显示状态的应用，可以写v-if，使代码更简洁。

## v-on
v-on用于绑定事件
```
<div v-on:click="方法()"></div>
<div v-on:mouseenter="方法()"></div>
<div v-on:dbclick="方法()"></div>
```
`v-on:`也可以替换为`@`
```
<div @click="方法()"></div>
<div @mouseenter="方法()"></div>
<div @dbclick="方法()"></div>
```
绑定的方法，必须在vue实例的methods中指定，例如：
```
new Vue({
  el: '#app',
  methods: {
      fun1: function() {
        // ...
      }
  }
})
```

## v-bind
用于定义标签的属性，例如：
```
<img v-bind:src="imgSrc"></img>
```
这样，vue就会把data中的imgSrc解析到标签的src属性中去。
以上的写法也可以简写成：
```
<img :src="imgSrc"></img>
```

`class`也是可以用v-bind解析的：
```
<div :class="{active: isActive}"></div>
```
这表示，是否有active属性，取决于data中isActive的真假。

## v-for
用于从数组中取值。
带有v-for的标签会根据数组的长度重复多次，如果为空则不显示。
```
<select id="filter-selector">
    <option value="0" selected>全部应用程序</option>
    <option v-for="option in options" :value="option.appId">{{ option.appName }}</option>
</select>
```
`v-for`还有一种写法，可以在遍历时得到索引
```
<option v-for="(option, index) in options" :value="option.appId">{{ index + 1 }} {{ option.appName }}</option>
```


## v-modal
用于实现表单元素`value`属性的双向绑定，修改变量的同时表单值会被修改，修改表单值的同时变量值也会被修改。

## 表单取值
v-modal绑定的表单标签，可以直接用变量取值。
有时候表单是不需要双向绑定的，取值可以用下面的方式实现：
```
<input type="text" ref="aim_page_input" :value="navigation.current_page">
<button @click="search($refs.aim_page_input.value)">跳转</button>
```
ref的命名要遵循变量命名规则，否则无法取值，与id的命名规则略有不同。

## 避免vue没加载出来时显示占位符
可以在**行内**css中写`display=none`，然后用v-show属性修改显示状态，这样vue没加载出来时，占位符不会显示在页面上。

## 补充
在IDEA中，安装Vue.js插件，写代码时会有语法提示。

# Reference
https://www.bilibili.com/video/BV12J411m7MG?t=295&p=17