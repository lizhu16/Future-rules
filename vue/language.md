## 1.基于模块开发

+ 每一个 Vue 组件(等同于模块)首先必须专注于解决一个单一的问题，独立的, 可复用的, 微小的，保证组件可独立的运行

## 2.组件命名

**组件的命名需遵从以下原则：**
+ 有意义的: 不过于具体，也不过于抽象
+ 简短: 2 到 3 个单词
+ 具有可读性: 以便于沟通交流

>**原因：组件是通过组件名来调用的。所以组件名必须简短/富有含义并且具有可读性**

``` JavaScript
<!-- 推荐 -->
<app-header></app-header>
<user-list></user-list>
<range-slider></range-slider>

<!-- 避免 -->
<btn-group></btn-group> <!-- 虽然简短但是可读性差. 使用 `button-group` 替代 -->
<ui-slider></ui-slider> <!-- ui 前缀太过于宽泛，在这里意义不明确 -->
<slider></slider> <!-- 与自定义元素规范不兼容 -->
```

## 3.组件表达式简单化

**原因**:
+ 复杂的行内表达式难以阅读
+ 行内表达式不是通用的，可能会导致重复编码的问题
  
**推荐**

如果有太多复杂并难以阅读的行内表达式，那么可以使用 `method` 或是 `computed` 属性来替代其功能。


```html
<!-- 推荐 -->
<template>
  <h1>
    {{ normalizedFullName }}
  </h1>
</template>
<script>
  export default {
    computed: {
      normalizedFullName: function () {
        return this.fullName.split(' ').map(function (word) {
          return word[0].toUpperCase() + word.slice(1)
        }).join(' ')
      }
    }
  }
</script>
```

**不推荐**

![](example.png)

## 4.组件props原子化

虽然 Vue.js 支持传递复杂的 JavaScript 对象通过 props 属性，但是你应该尽可能的使用原始类型的数据。尽量只使用JavaScript 原始类型(字符串、数字、布尔值) 和 函数。尽量避免复杂的对象。

**原因**
+ 使得组件API清晰直观
+ 只使用原始类型和函数作为props使得组件的API更接近HTML(5)原生元素
+ 其他开发者更好的理解每一个prop的含义，作用
+ 传递过于复杂的对象是的我们不能够清除的知道哪些属性或方法被自定义组件使用，使得代码难以重构和维护

**推荐**

组件的每一个属性单独使用一个props, 并且使用函数或是原始类型的值

``` javascript
<!-- 推荐 -->
<range-slider
  :values="[10, 20]"
  min="0"
  max="100"
  step="5"
  :on-slide="updateInputs"
  :on-end="updateResults">
</range-slider>

<!-- 避免 -->
<range-slider :config="complexConfigObject"></range-slider>
```


## 5.验证组件的props

在 Vue.js 中，组件的 props 即 API，一个稳定并可预测的 API 会使得你的组件更容易被其他开发者使用。组件 props 通过自定义标签的属性来传递。属性的值可以是 Vue.js 字符串(:attr="value" 或 v-bind:attr="value")或是不传。你需要保证组件的 props 能应对不同的情况。

**原因**

验证组件 props 可以保证你的组件永远是可用的(防御性编程)。即使其他开发者并未按照你预想的方法使用时也不会出错。

**推荐**
+ 提供默认值
+ 使用type属性校验类型
+ 使用props之前先检查该props是否存在
``` javascript
<template>
  <input type="range" v-model="value" :max="max" :min="min">
</template>
<script>
  export default {
    props: {
      max: {
        type: Number, // 这里添加了数字类型的校验
        default() { return 10 },
      },
      min: {
        type: Number,
        default() { return 0 },
      },
      value: {
        type: Number,
        default() { return 4 },
      }
    }
  };
</script>
```

## 6.组件结构化

按照一定的结构组织，使得组件便于理解。

**原因**

+ 导出一个清晰、组织有序的组件，使得代码易于阅读和理解。同时也便于标准化。
+ 按首字母排序属性，data, computed, watches 和 methods 使得属性便于查找


**推荐**
``` javascript
<template>
    <div class="Ranger__Wrapper">
        <!-- ... -->
    </div>
</template>

<script>
  export default {
    // 不要忘记了 name 属性
    name: 'RangeSlider',
    // 组合其它组件
    extends: {},
    // 组件属性、变量
    props: {
      bar: {}, // 按字母顺序
      foo: {},
      fooBar: {}
    },
    // 变量
    data() {},
    computed: {},
    // 使用其它组件
    components: {},
    // 方法
    watch: {},
    methods: {},
    // 生命周期函数
    beforeCreate() {},
    mounted() {}
};
</script>

<style scoped>
  .Ranger__Wrapper { /* ... */ }
</style>
```

## 7.组件事件命名

+ 事件命名采用驼峰命名
+ 一个事件的名字对应组件外的一组意义操作，如：change，upload

## 8.组件内样式添加作用域空间

Vue.js 的组件是自定义元素，这非常适合用来作为样式的根作用域空间。可以将组件名作为 css 类的命名空间。

**原因**

+ 给样式加上作用域空间可以避免组件样式影响外部的样式

**推荐**

给style标签加上 scoped 属性。加上 scoped 属性编译后会给组件的 class 自动加上唯一的前缀从而避免样式的冲突。