# float

## 介绍

float即为浮动，在CSS中的作用是使元素脱离正常的文档流并使其移动到其父元素的“最左边”或“最右边”。

+ 文档流：在html中文档流即为元素从上至下排列的顺序。
+ 脱离文档流（浮动层）：元素从正常的排列顺序被抽离。给元素的float属性赋值后，就是脱离文档流，进行左右浮动，紧贴着父元素(默认为body文本区域)的左右边框。
+ 最左边/最右边：上述的移动到父元素最左和最右是指元素往左或往右移动直到碰到另一个浮动元素或父元素内容区的边界（不包括padding）。

## 基本属性

  float是CSS中关于定位的属性。

  float有4个值：none, left, right, inherit (继承父元素的float属性值）

  float的姐妹属性：clear

  clear有4个值：both， none， left, right 

## float造成的影响

例子中使用的样式表
~~~css
 <style type="text/css">
    .wrapper{
        padding: 20px;
        border: 1px solid #F4606C;
        width: 350px;
    }
    .floatLeft{
        color:#333;
        width: 100px;
        height: 100px;
        border: 1px solid #000;
        text-align:center;
        float: left;
    }
    .floatRight{
        width: 100px;
        height: 100px;
        border: 1px solid #000;
        float: right;
    }
    .blue {
        background: #19CAAD;
    }
    .red {
        background: #F4606C;
    }
    .gray{
        background: #e6ceac;
    }
    .block {
        width: 200px;
        height: 150px;
        border: 1px solid #000;
    }
    .inline{
        display:inline;
        border: 1px solid #000;
    }
    .clear{
        clear:both;
    }
    .outer {
        height:150px;
        width: 350px;
        border:1px solid blue;
    }
 </style>
~~~

 <style type="text/css">
    .wrapper{
        padding: 20px;
        border: 1px solid #F4606C;
        width: 350px;
    }
    .floatLeft{
        color:#333;
        width: 100px;
        height: 100px;
        border: 1px solid #000;
        text-align:center;
        float: left;
    }
    .floatRight{
        width: 100px;
        height: 100px;
        border: 1px solid #000;
        float: right;
    }
    .blue {
        background: #19CAAD;
    }
    .red {
        background: #F4606C;
    }
    .gray{
        background: #e6ceac;
    }
    .block {
        width: 200px;
        height: 150px;
        border: 1px solid #000;
    }
    .inline{
        display:inline;
        border: 1px solid #000;
    }
    .clear{
        clear:both;
    }
    .outer {
    height:150px;
    width: 350px;
    border:1px solid blue;
}
 </style>

### 对其父元素的影响

对于其父元素来说，元素浮动之后，它脱离当前正常的文档流，所以它也无法撑开其父元素，造成父元素的塌陷。

 ~~~html
<div class="wrapper">
    <div class="floatLeft blue">左浮动的元素</div>
</div>
 ~~~

<div class="wrapper">
    <div class="floatLeft blue">左浮动的元素</div>
</div>
<div class="clear" ></div>

### 对其兄弟元素的影响(非浮动块级元素)

在现代浏览器和IE8+下，该元素会忽视浮动元素的而占据它的位置，并且元素会处在浮动元素的下层（并且无法通过z-index属性改变他们的层叠位置），但它的内部文字和其他行内元素都会环绕浮动元素。

~~~html
<div class="wrapper">
    <div class="floatLeft blue" >左浮动的元素</div>
    <div class="block gray" >
        block兄弟元素
    </div>
</div>
~~~

<div class="wrapper">
    <div class="floatLeft blue" >左浮动的元素</div>
    <div class="block gray" >
    block兄弟元素
    </div>
</div>
<div style="clear: both;"></div>
<br/><br/>

### 对其兄弟元素的影响(非浮动内联元素)

元素会环绕浮动元素排列

~~~html
<div class="wrapper" >
    <div class="floatLeft blue" >浮动的元素</div>
    <div class="inline gray">
    inline兄弟元素 inline兄弟元素 inline兄弟元素 inline兄弟元素 inline兄弟元素 inline兄弟元素 inline兄弟元素 inline兄弟元素 inline兄弟元素 inline兄弟元素 
    inline兄弟元素 inline兄弟元素 inline兄弟元素 inline兄弟元素 inline兄弟元素 inline兄弟元素 inline兄弟元素 inline兄弟元素
    </div>
</div>
~~~

<div class="wrapper" >
    <div class="floatLeft blue" >浮动的元素</div>
    <div class="inline gray">
    inline兄弟元素 inline兄弟元素 inline兄弟元素 inline兄弟元素 inline兄弟元素 inline兄弟元素 inline兄弟元素 inline兄弟元素 inline兄弟元素 inline兄弟元素 
    inline兄弟元素 inline兄弟元素 inline兄弟元素 inline兄弟元素 inline兄弟元素 inline兄弟元素 inline兄弟元素 inline兄弟元素
    </div>
</div>
<div style="clear: both;"></div>

### 对其兄弟元素的影响（浮动同一个方向）

当一个浮动元素在浮动过程中碰到同一个方向的浮动元素时，它会紧跟在它们后面。浮动的队列和正常的文档流队列也依旧在同一个父元素当中。

<div class="wrapper">
    <div class="floatLeft red">第一个左浮动元素</div>
    <div class="floatLeft blue">第二个左浮动元素</div>
</div>
<div style="clear: both;"></div>


### 对其兄弟元素的影响（浮动相反方向）

一个向左浮动，一个向右浮动，在父元素足够宽的时候两条队列是互不受影响的。因此他们在同一条水平线上。

~~~html
<div class="wrapper">
    <div class="floatLeft red">>左浮动元素</div>
    <div class="floatRight blue">右浮动元素</div>
</div>
~~~

<div class="wrapper">
    <div class="floatLeft red">>左浮动元素</div>
    <div class="floatRight blue">右浮动元素</div>
</div>
<div style="clear: both;"></div>

在父元素过窄或者左右两边的队列过长时，在html文档结构中靠后的浮动队列（这里是右浮动队列）的队列会另起一行排列或者错开排列。

~~~html
<div class="wrapper">
    <div class="floatLeft red">第一个左浮动元素</div>
    <div class="floatLeft red">第二个左浮动元素</div>
    <div class="floatLeft blue">第一个右浮动元素</div>
</div>
~~~

<div class="wrapper">
    <div class="floatLeft red">第一个左浮动元素</div>
    <div class="floatLeft red">第二个左浮动元素</div>
    <div class="floatLeft blue">第一个右浮动元素</div>
    <div class="floatLeft blue">第二个右浮动元素</div>
</div>
<div style="clear: both;"></div>

~~~html
<div class="wrapper">
    <div class="floatLeft red">第一个左浮动元素</div>
    <div class="floatLeft red">第二个左浮动元素</div>
    <div class="floatLeft red">第三个左浮动元素</div>
    <div class="floatRight blue">第一个右浮动元素</div>
    <div class="floatLeft blue">第二个右浮动元素</div>
</div>
~~~

<div class="wrapper">
    <div class="floatLeft red">第一个左浮动元素</div>
    <div class="floatLeft red">第二个左浮动元素</div>
    <div class="floatLeft red">第三个左浮动元素</div>
    <div class="floatRight blue">第一个右浮动元素</div>
    <div class="floatRight blue">第二个右浮动元素</div>
</div>
<div style="clear: both;"></div>


## float对自身元素的影响

float对象将被视作块对象(block-level)，即display属性等于block。

## float对子元素的影响

道当一个元素浮动时，在没有清楚浮动的情况下，它无法撑开其父元素，但它可以让自己的浮动子元素撑开它自身，
并且在没有定义具体宽度情况下，使自身的宽度从100%变为自适应（浮动元素display:block）。
其高度和宽度均为浮动元素高度和非浮动元素高度之间的最大值。

## 父元素之外的非浮动元素

当一个元素浮动时，在没有清楚浮动的情况下，它无法撑开其父元素，也就是父元素的宽高都为0。并且其父元素之外的非浮动元素也会无视该浮动元素。

~~~html
<div class="wrapper">
    <div class="floatLeft red">左浮动元素</div>
</div>
<div class="outer">外部block元素</div>
~~~

<div class="wrapper" style="padding:0;">
    <div class="floatLeft red">左浮动元素</div>
</div>
<div class="outer">外部block元素</div>
<div style="clear: both;"></div>

## 父元素之外的浮动元素

当浮动元素的父元素之外的元素为浮动元素时，他们仿佛去到了同一个世界里。排序机制与之前兄弟浮动元素的规则一致。


## 实践

**float设计的目的是实现文字环绕排版，这个功能是其他的css属性中都不能实现的。**

float使元素脱离脱离文档流，造成父元素高度塌陷，不应该用于布局等其他用处。

使用float实现文字环绕排版：
<p>
<span style="float:left;width:0.7em;font-size:400%;font-family:algerian,courier;line-height:80%;">T</span>
This is some text. This is some text.
This is some text. This is some text. This is some text.
This is some text. This is some text. This is some text.
This is some text. This is some text. This is some text.
This is some text. This is some text. This is some text.
This is some text. This is some text. This is some text.
This is some text. This is some text. This is some text.
</p>
<div style="clear: both;"></div>

## 参考

[all-about-floats](https://css-tricks.com/all-about-floats/)
[css_positioning_floating](http://www.w3school.com.cn/css/css_positioning_floating.asp)

