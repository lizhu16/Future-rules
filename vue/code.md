## 1.v-for

在执行v-for遍历的时候，总是应该带上key值使更新DOM时渲染效率更高。

**示例**

``` HTML
// 反例
<ul>
    <li v-for="item in list">
        {{ item.title }}
    </li>
</ul>

// 正例
<ul>
  <li v-for="item in list" :key="item.id">
    {{ item.title }}
  </li>
</ul>
```


v-for 应该避免与 v-if 在同一个元素（例如：`<li>`）上使用，因为 v-for 的优先级比 v-if 更高，为了避免无效计算和渲染，应该尽量将 v-if 放到容器的父元素之上。

**示例**

``` HTML
// 反例
<ul>
    <li v-for="item in list" :key="item.id" v-if="showList">
        {{ item.title }}
    </li>
</ul>

// 正例
<ul v-if="showList">
    <li v-for="item in list" :key="item.id">
        {{ item.title }}
    </li>
</ul>
```

## 2.路由

**路由跳转**

+ 通过`route-link`进行跳转

``` HTML
<template>
  <header class="header">
    <router-link id="logo" to="/home/first">{{logo}}</router-link>
    <ul class="nav">
      <li v-for="nav in navs">
        <router-link :to="nav.method">{{nav.title}}</router-link>
      </li>
    </ul>
</template>
```
+ 通过编程导航进行路由跳转
  
实际情况下，有很多按钮在执行跳转之前，还会执行一系列方法，这时可以用 this.$router.push(location) 来修改 url，完成跳转。

``` HTML
<div>
  <button class="register">注册</button>
  <button class="sign" @click="goFirst">登录</button>
</div>
```

``` javascript
methods: {
  goFirst() {
    this.$router.push({path: 'home/first'})
  }
}
```

**路由传参**

+ params
  
    请求参数不会体现在地址栏中
    
+ query
    
    请求参数会体现在地址栏中

能够使用动态路由的尽量通过路由配置使用动态路由，做到路由参数的简洁明了

>**注意: params如果没有在路由中定义参数，也是可以传过去的，同时也能接收到，但是一旦刷新页面，这个参数就不存在了。**

