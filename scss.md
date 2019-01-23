## 译：SCSS/SASS完整指南 [原文链接](https://medium.freecodecamp.org/the-complete-guide-to-scss-sass-30053c266b23)

在本教程中，Sassy，Sass和SCSS将大致相同。从概念上讲，没有太大区别。当你了解更多信息时，你将了解其中的差异，但基本上SCSS是人们现在使用的最多。它只是最初Sass语法的一个更新的版本。

要开始使用Sass，您需要知道一些基本概念。我将在本教程中介绍这些内容。

>  注意：我尽量完整。但我确信可能会遗漏一些东西。

所有Sass/SCSS代码都会编译回标准CSS，因此浏览器可以实际理解并呈现结果。浏览器目前没有直接支持Sass/SCSS或任何其他CSS预处理器，标准CSS规范也没有为类似功能提供替代方案。

### 让我们开始！

在创建第一个for循环以生成属性值，并了解其优点之前，您不能真正体会到Sassy CSS的强大功能。但我们将从基本的SCSS原则开始，并在这些原则的基础上建立它们。

### SASS/SCSS能做些什么，而普通的CSS做不到？

* 规则：将CSS属性嵌套在多个{}括号中。这使您的CSS代码看起来更整洁，更直观。
* 变量：您可以使用Sass变量执行更多操作：通过for循环进行迭代并动态生成属性值。您也可以将它们嵌入到CSS属性名中。它对property-name-N {...}定义很有用。
* 更好的运算符：对CSS值进行加，减，乘和除。当然原始的CSS通过calc（）实现了这个，但是在Sass中你不必使用calc（），而且实现更直观一些。
* 函数： Sass允许您自定义并创建可重用的CSS函数。
* 三角函数：在其许多基本功能（+， - ，*，/）中，SCSS允许您编写自己的函数。您可以完全使用Sass/SCSS语法编写自己的正弦和余弦（三角函数）函数，就像在其他语言（如JavaScript）中一样。但是需要了解一些三角学知识。但基本上，把正弦和余弦看作是数学值，可以帮助我们计算圆形进度条的运动或创建动画波效果。
* 代码流和控制语句：您可以使用熟悉的代码流和控制语句编写CSS，例如for-loops，while-loops，if-else语句，但是Sass最终还是会编译成标准的CSS，它只控制如何生成属性和值。同时它并一种实时语言，只有一个预处理器。
* 混合。创建一组CSS属性，并可重复使用它们或与任何新定义的“混合(mixins)”混合在一起使用。实际中，您可以使用“混合(mixins)”为相同的布局创建独立的主题。

### Sass预处理器

Sass不是动态的。因此您将无法实时生成或动画生成CSS的属性和值。但是你可以用更有效的方式生成css标准属性(例如CSS动画)。

### 新语法

SCSS并没有真正为CSS语言添加任何新功能。只是在很多情况下可以缩短编写CSS代码所花费的时间。

### 必要条件

