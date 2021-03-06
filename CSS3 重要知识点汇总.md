# CSS3 重要知识点汇总([CSS3新特性一览](http://www.cnblogs.com/star91/p/5659134.html))

[TOC]

---

## 1、盒模型 box-sizing属性

### 什么是盒模型？
盒模型是一种基础设计模式，定义了Web页面中的元素是如何看做盒子来解析的。

CSS中的每一个元素都是一个盒模型。网页设计中常听的属性名：content、padding、border、margin， CSS盒子模式都具备这些属性。这些属性我们可以用日常生活中的常见事物——盒子作一个比喻来理解，所以叫它盒子模式。

CSS盒子模型就是在网页设计中经常用到的CSS技术所使用的一种思维模型。

### box-sizing属性

Web前端设计师在制作布局效果时，常会因为给元素添加内距或边框二打破容器，破坏整个页面的布局。为了结局这个问题，CSS3添加了一个盒模型属性box-sizing，能够实现定义盒模型的解析方式，有content-box，border-box，inherit属性值。inherit：此值使用元素继承父元素的盒模型模式。

box-sizing属性主要用来控制元素的盒模型的解析模式，主要目的是控制元素的总宽度。有content-box和border-box属性值，content-box属性值内盒尺寸为：元素width/height=内容宽度/高度+padding+border+margin **内盒尺寸会发生变化** ；border-box内盒尺寸为：元素width/height=内容宽度/高度（包含了border和padding）**内盒尺寸不会发生变化** 。

