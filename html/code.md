## 1.HTML代码大小写
HTML标签名、类名、标签属性和大部分属性值统一用小写

## 2.元素标签
+ 自闭合（self-closing）标签，无需闭合 ( 例如： `img` `input` `br` `hr` 等 )
+ 可选的闭合标签（closing tag），需闭合 ( 例如：`</li>` 或 `</body>` )
+ 避免冗余标签(尽量减少标签数量)
+ 避免使用JS生成标签，特殊情况除外
+ 段落文字应该用`p`，避免使用`br`

## 3.元素属性：
+ 元素属性值使用双引号语法
+ 省略Boolean属性值。Boolean属性不用添加取值, `disabled`, `checked`, `selected`等
+ HTML 属性应该按照特定的顺序出现以保证易读性
  
    - `id`
    - `class`
    - `name`
    - `data-xxx`
    - `src, for, type, href`
    - `title, alt`
    - `aria-xxx, role`

## 4.Class 与 ID
+ class 应以功能或内容命名，不以表现形式命名
+ class 与 id 单词字母小写，多个单词组成时，采用中划线 `-` 分隔
+ 使用唯一的 id 作为 Javascript hook, 同时避免创建无样式信息的 class；
+ 禁止驼峰式命名

## 5.特殊字符引用
在HTML源代码中使用字符实体,如空格使用`&nbsp;`代替

## 6.代码缩进
+ 统一使用四个空格进行代码缩进（使用四个空格来代替tab），使得各编辑器表现一致，保持良好的简洁的树形结构
+ 每一个块级元素都另起一行，每一行都使用Tab缩进对齐。同时删除冗余的行尾的空格。

## 7.代码嵌套

元素嵌套规范，每个块状元素独立一行，内联元素可选

**推荐**
``` HTML
<div>
    <h1></h1>
    <p></p>
</div>	
<p><span></span><span></span></p>
```

**不推荐**
``` HTML
<div>
    <h1></h1><p></p>
</div>	
<p> 
    <span></span>
    <span></span>
</p>
```