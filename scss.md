## 译：SCSS/SASS完整指南 [原文链接](https://medium.freecodecamp.org/the-complete-guide-to-scss-sass-30053c266b23)

目前 SCSS 是使用最多的 css 预处理语言，在本教程中，我将Sassy、Sass、SCSS 做讲解，主要以 SCSS 为主。SCSS 可以看成是最初 Sass 语法的一个更新版本。

要开始使用 Sass，你需要知道一些基本概念。我将在本教程中介绍这些内容。

> 在本教程中，我会尽量完整的讲解，但可能会遗漏一些东西

所有 Sass/SCSS 代码最终都会通过编译回标准 CSS 在浏览器以呈现效果。因为浏览器目前并不没有支持 Sass/SCSS 或任何其他 CSS 预处理语言，CSS 规范也没有为类似功能提供替代方案。

## 让我们开始！
<!-- 在创建第一个 for 循环以生成属性值，并了解其优点之前，你不能真正体会到 Sassy CSS 的强大功能。但我们将从基本的 SCSS 原则开始，并在这些原则的基础上建立它们。 -->

### sass/scss 能做些什么，而普通的 CSS 做不到？

* 嵌套规则：将 CSS 属性嵌套在多个 { } 括号中。这可以使 CSS 代码看起来更整洁、直观。
* 变量： sass/scss 可以通过设置变量，执行更多操作。如通过 for 循环动态生成属性和属性值。同时可以将它们嵌入到 CSS 属性名中。
* 运算符：对 CSS 值进行加、减、乘、除、求余。当然在 CSS3 通过 calc() 也可以实现，但是在 sass/scss 中不必使用 calc() 也可以实现，而且更直观一些。
* 函数: sass/scss 可以自定义 css 函数。
* 三角函数：在其许多基本功能（+， - ，*，/）中，sass/scss 允许你编写自己的函数。你可以完全使用 sass/scss 语法编写自己的正弦和余弦（或其它三角函数）函数，就像在其他语言（如 JavaScript）中一样。
* 流程控制语句：你可以使用流程控制语句编写 CSS，例如 for-loops，while-loops，if-else 语句，但是 sass/scss 最终还是会编译成标准的 CSS，它只控制如何生成属性和值。
* 混合。创建一组 CSS 属性，重复使用或与任何新定义的“混合(mixins)”混合在一起使用。实际中，你可以使用“混合(mixins)”为相同的布局创建独立的主题。

### sass/scss 预处理器

sass/scss 不是动态的。因此你将无法实时生成或动态生成 CSS 的属性和值。但是可以用更有效的方式生成 css 标准属性(例如 CSS 动画)。

### 新语法

sass/scss 并没有为 CSS 语言添加任何新功能。只是简化了 css 编写的方式，节约了时间。 

### 必要条件