CSS预处理器为CSS语言的语法添加了新功能。
有5个CSS预处理器：Sass，SCSS，Less，Stylus和PostCSS。
本教程主要介绍的SCSS是相似于Sass。你可以在这里了解更多关于Sass的信息：[https://www.sass-lang.com/。](https://www.sass-lang.com/。)

* SASS(.sass) 在语法上非常棒的样式表。
* SCSS(.scss) 友好的层叠样式表。

扩展 .sass和 .scss相似但不相同。同时可以通过命令行对他们进行相互转换

> sass 转换为 scss  
> sass-convert style.sass style.scsss   
> sass 转换为 scss  
> sass-convert style.sass style.scsss

Sass是Sassy CSS的第一个规范，文件扩展名为.sass。该开发始于2006年。但后来开发了一种扩展名为.scss的替代语法，一些开发人员认为这种语法更好。

目前在任何浏览器中都没有对Sassy CSS 的开箱即用支持，无论您使用哪种Sass语法或扩展名。但是你可以在codepen.io上测试5个预处理器。

本文旨在帮助您熟悉SCSS。其他预处理器也有相似的功能，但语法可能不同。

### 扩展

任何表现形式的Sassy CSS都是CSS语言的扩展。因此，所有的css都可以在Sass或SCSS中使用

### 变量

Sass/SCSS允许您使用变量。它们与您之前可能看到过的双破折号的CSS变量不同（例如，--color: #9c27b0）。相反，他们以美元符号开头（例如$color: #9c27b0）

> $number: 1;    
> $color: #ff0000;   
> $text: "Piece of string.";    
> $text: "Another string." !default;    
> $nothing: null;

您可以尝试覆盖变量名称。如果将 !default附加到新定义的变量中，但该变量已经存在，则不会再次重新赋值。  
换句话说，这意味着此示例中变量 $text的最终值仍将是“Piece of string.”。   
第二个赋值“Another string。”将被忽略，因为默认值已存在。

```
#container {
    content: #text;
}
sass $变量可以分配给任何css属性
``` 

### 嵌套规则

标准CSS

```
# 标准 css
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
上面的代码用Sassy的嵌套规则表示如下：
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
嵌套规则 - Sassy嵌套看起来友好很多。
```

当然，最终，它都编译成普通的CSS。
正如您所看到的，这种语法看起来更干净，重复性更低。  
这对于管理复杂的布局特别有用。这样方便编写与应用程序布局相匹配的嵌套CSS属性的布局对齐方式。
在最后，预处理器仍将其编译为标准CSS代码，使用编译后的在浏览器中呈现。因此，我们只是改变了CSS的编写方式而已。

### 特性

Sassy CSS添加了&（和）字符指令。   
我们来看看它是如何工作的！
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
在第5行，&字符用于指定&:hover并在编译后转换为父元素a的名称。 

那么当它转换为CSS时，上面的SCSS代码的结果是什么？

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

& 转换为父元素的名称。

### 混入(有的地方说成混合)
> 混入由@mixin指令定义(或也称为混入规则)

让我们定义一个Flex行为的@mixin：

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

现在，每次将 .centered-elements类应用于HTML元素时，它都将变为Flexbox。mixins的一个主要优点是您可以将它们与其他CSS属性一起使用。    
在这里，我还在 .centered-elements类中添加了border: 1px solid gray;

您甚至可以将参数传递给@mixin，就像一个函数一样，然后将它们分配给CSS属性。我们将在下一节中看一下。

### 多浏览器示例

一些兼容性的处理（例如基于-webkit）或Firefox（基于-moz）仅适用于它们出现的浏览器。
Mixins有助于在一个类中定义与浏览器无关的CSS属性。  
例如，如果您需要在基于Webkit的浏览器以及其他浏览器中添加旋转元素，则可以创建以$degree参数的“混入”

```
#mixin rotate($degree) {
    -webkit-transform: rotate($degree); //webkit-based
    -moz-transform: rotate($degree); //firefox
    -mstransform: rotate($degree); // internet explorer
    -o-transfrom: rotate($degree); // opera
    transfrom: rotate($degree); // standard css
}
与浏览器无关的@mixin用于指定旋转角度。
```
现在我们所要做的就是在我们的CSS类定义中使用 @include引用mixin：
```
.rotate-element {
    @include rotate(45deg);
}
按照所有浏览器进行旋转。
```

### 算术运算符

与标准CSS语法类似，您可以执行 加、减、乘、除，而无需使用CSS语法中的calc() 函数。  
但也有一些用法可能会产生错误。

### 加法
```
p {
    font-size: 10px + 2em; // 错误用法
    font-size: 10px + 6px; // 16px
    font-size: 10px - 6;   // 16px
}
不使用calc()函数添加值
只需确保以匹配的格式提供这两个值。
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

乘法运算。就像CSS中的calc(a * b)一样。

```
p {
    width: 10px * 10px;     // 错误用法
    width: 10px * 10;       // 100px
    width: 1px * 5 + 5px;   // 10px
    width: 2 * (5px + 5px); // 50px
    width: 5px + (10px / 2) * 3; // 20px
}
乘法和除法
```

### 除法

除法有点棘手。因为在标准CSS中，分割符号被保留用于与其它“简写属性”一起使用。例如，font:24/32px 定义了一个大小为25px且行高为32px的字体。但SCSS声称与标准CSS兼容。

```
p {
    font: 16px/24px Arial , sans-serif;
}
```

在标准CSS中，除法符号出现在简写字体属性中。但它并不习惯于实际划分价值。那么，Sass如何处理

```
p {
    top: 16px / 24px // 标准CSS
    top: (16px / 24px) // 除法 (添加括号)
    top: #{$var1} / #{$val2}; // 使用变量，输出CSS
    top: $val1 / $val2; // 除法
    top: random(4) / 5; // 除法 (使用函数)
    top: 2px / 4px +3px; // 除法 (算术的一部分)
}
```
如果要分割两个值，只需用括号包裹除法运算。否则，除法仅与某些其他运算符或函数组合使用。

### 余数

余数运算。在这个例子中，让我们看看它如何用于为任意一组HTML元素创建斑马条纹图案。

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

* {@include zebra();}
创建斑马条纹。
```

让我们从创建斑马图案的“混合”开始吧

>注：在 @for和 @if规则是在下面的章节中讨论。

此演示至少需要几个HTML元素：

```
<div class = "stripe-1">zebra</div>
<div class = "stripe-2">zebra</div>
<div class = "stripe-3">zebra</div>
<div class = "stripe-4">zebra</div>
<div class = "stripe-5">zebra</div>
<div class = "stripe-6">zebra</div>
<div class = "stripe-7">zebra</div>
这个混入实验的HTML源代码。
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

那么如何在实践中使用比较运算符呢？
案例：如果它大于边距，我们可以尝试编写一个选择填充大小的@mixin：

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
比较运算符的作用
```

编译后我们将得到这个CSS：

```
.container {
    padding: 20px;
}
“混合”使用的结果
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
```

### 字符串

在某些情况下，只要添加的字符串是相连的，就可以将字符串添加到有效的非引用CSS值中

```
p {
    font: 50px Ari + "al" //  符合 50px Arial
}
将常规CSS属性值与Sass/SCSS字符串组合在一起。
```

```
p {
    font: "50px " + Arial; // 错误
}
这个例子不起作用。
```

```
只要字符串不包含空格，您就可以在没有双引号的情况下添加字符串。例如，以下示例将无法编译：
p:after {
    content: "Quoted string width " + added tail.;
}
这个例子也行不通。下面为正确写法

p:after {
    content: "Quoted string with " + “added tail."
}
包含空格的字符串必须用引号括起来。

p:after {
    content: "Long " + "String " + "Added";
}
添加多个字符串。

p:after {
    content: "Long " + 1234567 + "Added";
}
添加数字和字符串。
```

> 注意：content属性仅适用于伪选择器。如:before和:after。建议避免在CSS中使用Content属性，而是始终在HTML标记之间指定内容。这里，仅在使用sass/scss中的字符串做解释使用。

### 流程控制语句

SCSS具有函数()和指令(也称为规则)。当我们使用mixins时，创建了一种函数。你可以传递参数。   
函数通常在函数名称的末尾添加一个括号。指令/规则 以@字符开头。  
就像在JavaScript或其他语言中一样，SCSS允许您使用流程控制语句。

### if() 函数

用法相当原始。该语句将根据条件返回两个指定值中的一个。

```
/* 使用 if() 函数 */     
if(true, 1px, 2px) => 1px     
if(false, 1px, 2px) => 2px
```

### @if

@if 是一个根据条件判断进行选择的指令。
```
/* 使用 @if 指令 */
p {
    @if 1 + 1 = 2 { border: 1px solid;}
    @if 7 < 5     { border: 2px solid;}
    @if null      { border: 3px solid;}
}
这个Sassy if 语句编译为：
p { border: 1px solid; }
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

/* 根据条件判断颜色 */
p {
    @if $type == tree {
        color: green;
    } @else if $type == river {
        color: blue;
    } @else if $type == dirt {
        color: brown;
    }
}
使用单个if语句和if-else组合的示例。。
```

### does-parent-exist(判断父级是否存在)

and符号&将判断父元素是否存在（如果存在）。否则返回null。因此，它可以与@if指令结合使用。    
在下面的示例中，让我们看看如何根据父元素是否存在来创建条件CSS样式。
```
/* 判断父级是否存在 */ 
@mixin does-parent-exist {
    @if & {
        /* 父级存在应用的 */
        &:hover {
            color: blue
        }
    } @else {
        /* 父级不存在应用的样式 */
        a {
            color: blue;
        }
    }
}

p {
    @include does-parent-exist();
}
如果父级不存在，&计算结果为空，将使用 @else下的样式。
```

### @for

@for规则用于对连续重复的css定义多次。

```
@for $i from 1 through 5 {
    .definition-#{$si} {
        width: 10px * $si;
    }
}
for循环迭代5个项目。
```