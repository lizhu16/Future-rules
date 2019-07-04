## 1.SCSS注释

SCSS文件内全部遵循CSS注释规范

## 2.嵌套规范

  --用到嵌套选择器，把它们放到最后，嵌套选择器之间要加上空白，相邻嵌套选择器之间也要加上空白。嵌套选择器中的内容也要遵循上述指引。

  
**推荐**
``` scss
.btn {
    background: green;
    font-weight: bold;

    .icon {
        margin-right: 10px;
    }
    
}
```

## 3.变量

可复用属性尽量抽离为页面变量，易于统一维护
``` scss
$color: red;
.jdc {
    color: $color;
    border-color: $color;
}
```

## 4.混合(mixin)

根据功能定义模块，然后在需要使用的地方通过 @include 调用，避免编码时重复输入代码段


## 5.占位选择器 %

如果不调用则不会有任何多余的 css 文件，占位选择器以 % 标识定义，通过 @extend 调用
``` scss
%borderbox {
    -webkit-box-sizing: border-box;
    box-sizing: border-box;
}
.jdc {
    @extend %borderbox;
}
``` 

## 6.extend 继承
``` scss
// SCSS
.jdc_1 {
    font-size: 12px;
    color: red;
}
.jdc_2 {
    @extend .jdc_1;
    font-weight: bold;
}

// 或者
%font_red {
    font-size: 12px;
    color: red;
}
.jdc_1 {
    @extend %font_red;
}
.jdc_2 {
    @extend %font_red;
    font-weight: bold;
}
```

## 7.for循环

``` scss
@for $i from 1 through 3 {
    .jdc_#{$i} {
        background-position: 0 (-20px) * $i;
    }
}
```

## 8.each循环

``` scss
// CSS
.jdc_list {
    background-image: url(/img/jdc_list.png);
}
.jdc_detail {
    background-image: url(/img/jdc_detail.png);
}

// SCSS
@each $name in list, detail {
    .jdc_#{$name} {
        background-image: url(/img/jdc_#{$name}.png);
    }
}


// CSS
.jdc_list {
    background-image: url(/img/jdc_list.png);
    background-color: red;
}
.jdc_detail {
    background-image: url(/img/jdc_detail.png);
    background-color: blue;
}

// SCSS
@each $name, $color in (list, red), (detail, blue) {
    .jdc_#{$name} {
        background-image: url(/img/jdc_#{$name}.png);
        background-color: $color;
    }
}
``` 

## 9.function函数

``` scss
@function pxToRem($px) {
    @return $px / 10px * 1rem;
}
.jdc {
    font-size: pxToRem(12px);
}
```


## 10.运算规范

运算符之间空出一个空格
``` scss
.jdc {
    width: 100px - 50px;
    width: 100px + 50px;
    width: 100px * 2;
    width: 100px / 2;
}
```

 >**注意运算单位，单位同时参与运算，所以 10px 不等于 10，乘除运算时需要特别注意**