CSS 预处理器为 CSS 语言的语法添加了新功能。
目前主流的 CSS 预处理器有: Sass、SCSS、Less、tylus、PostCSS。
本教程主要介绍的 scss 与 sass 类似。[更多详细信息](https://www.sass-lang.com/。)

* SASS(.sass) 在语法上非常棒的样式表。
* SCSS(.scss) 友好的层叠样式表。

扩展 .sass和 .scss 类似但不相同。他们之间可以通过命令行对他们进行相互转换

> sass 转换为 scss  
> sass-convert style.sass style.scsss   
> sass 转换为 scss  
> sass-convert style.sass style.scsss

sass 是 Sassy CSS 的第一个规范，文件扩展名为 .sass。该开发始于2006年。但后来开发了一种扩展名为 .scss 的替代语法，部分开发人员更喜欢 .scss 语法。

由于目前没有浏览器对 css 预处理器(Sass、SCSS、Less...)支持。但是你可以在 [codepen.io](https://codepen.io/) 上测试。

本文旨在帮助你熟悉SCSS。其他预处理器功能也都类似，不同的只是语法。

### 扩展

任何表现形式的 Sassy CSS 都是 CSS 语言的扩展。因此，所有的 css 都可以在 sass/scss 中使用

### 变量

sass/scss 可以使用变量。变量以美元符号开头（例如 $color: #9c27b0）

> $number: 1;    
> $color: #ff0000;   
> $text: "Piece of string.";    
> $text: "Another string." !default;    
> $nothing: null;

重新定义覆盖变量名称，如果将 !default 附加到新定义的变量中，由于该变量已经存在，所以不会重新赋值。  
也就是说此示例中变量 $text 的最终值仍将是 “Piece of string.”。   
重定义的 “Another string。” 将被忽略。

```
#container {
    content: $text;
}
sass $text 可以分配给任何 css 属性
``` 

### 嵌套规则

标准CSS

```
#a {
    color: red;
}
#a #b {
    color: green;
}
#a #b #c p {
    color: blue;
}

```

上面的代码用 Sassy 的嵌套规则表示如下：

```
#a {
    color: red;
    #b {
        color: green;
        #c p {
            color: blue
        }
    }
}
嵌套规则 Sassy 嵌套看起来更加友好。
```

当然，它们最终都编译成标准的 CSS。
正如你所看到的，这种语法看起来更干净，重复性更低。  
这对于管理复杂的布局特别有用。这样方便编写与应用程序布局相匹配的嵌套CSS属性的布局对齐方式。
在最后，预处理器仍将其编译为标准 CSS 代码以便在浏览器中呈现。因此，我们只是改变了 CSS 的编写方式而已。

### 特性

Sassy CSS 添加了 & 字符指令。我们来看看它是如何工作的！ 

```
#p {
    color: black;
    a {
        font-weight: bold;
        &:hover {
            color: red;
        }
    }
}
    & 字符指令的用法
```

在第 5 行，& 字符用于指定 &:hover 并在编译后将 & 转换为父元素 a 。

编译成标准的 css 结果。

```
#p {
    color: black;
}
#p a {
    font-weight: bold;
}
#p a:hover {
    color: red;
}
    结果 - SCSS转换为CSS
```

### 混合(有的地方说成混入)

> 混合由 @mixin 指令定义(或也称为混合规则)

让我们用 @mixin 定义一个 Flex 布局。

```
@mixin fiexible() {
    display: flex;
    justify-content: center;
    align-items: center;
}

.centered-elements {
    @include fiexible();
    border: 1px solid gray;
}
```

现在，每次将 .centered-elements 类应用在 HTML 元素上时，改元素就将变为 Flexbox。mixins 的一个特性是可以与其他 css 属性一起使用。

 @mixin 同时可以像函数一样添加参数，然后将它们分配给 CSS 属性。这个将在下节讲解。

### 多浏览器示例

css 部分兼容性的处理(例如基于 -webkit) 或 Firefox(基于 -moz)。
Mixins 可以将多个 css 属性定义在一起，即使部分浏览器不兼容该属性。  
例如，如果你需要在基于 Webkit 的浏览器及其他浏览器中添加旋转元素，则可以创建以 $degree 为参数的 @mixin(混合)。

```
@mixin rotate($degree) {
    -webkit-transform: rotate($degree); //webkit-based
    -moz-transform: rotate($degree); //firefox
    -mstransform: rotate($degree); // internet explorer
    -o-transfrom: rotate($degree); // opera
    transfrom: rotate($degree); // standard css
}
兼容所有浏览器的 @mixin 。
```

现在我们所要做的就是在我们的 CSS 类定义中使用 @include 引用 @mixin：

```
.rotate-element {
    @include rotate(45deg);
}
编译后的结果
.rotate-element {
    -webkit-transform: rotate($degree);
    -moz-transform: rotate($degree);
    -mstransform: rotate($degree);
    -o-transfrom: rotate($degree);
    transfrom: rotate($degree);
}
这样所有浏览器都可以执行旋转效果了。
```

### 算术运算符

与标准 css 语法类似，你可以执行加、减、乘、除、求余，而无需使用 calc() 函数。  
但是有些用法可能会产生错误。

### 加法

```
p {
    font-size: 10px + 2em; // 错误用法
    font-size: 10px + 6px; // 16px
    font-size: 10px - 6;   // 16px
}
不使用 calc() 函数添加值,但是需要满足 sass/scss 语法规范。
```

### 减法

减法运算符的工作方式与加法运算符相同。

```
div {
    height: 12% - 2%;
    margin: 4rem - 1;
}
不同类型的值相减
```

### 乘法

乘法运算。就像 CSS 中的 calc(a * b)一样。

```
p {
    width: 10px * 10px;           // 错误用法
    width: 10px * 10;             // 100px
    width: 1px * 5 + 5px;         // 10px
    width: 2 * (5px + 5px);       // 50px
    width: 5px + (10px / 2) * 3;  // 20px
}
乘法和除法
```

### 除法

除法就有点棘手了。因为在标准 CSS 中，分割符号被保留用于与其它“简写属性”一起使用。例如，font:24/32px 。但 scss 与标准 CSS 兼容。

```
p {
    font: 16px/24px Arial , sans-serif;
}
```

在标准CSS中，除法符号出现在简写字体属性中。但是并不是做除法计算使用。那么，sass 如何处理

```
p {
    top: 16px / 24px            // 标准CSS
    top: (16px / 24px)          // 除法 (使用括号)
    top: #{$var1} / #{$val2};   // 使用变量，输出CSS
    top: $val1 / $val2;         // 除法
    top: random(4) / 5;         // 除法 (使用函数)
    top: 2px / 4px +3px;        // 除法 (算术的一部分)
}

编译后的结果
p {
    top: 16px/24px;
    top: .66667;
    top: 16px/24px;
    top: .66667;
    top: .2;
    top: 2px/4px 3px;
}
```
如果要进行除法运算，只需用括号包裹即可。否则，除法仅与其他运算符或函数组合使用。

### 余数

余数运算。在下面例子中，为一组 HTML 元素创建斑马条纹。

```
@mixin zebra() {
    @for $si from 1 through 7 {
        if ($si % 2 == 1) {
            .stripe-#{$si} {
                background-color: black;
                color: white;
            }
        }
    }
}

* { 
    @include zebra();
}
创建斑马条纹。
```

让我们从创建斑马图案的“混合”开始吧

>注：在 @for 和 @if 规则是在下面的章节中讨论。

几个HTML元素。

```
<div class = "stripe-1">zebra</div>
<div class = "stripe-2">zebra</div>
<div class = "stripe-3">zebra</div>
<div class = "stripe-4">zebra</div>
<div class = "stripe-5">zebra</div>
<div class = "stripe-6">zebra</div>
<div class = "stripe-7">zebra</div>
```

![浏览器图片](http://inews.gtimg.com/newsapp_match/0/7408930714/0)

### 比较运算符

| operator | example | description |
| :------: | :-----: | :---------- |
|  ==      | x == y  | 如果x和y相等，则返回true |
|  !=      | x != y  | 如果x和y不相等，则返回true |
|  >       | x > y   | 如果x大于y，则返回true |
|  <       | x < y   | 如果x小于y，则返回true |
|  >=      | x >= y  | 如果x大于或等于y，则返回true |
|  <=      | x <= y  | 如果x小于或等于y，则返回true |

那么在实践中使用比较运算符呢？
案例：根据传入的值判断 paddin 的值。

```
@mixin spacing($padding, $margin) {
    @if ($padding > $margin) {
        padding: $padding;
    } @else {
        padding: $margin
    }
}
.container {
    @include spacing(10px, 20px);
}
比较运算符的使用
```

编译后我们将得到这个CSS：

```
.container {
    padding: 20px;
}
```

### 逻辑运算符

| operator | example | description |
| :------: | :-----: | :---------- |
|  and     | x and y | 如果x和y为真，则返回真  |
|  or      | x or y  | 如果x或y为真，则返回真  |
|  not     | x not y | 如果x不是y，则返回true  |
逻辑运算符。

```
使用Sass逻辑运算符
创建一个按钮颜色类，根据其宽度更改其背景颜色。
@mixin button-color ($height, $width) {
    @if (($height < $width) and ($width >= 35px)) {
        backgroiund-color: blue;
    } @else {
        background-color: green;
    }
}
.button {
    @include button-color(20px, 30px)
}
编译后的结果
.button {
    background-color: green;
}
```

### 字符串

<!-- 在某些情况下，只要添加的字符串是相连的，就可以将字符串添加到有效的非引用CSS值中 -->

```
p {
    font: 50px Ari + "al"       // 符合 50px Arial
}
将常规 css 属性值与 sass/scss 字符串组合在一起。
```

```
p {
    font: "50px " + Arial; // 错误用法
}
```

```
p:after {
    content: "Quoted string width " + added tail.;      // 错误用法
}

p:after {
    content: "Quoted string with " + “added tail."      // 正确用法  包含空格的字符串必须用引号括起来。
}

p:after {
    content: "Long " + "String " + "Added";             // 多个字符串连接。
}

p:after {
    content: "Long " + 1234567 + "Added";               // 数字和字符串连接。
}

```

> 注意：content 属性仅适用于伪选择器。如 :before 和 :after。建议避免在 css 中使用 content 属性，而是始终在 HTML 标记之间指定内容。在此仅在 sass/scss 中做讲解使用。

### 流程控制语句

scss 具有函数()和指令(也称为规则)。当我们使用 mixins 时，相当于创建了一种函数。你可以传递参数。

函数通常会在末尾添加一个括号。指令/规则 以 @ 开头。  

就像在 JavaScript 或其他语言中一样，scss 允许使用流程控制语句。

### if() 函数

根据条件判断返回两个值中的一个。

```
/* 使用 if() 函数 */
if(true, 1px, 2px) => 1px
if(false, 1px, 2px) => 2px
```

### @if

@if 根据条件判断输出的指令。
```
/* 使用 @if 指令 */
p {
    @if 1 + 1 = 2 { border: 1px solid;}
    @if 7 < 5     { border: 2px solid;}
    @if null      { border: 3px solid;}
}

这个 Sassy if 语句编译为

p {
    border: 1px solid;
}
```

```
/* 创建变量 $type */

$type: river;

/* 如果变量为river，则设置为蓝色 */

div {
    @if $type == river {
        color: blue;
    }
}

/* 根据条件判断输出文字颜色 */
p {
    @if $type == tree {
        color: green;
    } @else if $type == river {
        color: blue;
    } @else if $type == dirt {
        color: brown;
    }
}
if 语句和 if-else 组合的示例。。
```

### does-parent-exist(判断父级是否存在)

and符号&将判断父元素是否存在（如果存在）。否则返回null。因此，它可以与@if指令结合使用。    
在下面的示例中，让我们看看如何根据父元素是否存在来创建条件CSS样式。
```
/* 判断父级是否存在 */ 
@mixin does-parent-exist {
    @if & {
        &:hover {
            color: blue
        }
    } @else {
        a {
            color: blue;
        }
    }
}

p {
    @include does-parent-exist();
}
如果父级不存在，& 计算结果为空，将使用 @else下的样式。
```

### @for

@for 用来定义连续重复的 css。 

```
@for $i from 1 through 5 {
    .definition-#{$si} {
        width: 10px * $si;
    }
}
for循环输出 5 个项目。
```