![img](http://img.mukewang.com/5365d98000018fa606460416.jpg)

**在自适应布局当中，在元素基础上添加内距padding，按照标准盒模型解析，往往会将布局撑破，但使用box-sizing的border-box值，就不会打破布局**。

---

## 2、解释一下CSS3的flexbox，以及适用场景（[详细](https://www.cnblogs.com/sxz2008/p/6635196.html)）

CSS3引入了一种新的布局模式——Flexbox布局，即伸缩布局盒（Flexible Box）模型，[W3C官方称其为CSS弹性盒子布局](https://www.w3.org/TR/css-flexbox/) ；此布局对于设计比较复杂的页面非常有用，特别是“垂直居中”布局，非常容易实现。

### 基本概念

采用Flex布局的元素，称为Flex容器（flex container），简称”容器”。它的所有子元素自动成为容器成员，称为Flex项目（flex item），简称”项目”。

![img](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071004.png)

容器默认存在两根轴：水平的主轴（main axis）和垂直的交叉轴（cross axis）。主轴的开始位置（与边框的交叉点）叫做main start，结束位置叫做main end；交叉轴的开始位置叫做cross start，结束位置叫做cross end。

项目默认沿主轴排列。单个项目占据的主轴空间叫做main size，占据的交叉轴空间叫做cross size。

### 容器的属性

以下6个属性设置在容器上。

- flex-direction 属性决定主轴的方向（即项目的排列方向）

```css
.box {
  flex-direction: row | row-reverse | column | column-reverse;
}
/*
row（默认值）：主轴为水平方向，起点在左端。
column：主轴为垂直方向，起点在上沿。
row-reverse：主轴为水平方向，起点在右端。
column-reverse：主轴为垂直方向，起点在下沿 */
```

- flex-wrap属性

默认情况下，项目都排在一条线（又称”轴线”）上。flex-wrap属性定义，如果一条轴线排不下，可选择相应属性值换行。

```css
.box{
  flex-wrap: nowrap | wrap | wrap-reverse;
}
/*
nowrap（默认）：不换行。
wrap：换行，第一行在上方。
wrap-reverse：换行，第一行在下方
*/
```

-  flex-flows属性

flex-flow属性是flex-direction属性和flex-wrap属性的简写形式，默认值为row nowrap。

```css
.box {
  flex-flow: <flex-direction> || <flex-wrap>;
}
```

- **justify-content属性** , 定义了项目在主轴上的对齐方式。

```css
.box {
  justify-content: flex-start | flex-end | center | space-between | space-around;
}
/*
flex-start（默认值）：左对齐
flex-end：右对齐
center： 居中
space-between：两端对齐，项目之间的间隔都相等。
space-around：每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍。
*/
```

- **align-items属性**， 定义项目在交叉轴上如何对齐。

```css
.box {
  align-items: flex-start | flex-end | center | baseline | stretch;
}
/*
flex-start：交叉轴的起点对齐。
flex-end：交叉轴的终点对齐。
center：交叉轴的中点对齐。
baseline: 项目的第一行文字的基线对齐。
stretch
*/
```

-  align-content属性

align-content属性定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用。

```css
.box {
  align-content: flex-start | flex-end | center | space-between | space-around | stretch;
}
/*
flex-start：与交叉轴的起点对齐。
flex-end：与交叉轴的终点对齐。
center：与交叉轴的中点对齐。
space-between：与交叉轴两端对齐，轴线之间的间隔平均分布。
space-around：每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍。
stretch（默认值）：轴线占满整个交叉轴。
*/
```

### 适用场景：

1. Flexbox适用于包含有多个元素的盒子的样式渲染
2. Flexbox适用于在子元素的尺寸未知或者动态的情况下，对子元素的对齐方式、排列方式以及排序顺序进行控制展示。

---

## 3、CSS中的长度单位和颜色表示

### 长度单位 [详情](https://blog.csdn.net/javaloveiphone/article/details/51120476)

| 单位 | 描述                                                         |
| ---- | ------------------------------------------------------------ |
| %    | `%` 是相对于父元素的大小设定的比率，                         |
| in   | 英寸                                                         |
| cm   | 厘米                                                         |
| mm   | 毫米                                                         |
| em   | 相对单位，1em 等于当前的字体尺寸。2em 等于当前字体尺寸的两倍。例如，如果某元素以 12pt 显示，那么 2em 是24pt。在 CSS 中，em 是非常有用的单位，因为它可以自动适应用户所使用的字体。 |
| ex   | 一个 ex 是一个字体的 x-height。 (x-height 通常是字体尺寸的一半。) |
| pt   | 磅 (1 pt 等于 1/72 英寸)                                     |
| pc   | pica，大约6pt，1/6寸                                         |
| px   | 相对长度单位。像素px是相对于显示器屏幕分辨率而言的。         |
| vw   | 视窗宽度，1vw等于视窗宽度的1%。 `100vw`就是整个视窗的宽度    |
| vh   | 视窗高度，1vh等于视窗高度的1%。                              |
| vmin | 当前较小的vw和vh                                             |
| vmax | 当前较大的vw和vh                                             |
| rem  | 相对长度单位。r’是“root”的缩写，相对于根元素`<html>`的字体大小 html的尺寸是浏览器（chrome）默认尺寸12px |

- **说明：**

  1. vw，vh

     vw是相对视口（viewport）的宽度而定的，长度等于视口宽度的`1/100`。

     假如浏览器的宽度为200px，那么1vw就等于2px（200px/100）。

     vh是相对视口（viewport）的高度而定的，长度等于视口高度的`1/100`。

     假如浏览器的高度为500px，那么1vh就等于5px（500px/100）。

  2. vmin、vmax

     vmin和`vmax`是相对于视口的高度和宽度两者之间的`最小值`或`最大值`。

     如果浏览器的高为300px、宽为500px，那么1vmin就是3px，1vmax就是5px；如果浏览器的高为800px，宽为1080px，那么1vmin也是8px，1vmax也是10.8px。

### 颜色表示

| 单位              | 描述                                |
| ----------------- | ----------------------------------- |
| (颜色名)          | 颜色名称 (比如 red)                 |
| `rgb(x,x,x)`      | RGB 值 (比如 rgb(255,0,0))          |
| `rgb(x%, x%, x%)` | RGB 百分比值 (比如 rgb(100%,0%,0%)) |
| `#rrggbb`         | 十六进制数 (比如 #ff0000)           |

---

## 4、 link和@import引入css的区别

- link属于html标签，而@import是css提供的。

- 页面被加载时，link会并行加载节约时间；而@import引用的css是串行加载，会等到页面加载结束后加载，比较费时。

- link是html标签，因此没有兼容性，而@import只有IE5以上才能识别，且只能引入css文件。

- link因为是html元素，可以通过js DOM动态的添加样式，而@import却不可以。

- link方式样式的权重高于@import

  **link引入方式：**

  ```html
  <link rel="stylesheet" type="text/css" href="sheet.css">

  <!--
  rel = “stylesheet”表示的是当前文档与引用的文档之间的关系。 
  type=“text/css”表示引用的文档是文本类型的css文件。 
  href=“URL”指明引用文件的URL。 
  注意：上述这三个缺一不可，比如如果缺少rel页面link到多个css文件的话，可能会忽略该文件。
  -->
  ```

  **@import：**

  ```css
  @import url(sheet.css);
  .content{
    /* 
    ………………
     */
  }
  ```

   **@import是css的一个属性，代表着引入css文件到当下css文件中，且只能引入css文件。@import只能位于文件的顶部，这降低了灵活性。**

---

## 5、CSS3选择器注意点

### 简述CSS的选择器

**元素选择器**：* 、E、 E#id、 E.class

**关系选择器**：E、F、E>F、E+F、E~F

**属性选择器**：E[att]、E[att="val"]、E[att~="val"]、E[att^="val"]、E[att$="val"]、E[att*="val"]、E[att|="val"]

**伪类选择器**：E:link、E:visited、E:hover、E:active、E:focus、E:lang(fr)、E:not(s)、E:root、E:empty、E:target、E:first-child、E:last-chil等

**伪元素选择器**：E:first-letter/E::first-letter、E:first-line/E::first-line、E:before/E::before、E:after/E::after、E::selection

### (1) css选择器一览表

"CSS" 列指示该属性是在哪个 CSS 版本中定义的。（CSS1、CSS2 还是 CSS3。）

| 选择器                                                       | 例子                  | 例子描述                                            | CSS  |
| ------------------------------------------------------------ | --------------------- | --------------------------------------------------- | ---- |
| [.*class*](http://www.w3school.com.cn/cssref/selector_class.asp) | .intro                | 选择 class="intro" 的所有元素。                     | 1    |
| [#*id*](http://www.w3school.com.cn/cssref/selector_id.asp)   | #firstname            | 选择 id="firstname" 的所有元素。                    | 1    |
| [*](http://www.w3school.com.cn/cssref/selector_all.asp)      | *                     | 选择所有元素。                                      | 2    |
| [*element*](http://www.w3school.com.cn/cssref/selector_element.asp) | p                     | 选择所有 <p> 元素。                                 | 1    |
| [*element*,*element*](http://www.w3school.com.cn/cssref/selector_element_comma.asp) | div,p                 | 选择所有 <div> 元素和所有 <p> 元素。                | 1    |
| [*element* *element*](http://www.w3school.com.cn/cssref/selector_element_element.asp) | div p                 | 选择 <div> 元素内部的所有 <p> 元素。                | 1    |
| [*element*>*element*](http://www.w3school.com.cn/cssref/selector_element_gt.asp) | div>p                 | 选择父元素为 <div> 元素的所有 <p> 元素。            | 2    |
| [*element*+*element*](http://www.w3school.com.cn/cssref/selector_element_plus.asp) | div+p                 | 选择紧接在 <div> 元素之后的所有 <p> 元素。          | 2    |
| [[*attribute*\]](http://www.w3school.com.cn/cssref/selector_attribute.asp) | [target]              | 选择带有 target 属性所有元素。                      | 2    |
| [[*attribute*=*value*\]](http://www.w3school.com.cn/cssref/selector_attribute_value.asp) | [target=_blank]       | 选择 target="_blank" 的所有元素。                   | 2    |
| [[*attribute*~=*value*\]](http://www.w3school.com.cn/cssref/selector_attribute_value_contain.asp) | [title~=flower]       | 选择 title 属性包含单词 "flower" 的所有元素。       | 2    |
| [[*attribute*\|=*value*\]](http://www.w3school.com.cn/cssref/selector_attribute_value_start.asp) | [lang\|=en]           | 选择 lang 属性值以 "en" 开头的所有元素。            | 2    |
| [:link](http://www.w3school.com.cn/cssref/selector_link.asp) | a:link                | 选择所有未被访问的链接。                            | 1    |
| [:visited](http://www.w3school.com.cn/cssref/selector_visited.asp) | a:visited             | 选择所有已被访问的链接。                            | 1    |
| [:active](http://www.w3school.com.cn/cssref/selector_active.asp) | a:active              | 选择活动链接。                                      | 1    |
| [:hover](http://www.w3school.com.cn/cssref/selector_hover.asp) | a:hover               | 选择鼠标指针位于其上的链接。                        | 1    |
| [:focus](http://www.w3school.com.cn/cssref/selector_focus.asp) | input:focus           | 选择获得焦点的 input 元素。                         | 2    |
| [:first-letter](http://www.w3school.com.cn/cssref/selector_first-letter.asp) | p:first-letter        | 选择每个 <p> 元素的首字母。                         | 1    |
| [:first-line](http://www.w3school.com.cn/cssref/selector_first-line.asp) | p:first-line          | 选择每个 <p> 元素的首行。                           | 1    |
| [:first-child](http://www.w3school.com.cn/cssref/selector_first-child.asp) | p:first-child         | 选择属于父元素的第一个子元素的每个 <p> 元素。       | 2    |
| [:before](http://www.w3school.com.cn/cssref/selector_before.asp) | p:before              | 在每个 <p> 元素的内容之前插入内容。                 | 2    |
| [:after](http://www.w3school.com.cn/cssref/selector_after.asp) | p:after               | 在每个 <p> 元素的内容之后插入内容。                 | 2    |
| [:lang(*language*)](http://www.w3school.com.cn/cssref/selector_lang.asp) | p:lang(it)            | 选择带有以 "it" 开头的 lang 属性值的每个 <p> 元素。 | 2    |
| [*element1*~*element2*](http://www.w3school.com.cn/cssref/selector_gen_sibling.asp) | p~ul                  | 选择前面有 <p> 元素的每个 <ul> 元素。               | 3    |
| [[*attribute*^=*value*\]](http://www.w3school.com.cn/cssref/selector_attr_begin.asp) | a[src^="https"]       | 选择其 src 属性值以 "https" 开头的每个 <a> 元素。   | 3    |
| [[*attribute*$=*value*\]](http://www.w3school.com.cn/cssref/selector_attr_end.asp) | a[src$=".pdf"]        | 选择其 src 属性以 ".pdf" 结尾的所有 <a> 元素。      | 3    |
| [[*attribute**=*value*\]](http://www.w3school.com.cn/cssref/selector_attr_contain.asp) | a[src*="abc"]         | 选择其 src 属性中包含 "abc" 子串的每个 <a> 元素。   | 3    |
| [:first-of-type](http://www.w3school.com.cn/cssref/selector_first-of-type.asp) | p:first-of-type       | 选择属于其父元素的首个 <p> 元素的每个 <p> 元素。    | 3    |
| [:last-of-type](http://www.w3school.com.cn/cssref/selector_last-of-type.asp) | p:last-of-type        | 选择属于其父元素的最后 <p> 元素的每个 <p> 元素。    | 3    |
| [:only-of-type](http://www.w3school.com.cn/cssref/selector_only-of-type.asp) | p:only-of-type        | 选择属于其父元素唯一的 <p> 元素的每个 <p> 元素。    | 3    |
| [:only-child](http://www.w3school.com.cn/cssref/selector_only-child.asp) | p:only-child          | 选择属于其父元素的唯一子元素的每个 <p> 元素。       | 3    |
| [:nth-child(*n*)](http://www.w3school.com.cn/cssref/selector_nth-child.asp) | p:nth-child(2)        | 选择属于其父元素的第二个子元素的每个 <p> 元素。     | 3    |
| [:nth-last-child(*n*)](http://www.w3school.com.cn/cssref/selector_nth-last-child.asp) | p:nth-last-child(2)   | 同上，从最后一个子元素开始计数。                    | 3    |
| [:nth-of-type(*n*)](http://www.w3school.com.cn/cssref/selector_nth-of-type.asp) | p:nth-of-type(2)      | 选择属于其父元素第二个 <p> 元素的每个 <p> 元素。    | 3    |
| [:nth-last-of-type(*n*)](http://www.w3school.com.cn/cssref/selector_nth-last-of-type.asp) | p:nth-last-of-type(2) | 同上，但是从最后一个子元素开始计数。                | 3    |
| [:last-child](http://www.w3school.com.cn/cssref/selector_last-child.asp) | p:last-child          | 选择属于其父元素最后一个子元素每个 <p> 元素。       | 3    |
| [:root](http://www.w3school.com.cn/cssref/selector_root.asp) | :root                 | 选择文档的根元素。                                  | 3    |
| [:empty](http://www.w3school.com.cn/cssref/selector_empty.asp) | p:empty               | 选择没有子元素的每个 <p> 元素（包括文本节点）。     | 3    |
| [:target](http://www.w3school.com.cn/cssref/selector_target.asp) | #news:target          | 选择当前活动的 #news 元素。                         | 3    |
| [:enabled](http://www.w3school.com.cn/cssref/selector_enabled.asp) | input:enabled         | 选择每个启用的 <input> 元素。                       | 3    |
| [:disabled](http://www.w3school.com.cn/cssref/selector_disabled.asp) | input:disabled        | 选择每个禁用的 <input> 元素                         | 3    |
| [:checked](http://www.w3school.com.cn/cssref/selector_checked.asp) | input:checked         | 选择每个被选中的 <input> 元素。                     | 3    |
| [:not(*selector*)](http://www.w3school.com.cn/cssref/selector_not.asp) | :not(p)               | 选择非 <p> 元素的每个元素。                         | 3    |
| [::selection](http://www.w3school.com.cn/cssref/selector_selection.asp) | ::selection           | 选择被用户选取的元素部分。                          | 3    |

**注意：**

1. **CSS3中引入双冒号(`::`)是为了在伪类中，如:`:hover`,`:active`,区分伪元素，如`::before`，`::after`。**
2. **[CSS伪类和伪元素区别](https://www.w3cplus.com/css/an-ultimate-guide-to-css-pseudo-classes-and-pseudo-elements.html)**

---

### **(2) 通配符，是对所有标签设置的样式**

```css
*{
    margin:0px;
    padding:0px;
}
/*特别注意：通配符中设置内外边距为零时，会去掉所有块级元素自带的内外边距，会对表格、ul、ol、dl等标签布局造成破坏*/
```

### **(3) 多类选择器，注意写法**

```html
<p class='p1'>hello</p>;
<p class='p2'>hello</p>；
<p class='p1 p2'>hello</p>； <!--注意中间用空格隔开，会继承p1和p2的样式-->
```

```css
.p1{
   color: red;
};
.p2{
   font-size: 2em;
};
.p1.p2{              /*注意中间不能有空格，会继承p1和p2的样式，还会再添加自己的样式*/
    font-style: italic;  	/*斜体*/
}
```

### **(4) class 选择器与 id 选择器的区别**

- id只能在文档中使用一次，而class可以使用多次
- id选择器不能借个使用
- 当使用js时候，需要用到id，(`document.getElementById`)

### **(5) 属性选择器**

#### 用法

- 根据**属性**选择

- 根据具体**属性值**选择，属性和属性值完全匹配

- 根据**部分属性值匹配**选择

  ```html
  <p title="tit">属性选择器</p>
  <p title="title">属性选择器</p>
  <p title="title hello">属性选择器</p>
  ```

  ```css
  [title]{
      font-size: 20px;
      font-style: italic;
  } /*具有title属性的样式都会改变*/
  [title='title']{
      color: #dc2c24;
  }/*属性和属性值完全匹配，相当于唯一的标识*/
  [title~=title]{
      background-color: cadetblue;
  }/* ~ 代表模糊匹配，含有 title 字符串的属性值 都会改变*/
  ```

#### CSS3新添加的三个属性选择器

```css
[title*=tit]{
    /*和 ~= 一样，所有包含 tit 的样式*/
}
[title^=ti]{
    /*以 ti 开始的头部*/
}
[title$=lo]{
    /*以 lo 结束的末尾*/
}
```

### (5) 后代选择器与子元素选择器

```html
<div id="div">
    <p> Hello <strong> wuke </strong></p>
    <i> Hello </i>
</div>
```

```css
#div strong,i{
    font-weight: bold;
    color: #dc2c24;
}/*后代选择器通过空格隔开，strong和i都是div的后代，*/
#div>p>strong，#div>i{
    color: #8997a3;
}/*子元素选择器使用 > 来一层层寻找，不能越级，不能写成  #div>strong*/
```

**两者区别：**后代选择器可以越级，而子元素选择器只能一层一层递进。

### (6) 结构性伪类选择器

在CSS3中，结构性伪类选择器的共同特征是允许开发者根据文档中的结构来指定元素的样式。**常见的有 root、not、empty和target**

1. root 将样式绑定在页面的根元素当中，根元素位于最顶层，在页面中是html元素

   ```css
   :root{
       /*给整个页面添加一个背景颜色*/
       background-color:darkgrey;
   }
   body{
       background-color:darkgreen;
   }
   /*细节：如果有root 在用body时，body的背景颜色只给内容区域添加，如果没有root 则是给整个页面添加*/
   ```

2. not 除过子元素中的某个元素而给其他元素添加的样式

   ```html
   <div id='div1'>
       <h1>伪类选择器</h1>
       <h2>伪类选择器</h2>
       <p>伪类选择器</p>
   </div>
   ```

   ```css
   #div1 :not(h2){  /*id为div1下除过h2元素其他元素添加的样式，注意中间空格不能少*/
               color: seagreen;
               font-style: italic;
           }
   ```

3. empty 当前元素中内容为空白时的样式，多用于表格中的空白内容

   ```css
   table :empty{
       background-color:darkgreen
   }
   ```

4. target ，在页面中点击超链接跳转到目标（target）元素的样式

   ```html
   <a href="#a1">菜单1</a>
   <div id="a1">
       <h2>菜单1</h2>
       <p>菜单1内容</p>
   </div>
   ```

   ```css
   :target{ /*点击<a>标签链接跳转到div内容时的样式*/
               background-color: #b8912d;
           }
   ```

---

### (7) `:nth-of-type`与`:nth-child` ；`:only-of-type`与 `:only-child`的区别

1. `:nth-of-type(n)` 是选择父元素下的指定子类型（type）的第n个元素。**关键字 type， 按照类型来计算**

2. `:nth-child(n)` 是选择父元素下所有子元素（child）的第n个。**关键字 child， 按照个数来计算**

   ```html
   <div id="type">
       <h1>标题</h1>
       <p>段落1</p>
       <p>段落2</p>
       <p>段落3</p>
       <span>span1</span>
       <span>span2</span>
       <span>span3</span>
       <p>段落4</p>
       <i>斜体</i>
   </div>
   ```

   ```css
   /*第一种情况：有指定元素时，*/
   #type p:nth-of-type(3){ /*选择的是父元素（#type）下第三个 p 元素的样式*/
               background-color: #84c775;
           }；/*只选中 段落3*/

   /*第二种情况：没有指定元素时，选择的是父元素（#type）下所有 有至少3个相同元素的第三个元素*/
   #type :nth-of-type(3){ 
       /*在这选择的是第三个 p 元素和第三个 span 元素的样式*/
               background-color: #84c775;
           }；/*选中 段落3 和 span3*/
   ```

   ```css
   #type :nth-child(2){ /*所有子元素中的第二个*/
               background-color: #84c775;
           }； /*选中 段落1*/

   #type span:nth-child(5){ 
               background-color: #84c775;
           }； /*选中 span1*/
   /*注意 :nth-child 是从第一个子元素计算，此时指定 span 元素时n必须从5计算，否则不会有效果，所有指定元素作用不大。这种情况多用于无序列表中*/
   ```

3. `:only-of-type` 针对多个子元素当中没有重复的元素。

   ```css
   #type :only-of-type{ /*没有指定某个元素时，选中 #type中 所有没有重复的标签*/
       background-color: #84c775;
   }；/*选中 <h1> 和 <i> 标签*/

   #type i:only-of-type{ /*有指定某个元素时，则选中该元素*/
       background-color: #84c775;
   }；/*选中 <i> 标签*/
   ```

4. `:only-child` 针对父级元素中只有一个子元素的情况。

5. > ![UI元素状态选择器](./xuanzeqi.png)

### (8) 通用兄弟元素选择器：

**用来指定位于同一个父级元素中的某个元素之后的所有其他种类的兄弟元素所使用的样式。**

```html
<div id="brotherDiv">
    <div>
        <p>段落1</p>
        <p>段落2</p>
    </div>
    <p>段落3</p>  <!--此处的p与上面的div 是兄弟元素-->
    <p>段落4</p>
</div>
```

```css
#brotherDiv div~p{ /*父级元素下与 div 相邻的所有兄弟元素 p 的样式 */
            background-color: #d37fa3;
        }; /*选中 "段落3" 和 "段落4" */
```



## 6、 CSS float（浮动属性）[深入理解](https://segmentfault.com/a/1190000014554601)

**浮动属性的初衷：**

浮动属性的设计初衷，只是为了**实现文本环绕效果！** 时刻牢记这一点，才能正确使用浮动。

由于浮动元素脱离文档流，它后面的块级元素会忽略它的存在，占据它原本的位置，但是这个块级元素中的内联元素（行内元素），在流入页面时会考虑浮动元素的边界，它们会围绕着浮动元素。

**浮动元素的特征：**

1. 浮动元素脱离文档流(不完全脱离)
2. 浮动元素周围的外边距不会合并。
3. 浮动元素具有包裹性。
4. 浮动元素具有破坏性。

![浮动布局](./float.jpg)

5. 浮动元素块状化。不管元素本身是什么（inline/inline-block/block），只要浮动，自带display:inline-block声明

**小tips：**

- 父元素overflow: auto; 可解决浮动元素高度塌陷问题。


- 将元素浮动前，要设置body元素的margin和padding，以避免各浏览器的页面差异。

**浮动的规则 [详情](http://www.cnblogs.com/cc156676/p/5682439.html)**

---

## 7、 说说position，display

### position [深入理解](https://segmentfault.com/a/1190000014877050?utm_source=tag-newest)

**定义和用法：**

position 属性规定元素的定位类型。这个属性定义建立元素布局所用的定位机制。任何元素都可以定位，不过绝对或固定元素会生成一个块级框，而不论该元素本身是什么类型。相对定位元素会相对于它在正常流中的默认位置偏移。

**用position定位后的元素不会对排在其文档流上方的元素造成影响，只影响其本省和后面的元素位置。**

>**文档流概念：**
>
>文档流其实就 是文档的输出顺序，也就是我们通常看到的由左到右、由上而下的输出形式，在网页中每个元素都是按照这个顺序进行排序和显示的，而float和 position两个属性可以将元素从文档流脱离出来显示。

- `static` 

  默认值就是让元素继续按照文档流显示，不作出任何改变，无特殊定位，对象遵循正常文档流。top，right，bottom，left等属性不会被应用。

- `relative`

  相对定位，对象遵循正常文档流，但将依据top，right，bottom，left等属性在正常文档流中偏移位置。

  它是**以自己本身所在的正常文档流位置偏移的**（相对对象本身偏移）。本身位置变化了，而元素最初所占的物理空间依然还是存在；另外一点是，元素相对定位后并没有影响其他相邻的元素。

  >**注意：**
  >
  >**在Position属性值为absolute的同时，如果有一级父对象（无论是父对象还是祖父对象，或者再高的辈分，一样）的Position属性值为Relative时，则上述的相对浏览器窗口定位将会变成相对父对象定位，这对精确定位是很有帮助的。**

- `absolute`

  绝对定位，对象脱离正常文档流，使用top，right，bottom，left等属性进行绝对定位。而其层叠通过z-index属性定义。

  位置被设置为absolute后，**被设置的元素会被定义到包含它的父元素内的指定坐标（X坐标、Y坐标）。**

  比如：position：absolute；left:20px;top:80px; 这个容器始终位于距离浏览器左20px,距离浏览器上80px的这个位置。它不会随着窗口大小变化，只是固定在一个特定的坐标轴上面；

- `fixed`

  固定定位，对象脱离正常文档流，使用top，right，bottom，left等属性以窗口为参考点进行定位，当出现滚动条时，对象不会随着滚动。

### display

1. none： 元素不会显示，而且改元素现实的空间也不会保留。但有另外一个 visibility: hidden， 是保留元素的空间的。

2. inline： display的默认属性。将元素显示为内联元素，元素前后没有换行符。我们知道内联元素是无法设置宽高的，所以一旦将元素的display 属性设为 inline， 设置属性height和width是没有用的。此时影响它的高度一般是内部元素的高度（font-size）和padding。

3. block： 将元素将显示为块级元素，元素前后会带有换行符。设置为block后，元素可以设置width和height了。元素独占一行。

4. inline-block：行内块元素。这个属性值融合了inline 和 block 的特性，即是它既是内联元素，又可以设置width和height。

   >**这里提及下内联元素和块级元素的一些特点：**
   >
   >**内联元素：**
   >
   >  和其他元素都在一行上；
   >   元素的高度、宽度及顶部和底部边距不可设置；
   >   元素的宽度就是它包含的文字或图片的宽度，不可改变。
   >
   ><a>、<span>、<br>、<i>、<em>、<strong>、<label>、<q>、<var>、<cite>、<code>
   >
   >**块级元素：**
   >
   >   每个块级元素都从新的一行开始，并且其后的元素也另起一行。（真霸道，一个块级元素独占一行）；
   >   元素的高度、宽度、行高以及顶和底边距都可设置。
   >   元素宽度在不设置的情况下，是它本身父容器的100%（和父元素的宽度一致），除非设定一个宽度。
   >
   >常用的块状元素有：
   ><div>、<p>、<h1>...<h6>、<ol>、<ul>、<dl>、<table>、<address>、<blockquote> 、<form
   >
   >**内联块状元素：**
   >
   >   和其他元素都在一行上；
   >   元素的高度、宽度、行高以及顶和底边距都可设置。
   >
   >常用的内联块状元素有：
   ><img>、<input>

### position与display、float区别

1. **positon 与 display**

   元素分为内联元素和区块元素两类（当然也有其它的），在内联元素中有个非常重要的常识，即内联元素是不可以设置区块元素所具有的样式，例如:width | height。
   relative : 原来是什么类型的依旧是什么类型。
   absolute | fixed ： 元素就被重置为了区块元素，

   例如：打算为span元素指定大小，并绝对定位

   ```html
   <span style="position:absolute; width:100px; height:50px;">span</span> 这是完全正确的，
   <span style="position:absolute; display:block; width:100px; height:100px;">span</span>
   这里的display:block就是多余的了。
   ```


2. **position 与 float**

   一个元素若设置了 position:absolute | fixed; 则该元素就不能设置float。这是一个常识性的知识点，因为这是两个不同的流，一个是浮动流，另一个是“定位流”。
   但是 relative 却可以。因为它原本所占的空间仍然占据文档流。

---

## 8、什么是BFC，如何创建BFC？解决什么问题？

### 一、常见定位方案

在讲 BFC 之前，我们先来了解一下常见的定位方案，定位方案是控制元素的布局，有三种常见方案:

- 普通流 (normal flow)

> 在普通流中，元素按照其在 HTML 中的先后位置至上而下布局，在这个过程中，行内元素水平排列，直到当行被占满然后换行，块级元素则会被渲染为完整的一个新行，除非另外指定，否则所有元素默认都是普通流定位，也可以说，普通流中元素的位置由该元素在 HTML 文档中的位置决定。

- 浮动 (float)

> 在浮动布局中，元素首先按照普通流的位置出现，然后根据浮动的方向尽可能的向左边或右边偏移，其效果与印刷排版中的文本环绕相似。

- 绝对定位 (absolute positioning)

> 在绝对定位布局中，元素会整体脱离普通流，因此绝对定位元素不会对其兄弟元素造成影响，而元素具体的位置由绝对定位的坐标决定。

### 二、什么是BFC？ [BFC详解1](https://www.w3cplus.com/css/understanding-block-formatting-contexts-in-css.html)   [BFC详解2](https://www.w3cplus.com/css/understanding-bfc-and-margin-collapse.html)

首先，**Formatting context** (格式化上下文)  是 W3C CSS2.1 规范中的一个概念。它是页面中的一块渲染区域，并且有一套渲染规则，它决定了其子元素将如何定位，以及和其他元素的关系和相互作用。

**BFC 即 Block Formatting Contexts (块级格式化上下文)**，它属于上述定位方案的普通流。

**具有 BFC 特性的元素可以看作是隔离了的独立容器，容器里面的元素不会在布局上影响到外面的元素，同时BFC仍然属于文档中的普通流并且 BFC 具有普通容器所没有的一些特性。**

>#### BFC的通俗理解：
>
>#### 首先BFC是一个名词，是一个独立的布局环境，我们可以理解为一个箱子（实际上是看不见摸不着的），箱子里面物品的摆放是不受外界的影响的。转换为BFC的理解则是：BFC中的元素的布局是不受外界的影响（我们往往利用这个特性来消除浮动元素对其非浮动的兄弟元素和其子元素带来的影响。）并且在一个BFC中，块盒与行盒（行盒由一行中所有的内联元素所组成）

### 三、如何创建BFC

一个BFC可以被显式的触发，如果想要创建一个新的BFC，只需要给它添加下面提到的任何一个CSS样式就可以。

- 浮动元素：`float`的值不为`none`


- 绝对定位元素：**`position`的值不为`static`或者`relative`**


- **`display`的值为`inline-flex` , `inline-block`, `flex`, 或者 `table-cell`, `table-caption`,中的其中一个**


- **overflow 除了 visible 以外的值 (hidden、auto、scroll)**

### 四、BFC 特性及应用

1. **同一个 BFC 下外边距会发生折叠**
2. **BFC 可以包含浮动的元素（清除浮动）**
3. **BFC 可以阻止元素被浮动元素覆盖**

---

## **9、实现三栏布局（圣杯布局/双飞翼布局，flex布局）[详情](https://segmentfault.com/a/1190000008705541)**

实现原理：两边固定，中间自适应。

实现方案：

1. **`float`实现**

   > 基于纯`float`实现的三栏布局需要**将中间的内容放在HTML结构的最后，否则右侧会沉在中间内容的下侧**
   >
   > 原理：元素浮动后，脱离文档流，后面的元素受浮动影响，设置受影响元素的`margin`值即可
   >
   > 注意：float脱离文档流并不是完全脱离，文字还是会避开其空间而环绕左右。

   - 两边固定宽度，中间宽度自适应。
   - 利用中间元素的`margin`值控制两边的间距。
   - **宽度小于左右部分宽度之和时，右侧部分会被挤下去。**

2. **`position`实现**

   > 基于绝对定位的三栏布局：注意绝对定位的元素脱离文档流，相对于最近的已经定位的祖先元素进行定位。无需考虑HTML中结构的顺序

   - 缺点：有顶部对齐问题，需要进行调整，**注意中间的高度为整个内容的高度**

3. **`float`和`BFC`配合圣杯布局**

   > 必须将中间部分的HTML结构写在最前面，三个元素均设置向左浮动。两侧元素宽度固定，中间设置为100%；然后利用左侧元素负的`margin`值进行偏移，覆盖在中间的宽度之上；右侧的元素同样利用**负的`margin`值**进行覆盖

   存在的问题：不能自适应高度

4. **flex布局**

   `flexbox`布局最简洁使用，并且没有明显缺陷。

   - 仅需将容器设置为`display:flex;`，盒内元素两端对其，将中间元素设置为`100%`宽度即可填充空白，再利用`margin`值设置边距即可
   - 并且盒内元素的高度撑开容器的高度

5. **总结**

   - 纯`float`的三栏布局需要将中间的内容放在最后；
   - 绝对定位的三栏布局：元素对其有点问题
   - 圣杯布局：容器内不能撑开高度
   - `flex`布局最好，基本没有大的缺点。

---

##  10、为什么 overflow:hidden/auto 可以清除浮动以及几种清除浮动的方法？

### overflow:hidden/auto 清除浮动原理

正常理解：

`overflow:hidden` 的意思是超出的部分要裁切隐藏掉，那么如果 float 的元素不占普通流位置，普通流的包含块要根据内容高度裁切隐藏，如果高度是默认值auto那么不计算其内浮动元素高度就裁切就有可能会裁掉float。

**其实不然，**

**如果没有明确设定容器高情况下，它要计算内容全部高度才能确定在什么位置hidden，浮动的高度就要被计算进去，顺带达成了清理浮动的目标**
同理，
overflow 非默认值
position 非默认值
float 非默认值
等都是遵循这个布局计算思路。

>**最终的结果就是你看到的，overflow 取值只要不是 visible ，就会开启这个超级属性（BFC），此超级属性反过来决定了 height: auto 是如何计算的。从 BFC 的机制设计来看，把 float 元素纳入尺寸计算（即所谓父块包裹子块）是合理的。**

### 几种清除浮动的方法

浮动会漂浮于普通流之上，像浮云一样，但是只能左右浮动。正是这种特性，导致框内部由于不存在其他普通流元素了，表现出高度为0（高度塌陷）。

1. **添加额外标签，例如`<div style="clear:both"></div>`**

2. **使用br标签和其自身的html属性，例如`<br clear="all" />`**

3. **父元素设置 `overflow：hidden` 或设置 `over：auto`；**

4. **父元素也设置浮动**

5. **父元素设置`display:table `**   原理：将div属性变成表格（不建议使用）

6. **使用`:after`,`:before`或`::after` ,`::before`伪元素**

   ```css
   /*伪元素清除浮动示例*/
   p::after{
               content:""; /*必须有*/
               clear: both;
               display: block;
   }
   /*注意：:after,:before是在当前元素的content（内容）前后加的样式，不是在某个元素的前后加样式*/
   ```

---

## 11、css3动画，transition和animation的区别，animation的属性，加速度，重力的模拟实现

### **(1) `transform`属性**  [详情](https://www.w3cplus.com/content/css3-transform)

`transform` （转变）并不是一个动态属性，它是一个静态的属性。专注于改变元素基于默认位置的以下值。
注意，只是改变，并不是一个过程，**只是针对css的各种特殊改变**，完全可以看作是与`width，height，position`等同类的属性。

**有以下属性值**

| 值                                        | 描述                                    |
| ----------------------------------------- | --------------------------------------- |
| none                                      | 定义不进行转换。                        |
| matrix(n,n,n,n,n,n)                       | 定义 2D 转换，使用六个值的矩阵。        |
| matrix3d(n,n,n,n,n,n,n,n,n,n,n,n,n,n,n,n) | 定义 3D 转换，使用 16 个值的 4x4 矩阵。 |
| translate(x,y)                            | 定义 2D 转换。                          |
| translate3d(x,y,z)                        | 定义 3D 转换。                          |
| translateX(x)                             | 定义转换，只是用 X 轴的值。             |
| translateY(y)                             | 定义转换，只是用 Y 轴的值。             |
| translateZ(z)                             | 定义 3D 转换，只是用 Z 轴的值。         |
| scale(x,y)                                | 定义 2D 缩放转换。                      |
| scale3d(x,y,z)                            | 定义 3D 缩放转换。                      |
| scaleX(x)                                 | 通过设置 X 轴的值来定义缩放转换。       |
| scaleY(y)                                 | 通过设置 Y 轴的值来定义缩放转换。       |
| scaleZ(z)                                 | 通过设置 Z 轴的值来定义 3D 缩放转换。   |
| rotate(angle)                             | 定义 2D 旋转，在参数中规定角度。        |
| rotate3d(x,y,z,angle)                     | 定义 3D 旋转。                          |
| rotateX(angle)                            | 定义沿着 X 轴的 3D 旋转。               |
| rotateY(angle)                            | 定义沿着 Y 轴的 3D 旋转。               |
| rotateZ(angle)                            | 定义沿着 Z 轴的 3D 旋转。               |
| skew(x-angle,y-angle)                     | 定义沿着 X 和 Y 轴的 2D 倾斜转换。      |
| skewX(angle)                              | 定义沿着 X 轴的 2D 倾斜转换。           |
| skewY(angle)                              | 定义沿着 Y 轴的 2D 倾斜转换。           |
| perspective(n)                            | 为 3D 转换元素定义透视视图。            |

### **(2) `transition` 属性**  [详情](https://www.w3cplus.com/content/css3-transition)

**W3C 标准中对CSS3 的 `transition` (过渡) 这是样描述的：**css 的`transition`允许 css 的属性值在一定的时间区间内平滑地过渡。这种效果可以在鼠标单击、获得焦点、被点击或对元素任何改变中触发，并圆滑地以动画效果改变CSS的属性值。

`transition`是指当它所绑定的属性（比如width）发生改变的时候，不再突变，而是根据速度曲线慢慢变化。
这种改变不仅仅是定义好的hover改变，也包括后期js导致的改变，甚至不小心替换class名导致的css属性改变，也就是说无论在何种情况下发生的属性改变，都会导致过渡。

**有以下属性值：**

| 值                         | 描述                                                         |
| -------------------------- | ------------------------------------------------------------ |
| transition-property        | 规定设置过渡效果的 CSS 属性的名称。                          |
| transition-duration        | 规定完成过渡效果需要多少秒或毫秒。                           |
| transition-timing-function | 规定速度效果的速度曲线。有`ease`    `linear` `cubic-bezier`  [详情](https://www.w3cplus.com/content/css3-transition) |
| transition-delay           | 定义过渡效果何时开始。                                       |

```css
li{
    width: 200px;
    height: 200px;
    background-color: red;
    transition: transform 1s, width 1s, height 1s, background-color 1s;
    /*可以给常用的任何属性添加过度*/
}
li:hover{
    /*在此只需写变化后的属性值，当鼠标单击、获得焦点、被点击或对元素任何改变中触发时发生*/
    transform: rotate(30deg); /*使用到transform属性*/
    width: 240px;
    height: 240px;
    background-color: green;
}
```

### (3) `transition` 和 `transform` 比较

>**这个时候就会知道`transition`并不是与`transform`绑定的属性，初学者在刚看的时候总会以为有`transform`必然有`transition`，不然不可用，然而其实`transition`是完全可以不需要`transform`而独立使用的。`transform`可以看作只是一个基础属性，与width，height，position同类的属性，而`transition`只是规定了发生过渡的时候所需的自定义规则，两者独立使用也可。**

### (4) `animation` 动画  [详情](https://www.w3cplus.com/content/css3-animation)

#### `animation` 属性表

| 值                        | 描述                                     |
| ------------------------- | ---------------------------------------- |
| animation-name            | 规定需要绑定到选择器的 keyframe 名称。   |
| animation-duration        | 规定完成动画所花费的时间，以秒或毫秒计。 |
| animation-timing-function | 规定动画的速度曲线。                     |
| animation-delay           | 规定在动画开始之前的延迟。               |
| animation-iteration-count | 规定动画应该播放的次数。                 |
| animation-direction       | 规定是否应该轮流反向播放动画。           |

**`animation`需要绑定`keyframe`，这就说明`animation`才是与`keyframes`不可分割的，不定义`animation`，`keyframes`写了毫无意义，`keyframes`不写，`animation`怎么也动不起来。**

#### **keyframes关键帧：**

他也可以看作时间帧，这个时间在表述的时候以百分比的形式展示出来。

```css
@keyframes myStyle {     /*注意动画完成时会复原，不会停留*/
    0%   {top:0px;}
    25%  {top:200px;}
    50%  {top:100px;}
    75%  {top:200px;}
    100% {top:0px;}
}
li:hover{
    animation: myStyle 2s;  /*在此调用自定义动画 myStyle*/
}
```

>在每个百分比里，其实就是写好的css样式，里面可以规定width等基础属性，当然也可以写`transform`！按照时间从小到大进行过渡。
>
>那最后`keyframes`就是已经写好的有过渡的动画动作，这才是动态的！
>`transform`只是某刻的转变，加了时间，才叫动态，才叫动画！
>
>那写好了动画，给谁用，就用到了`animation`，将`animation`配置好写到css里，就可以给特定元素辅以动画了！每写出来的一个`keyframes`，只是代表一个动画行为，变长变短，转圈圈，仅此而已，没有别的含了。

### (5) transition与animation的区别

- `transition`是由属性的变化而触发的，无论这个变化是不是我们期望的，只要属性改变就会触发transition。


- `animation`的触发就是我们所设置的，根据她所规定的值指定我们想要的规则，可以在一开始就执行，可以执行一次再也不变。
- **`transition` 引起的 `hover` 等 变化效果 ，鼠标移除前变化不会消失（会停留），`animation` 定义的动画执行完会消失，即使鼠标一直在元素上`hover`**

## 12、CSS3 多边形、CSS 百分比参照问题 及 transform-origin、transform属性注意点

###     (1) CSS3 各种多边形画法 [详细](http://www.jb51.net/css/41448.html)

**注意：等边三角形画法；**

```css
.div1{
    width: 0;
    height: 0;
    border-left: 57.7px solid transparent;  /*三角形边是115.4px，具体要计算*/
    border-right: 57.7px solid transparent;
    border-top: 100px solid black            /*三角形高是100px*/
}
```

### (2)transform-origin属性  [详细](https://blog.csdn.net/xu_ya_fei/article/details/51711968)

### (3) transform属性覆盖

```css
.div2{
    position: relative;
    left: 50%;
    margin: -100px auto;             /*此处margin 是相对父级容器的宽度*/
    border-left: 57.7px solid transparent;  
    border-right: 57.7px solid transparent;
    border-top: 100px solid yellow;
    transform-origin: 50% 100%;
     /*transform: translate(-50%,0)*/;
    /*transform:  rotate(60deg) ;  如果分开写，则此处的transform会覆盖上面的transform属性值，只会参                                    考left的值来旋转，*/
    transform: translate(-50%,0) rotate(60deg)；/* 这样写则有效，会参考left和translate两个值先平移，再旋转； 若写成先写rotate(60deg)后写 translate(-50%,0)，则会先根据left位置旋转再根据translate平移造成位置异常；*/
}
```

### (4) CSS 百分比参照问题

- 参照父元素**宽度**的元素：padding **margin** width text-indent


- 参照父元素高度的元素：height


- 参照父元素属性:font-size   line-height


- 特殊：相对定位的时候，top(bottom)   left(right)参照的是父元素的内容区域的高度与宽度，而绝对定位的时候参照的是最近的定位元素包含padding的高度与宽度

---

## 13、雪碧图

1. 概念

    CSS雪碧图即CSS Sprites，也有人叫它CSS精灵，是一种CSS图像合并技术，该方法是将小图标和背景图像合并到一张图片上，然后利用CSS的背景定位来显示需要显示的图片部分。

2. 原理

   把小图标合成一张大图，通过给元素的公共css设置`background-image`为该合成图，这样每个元素都会以该合成图为背景，**而且页面也只加载一张合成图，然后再给每个元素单独微调其`background-position`。把多个请求合并成一个。** 说白了其实就是把一张大图通过控制background-position属性值来确定图片呈现的位置，加上显示窗口显示感兴趣的区域，之外的都会隐藏。

3. 主要作用

   利用CSS Sprites能很好地减少网页的http请求，从而大大的提高页面的性能。（只向应一张图片的请求，避免加载多张图片）

4. background-position

   background-position属性是雪碧图原理的核心。[**详情**](https://blog.csdn.net/bingkingboy/article/details/51059209)

   **注意**：使用百分比来设置属性值，是以**自身容器的长宽 减去 图片的长宽 乘以 百分比** 所得的数值来确定图片的起始位置。

   ```javascript
   公式：
       （容器自身的宽度/高度 - 图片自身的宽度/高度） x 百分比 
   ```

5. 雪碧图各种实现方法

   [**详情**](https://segmentfault.com/a/1190000007686042)

---

## 14、CSS中可继承的属性

继承就是指子节点默认使用父节点的样式属性。

可以继承的属性很少，**只有颜色，文字，字体间距行高对齐方式，和列表的样式可以继承。**

```
所有元素可继承：visibility和cursor。
内联元素可继承：letter-spacing、word-spacing、white-space、line-height、color、font、font-family、font-size、font-style、font-variant、font-weight、text-decoration、text-transform、direction。
终端块状元素可继承：text-indent和text-align。
列表元素可继承：list-style、list-style-type、list-style-position、list-style-image。
```