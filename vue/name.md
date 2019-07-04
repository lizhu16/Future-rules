## 命名规范

****
### 1.单文件组件文件的大小写

单文件组件的文件名始终是单词大写开头 (PascalCase)。

**原因**

单词大写开头对于代码编辑器的自动补全最为友好，因为这使得我们在 JS(X) 和模板中引用组件的方式尽可能的一致。

**不推荐**
> <div>components/</div>
> <div>|- mycomponent.vue</div>
-or
> <div>components/</div>
> <div>|- myComponent.vue</div>

**推荐**
> <div>components/</div>
> <div>|- MyComponent.vue</div>


****
### 2.紧密耦合的组件名

和父组件紧密耦合的子组件应该以父组件名作为前缀命名。

如果一个组件只在某个父组件的场景下有意义，这层关系应该体现在其名字上。因为编辑器通常会按字母顺序组织文件，所以这样做可以把相关联的文件排在一起。

**详细解释**

你可以试着通过在其父组件命名的目录中嵌套子组件以解决这个问题。比如：
> <div>components/</div>
> <div>|- TodoList/</div>
> <div style="text-indent:2em;">|- Item/</div> 
> <div style="text-indent:4em;">|- index.vue</div>
> <div style="text-indent:4em;">|- Button.vue</div>
> <div>|- Button.vue</div>
> 
> 或者
> <div>components/</div>
> <div>|- TodoList/</div>
> <div style="text-indent:2em;">|- Item/</div> 
> <div style="text-indent:4em;">|- Button.vue</div>
> <div style="text-indent:2em;">|- Item.vue</div>
> <div>|- TodoList.vue</div>


但是这种方式并不推荐，因为这会导致：

+ 许多文件的名字相同，使得在编辑器中快速切换文件变得困难。
+ 过多嵌套的子目录增加了在编辑器侧边栏中浏览组件所花的时间。


**不推荐**
> <div>components/</div>
> <div>|- TodoItem.vue</div>
> <div>|- TodoList.vue</div>
> <div>|- TodoButton.vue</div>
 
-or

> <div>components/</div>
> <div>|- SearchSidebar.vue</div>
> <div>|- NavigationForSearchSidebar.vue</div>

**推荐**
> <div>components/</div>
> <div>|- TodoList.vue</div>
> <div>|- TodoListItem.vue</div>
> <div>|- TodoListItemButton.vue</div>
 
-or

> <div>components/</div>
> <div>|- SearchSidebar.vue</div>
> <div>|- SearchSidebarNavigation.vue</div>


****
### 3.完整单词的组件名

组件名应该倾向于完整单词而不是缩写。

**不推荐**
> <div>components/</div>
> <div>|- SdSettings.vue</div>
> <div>|- UProfOpts.vue</div>

**推荐**
> <div>components/</div>
> <div>|- StudentDashboardSettings.vue</div>
> <div>|- UserProfileOptions.vue</div>

****
### 4.多个特性的元素

多个特性的元素应该分多行撰写，每个特性一行。

在 JavaScript 中，用多行分隔对象的多个属性更易读。

**不推荐**
``` HTML
<MyComponent foo="a" bar="b" baz="c"/>
```

**推荐**
``` HTML
<MyComponent
  foo="a"
  bar="b"
  baz="c"
/>
```

****
### 5.简单的计算属性

应该把复杂计算属性分割为尽可能多的更简单的属性。

更简单、命名得当的计算属性是这样的：

+ 易于测试

  当每个计算属性都包含一个非常简单且很少依赖的表达式时，撰写测试以确保其正确工作就会更加容易。

+ 易于阅读

  简化计算属性要求你为每一个值都起一个描述性的名称，即便它不可复用。这使得其他开发者 (以及未来的你) 更容易专注在他们关心的代码上并搞清楚发生了什么。

+ 更好的“拥抱变化”

  任何能够命名的值都可能用在视图上。举个例子，我们可能打算展示一个信息，告诉用户他们存了多少钱；也可能打算计算税费，但是可能会分开展现，而不是作为总价的一部分。

  小的、专注的计算属性减少了信息使用时的假设性限制，所以需求变更时也用不着那么多重构了。


**不推荐**
```javascript
computed: {
  price: function () {
    var basePrice = this.manufactureCost / (1 - this.profitMargin)
    return (
      basePrice -
      basePrice * (this.discountPercent || 0)
    )
  }
}
```

**推荐**
```js
computed: {
  basePrice: function () {
    return this.manufactureCost / (1 - this.profitMargin)
  },
  discount: function () {
    return this.basePrice * (this.discountPercent || 0)
  },
  finalPrice: function () {
    return this.basePrice - this.discount
  }
}
```

***
### 6.带引号的特性值

非空 HTML 特性值应该始终带引号

在 HTML 中不带空格的特性值是可以没有引号的，导致可读性变差。

**不推荐**
``` HTML
<input type=text>

<AppSidebar :style={width:sidebarWidth+'px'}>
```

**推荐**
``` HTML
<input type="text">

<AppSidebar :style="{ width: sidebarWidth + 'px' }">
```