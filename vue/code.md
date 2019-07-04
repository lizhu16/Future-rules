1.v-for

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


