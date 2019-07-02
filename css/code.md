1.代码风格: 统一使用展开格式书写样式
``` css
.jdc{
    display: block;
    width: 50px;
}
```

2.选择器
+ 尽量少用通用选择器 `*`
+ 不使用 ID 选择器
+ 不使用无具体语义定义的标签选择器

3.声明块格式
+ 选择器分组时，保持独立的选择器占用一行（为单个css选择器或新申明开启新行）
+ 声明块的左括号 `{` 前添加一个空格
+ 声明块的右括号 `}` 应单独成行
+ 声明语句中的 `:` 后应添加一个空格
+ 声明语句应以分号 `;` 结尾
+ 一般以逗号分隔的属性值，每个逗号后应添加一个空格
+ `rgb()、rgba()、hsl()、hsla()` 或 `rect()` 括号内的值，逗号分隔，但逗号后不添加一个空格
+ 对于属性值或颜色参数，省略小于 1 的小数前面的 0 （例如，.5 代替 0.5；-.5px 代替-0.5px）
+ 十六进制值应该全部小写和尽量简写，例如，#fff 代替 #ffffff
+ 不要为 `0` 指明单位

**推荐 **
``` css
.selector,
.selector-secondary,
.selector[type="text"] {
  padding: 15px;
  margin-bottom: 15px;
  border: 0;
  background-color: rgba(0,0,0,.5);
  box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;
}
```

4.代码缩进
统一使用四个空格进行代码缩进，使得各编辑器表现一致
**推荐**
``` css
.jdc {
    width: 100%;
    height: 100%;
}
```

5.属性书写顺序

    1.布局定位属性：display / position / float / clear / visibility / overflow

    2.自身属性：width / height / margin / padding / border / background

    3.文本属性：color / font / text-decoration / text-align / vertical-align / white- space / break-word

    4.其他属性（CSS3）：content / cursor / border-radius / box-shadow / text-shadow / background:linear-gradient …

**推荐**
``` css
.jdc {
    display: block;
    position: relative;
    float: left;
    width: 100px;
    height: 100px;
    margin: 0 10px;
    padding: 20px 0;
    font-family: Arial, 'Helvetica Neue', Helvetica, sans-serif;
    color: #333;
    background: rgba(0,0,0,.5);
    -webkit-border-radius: 10px;
    -moz-border-radius: 10px;
    -o-border-radius: 10px;
    -ms-border-radius: 10px;
    border-radius: 10px;
}
```

6.CSS3浏览器私有前缀

使用 Autoprefixer 自动添加浏览器厂商前缀，编写 CSS 时不需要添加浏览器前缀，直接使用标准的 CSS 编写。
