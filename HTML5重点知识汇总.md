# HTML5重点知识汇总（[HTML5新特性一览](http://www.cnblogs.com/star91/p/5659134.html)）

[TOC]

---

## 1. HTML5新特性，语义化

### HTML5新特性

- 新特性应该基于HTML、CSS、DOM和JavaScript
- 减少了对外部插件的需求（如Flash）
- 更优秀的错误处理
- 更多取代脚本的机制
- HTML5应该独立于设备
- 用于绘画的canvas元素
- 用于媒介回放的video和audio元素
- 对本地离线存储的更好的支持
- 新元素和表单控件

### 语义化标签

所谓语义化标签就是一种我们仅通过标签名就能判断出该标签内容的语义的标签。一个典型的WEB页面包含头部，脚部，导航，中心区域，侧边栏。现在如果我们想在在HTML4的HTML区域中呈现这些内容，我们可能要使用DIV标签。但是在HTML5中通过为这些区域创建元素名称使他们更加清晰，也使得你的HTML更加可读。

![img](https://mmbiz.qpic.cn/mmbiz_jpg/eXCSRjyNYcZjb21CYHAQzVgcRrvlQvRial6UbhMnjWZPepKVo6MbQGBs2jWG2m6Jib18SBTGIBVjwS7nRIOuXIww/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1)

**➤<header>：代表HTML的头部数据**

**➤<footer>：页面的脚部区域**

**➤<nav>：页面导航元素**

**➤<article>：自包含的内容**

**➤<section>：使用内部article去定义区域或者把分组内容放到区域里**

**➤<aside>：代表页面的侧边栏内容**

---

## 2. HTML5新增标签与废除标签有哪些？

### 新增的标签（部分）

- 新增的结构元素：section、article、aside、header、footer、nav、figure等
- 新增的主要媒体元素与绘图元素：video、audio、details、canvas等
- 新增的input元素类型：email、url、number、range、DatePicker等

### 废除的标签（部分）

- 能使用CSS替代的元素：basefont、big、center、font、s、tt、u等
- 不在使用frame框架
- 只有部分浏览器支持的元素

---

## 3. 新增全局属性

- contentEditable：规定是否允许用户编辑内容
- designMode：制定整个页面是否可编辑，可编辑时支持contentEditable属性都变为可编辑状态
- hidden：规定该元素是否被隐藏，被隐藏的元素不会显示
- spellcheck：规定是否必须对元素进行拼写或语法检查
- tabindex：规定元素的 tab 键控制次序，用Tab键来遍历页面的所有元素。

## 4. HTML5中什么是不同的新的表单元素类型？

这里有10个重要的新的表单元素在HTML5中被介绍：

1. Color
2. Date
3. Datetime-local
4. Email
5. Time
6. Url
7. Range
8. Telephone
9. Number
10. Search

## 5. 哪些是块级元素哪些是行级元素，各有什么特点？

### 块级元素表

| 元 素        | 用 途                                                  |
| ------------ | ------------------------------------------------------ |
| < address >  | 定义地址                                               |
| < caption >  | 定义表格标题（居中标题）                               |
| < dd >       | **自定义列表中定义条目**                               |
| < div >      | 定义文档中的分区或节                                   |
| < dl >       | **自定义列表（类似ul，ol）**                           |
| < dt >       | **自定义列表中的项目**                                 |
| < fieldset > | 定义一个框架集                                         |
| < form >     | 创建 HTML 表单                                         |
| < h1 >       | 定义最大的标题                                         |
| < h2 >       | 定义副标题                                             |
| < h3 >       | 定义标题                                               |
| < h4 >       | 定义标题                                               |
| < h5 >       | 定义标题                                               |
| < h6 >       | 定义最小的标题                                         |
| < hr>        | 创建一条水平线                                         |
| < legend >   | 元素为 fieldset 元素定义标题                           |
| < li>        | 标签定义列表项目                                       |
| < noframes > | 为那些不支持框架的浏览器显示文本，于 frameset 元素内部 |
| < noscript > | 定义在脚本未被执行时的替代内容                         |
| < ol>        | 定义有序列表                                           |
| < ul>        | 定义无序列表                                           |
| < p>         | 标签定义段落                                           |
| < pre >      | 定义预格式化的文本                                     |
| < table>     | 标签定义 HTML 表格                                     |
| < tbody >    | 标签表格主体（正文）                                   |
| < td >       | 表格中的标准单元格                                     |
| < tfoot >    | 定义表格的页脚（脚注或表注）                           |
| < th >       | 定义表头单元格                                         |
| < thead >    | 标签定义表格的表头                                     |
| < tr >       | 定义表格中的行                                         |

**块级元素特点**：

1. 每个块级元素都是独自占一行，其后的元素也只能另起一行，并不能两个元素共用一行。
2. 元素的高度、宽度、行高和顶底边距都是可以设置的。　　
3. 元素的宽度如果不设置的话，默认为父元素的宽度。

### 行内元素列表

| 元素         | 用   途                           |
| ------------ | --------------------------------- |
| < a >        | 标签可定义锚                      |
| < abbr >     | 表示一个缩写形式                  |
| < acronym >  | 定义只取首字母缩写                |
| < b >        | 字体加粗                          |
| < bdo >      | 可覆盖默认的文本方向              |
| < big >      | 大号字体加粗                      |
| < br>        | 换行                              |
| < cite >     | 引用进行定义                      |
| < code >     | 定义计算机代码文本                |
| < dfn >      | 定义一个定义项目                  |
| < em >       | 定义为强调的内容                  |
| < i >        | 斜体文本效果                      |
| < img>       | 向网页中嵌入一幅图像              |
| < input>     | 输入框                            |
| < kbd >      | 定义键盘文本                      |
| < label >    | 标签为 input 元素定义标注（标记） |
| < q >        | 定义短的引用                      |
| < samp >     | 定义样本文本                      |
| < select >   | 创建单选或多选菜单                |
| < small >    | 呈现小号字体效果                  |
| < span>      | 组合文档中的行内元素              |
| < strong >   | 语气更强的强调的内容              |
| < sub >      | 定义下标文本                      |
| < sup >      | 定义上标文本                      |
| < textarea > | 多行的文本输入控件                |
| < var >      | 定义变量                          |

**特点**：

1. 可以和其他元素处于一行，不用必须另起一行。
2. 元素的高度、宽度及顶部和底部边距**不可**设置。
3. 元素的宽度就是它包含的文字、图片的宽度，不可改变。

------

**可变元素素列表--可变元素为根据上下文语境决定该元素为块元素或者内联元素**

| 元素       | 用  途                                       |
| ---------- | -------------------------------------------- |
| < button > | 按钮                                         |
| < del >    | 定义文档中已被删除的文本                     |
| < iframe > | 创建包含另外一个文档的内联框架（即行内框架） |
| < ins >    | 标签定义已经被插入文档中的文本               |
| < map >    | 客户端图像映射（即热区）                     |
| < object > | object对象                                   |
| < script > | 客户端脚本                                   |

**注意：**

**可以在css样式中用`display:inline`将块级元素设为行级元素；同样，也可以用`display:block`将行级元素设为块级元素**

## 6. **SGML（标准通用标记语言）和HTML（超文本标记语言），XML（可扩展标记语言）和HTML的之间有什么关系？**

SGML（标准通用标记语言）是一个标准，告诉我们怎么去指定文档标记。他是只描述文档标记应该是怎么样的元语言，HTML是被用SGML描述的标记语言。

因此利用SGML创建了HTML参照和必须共同遵守的DTD，你会经常在HTML页面的头部发现“DOCTYPE”属性，用来定义用于解析目标DTD。

> ```html
> <!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01//EN" 
> "http://www.w3.org/TR/html4/strict.dtd">
> ```

现在解析SGML是一件痛苦的事情，所以创建了XML使事情更好。XML使用了SGML，例如：在SGML中你必须使用起始和结束标签，但是在XML你可以有自动关闭的结束标签。

XHTML创建于XML，他被使用在HTML4.0中。你可以参考下面代码片段中展示的XML DTD。

> ```html
> <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" 
> "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
> ```

![img](https://mmbiz.qpic.cn/mmbiz_jpg/eXCSRjyNYcZjb21CYHAQzVgcRrvlQvRiaxaeN9QykBfNFfm1ENEibsRs6JLNsS4yKY0B011ly5E94svUZEB8rf9w/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1)

总之，SGML是所有类型的父类，较旧的HTML利用SGML，HTML4.0使用派生自XML的XHTML。

## 7.**HTML5中的datalist是什么？**

HTML5中的Datalist元素有助于提供文本框自动完成特性，如下图所示：

![img](https://mmbiz.qpic.cn/mmbiz_jpg/eXCSRjyNYcZjb21CYHAQzVgcRrvlQvRia0AFfW9K6veCRULia8uWiaqALbmXLsYYvssqz6lZc24Jiam8Gq66dHEjYQ/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1)

```html
<input list="Country">
<datalist id="Country">
  <option value="India">
  <option value="Italy">
  <option value="Iran">
  <option value="Israel">
  <option value="Indonesia">
</datalist>
```

## 8. **什么是SVG（Scalable Vector Graphics可缩放矢量图形）？**

SVG（Scalable Vector Graphics可缩放矢量图形）表示可缩放矢量图形。他是基于文本的图形语言，使用文本，线条，点等来进行图像绘制，这使得他轻便，显示更加迅速。

比方说，我们希望使用HTML5 SVG去显示以下简单的线条。![img](https://mmbiz.qpic.cn/mmbiz_jpg/eXCSRjyNYcZjb21CYHAQzVgcRrvlQvRia3b2XvsComRUSqUiaYRwVn8qofNIba29G8YMicQBBwzsTTysibf9hZbWLw/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1)

下面是HTML5代码

> ```html
> <svg id="svgelem" height="
> [object SVGAnimatedLength]" 
> xmlns="http://www.w3.org/2000/svg">
> <line style="stroke: rgb(255, 0, 0); 
> stroke-width: 2px;" 
> y2="[object SVGAnimatedLength]"
>  x2="[object SVGAnimatedLength]"
>   y1="[object SVGAnimatedLength]"
>    x1="[object SVGAnimatedLength]">
> </line>
> ```

## 9.**HTML5中canvas是什么？**

Canvas是HTML中你可以绘制图形的区域，我们如何使用Canvas来画一条简单的线？

1. 定义Canvas区域
2. 获取访问canvas上下文区域
3. 绘制图形

➤定义Canvas区域

定义Canvas区域你需要使用下面的HTML代码，这定义了你能进行绘图的区域。

> ```html
> <canvas id="mycanvas" 
> width="600"
>  height="500" 
>  style="border:1px solid #000000;">
>  </canvas>
> ```

➤获取画布区域的访问。

在画布上进行绘图我们首先需要获取上下文区域的关联，下面是获取画布区域的代码。

> ```html
> var c=document.getElementById("mycanvas");
> var ctx=c.getContext("2d");
> ```

➤绘制图形

现在一旦你获取了访问上下文，我们就可以开始在上下文中绘制了。首先调用“move”方法并从一个点开始，使用线条方法绘制线条然后使用stroke方法结束。

> ```html
> ctx.moveTo(10,10);
> ctx.lineTo(200,100);
> ctx.stroke();
> ```

以下是完整的代码。

> ```html
> <body  onload="DrawMe();">
> <canvas id="mycanvas" width="600" 
> height="500" 
> style="border:1px solid #000000;">
> </canvas>
> </body>
> <script>
> function DrawMe()
> {
> var c=document.getElementById("mycanvas");
> var ctx=c.getContext("2d");
> ctx.moveTo(10,10);
> ctx.lineTo(200,100);
> ctx.stroke();
> }
> ```

你可以得到以下输出。

![img](https://mmbiz.qpic.cn/mmbiz_png/eXCSRjyNYcZjb21CYHAQzVgcRrvlQvRiaLOoo29gMwS9MCsBibHJ17etJwxWrxxgPLjwJGQoULNibJExEW0HSbH1w/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1)

**Canvas和SVG图形的区别是什么？**

Note：-如果你看了之前的两个的问题，Canvas和SVG都可以在浏览器上绘制图形。因此在这个问题中，面试官想知道你在什么时候选用哪种方式。

| SVG                                                          | Canvas                                                     |
| ------------------------------------------------------------ | ---------------------------------------------------------- |
| 这个就好像绘制和记忆，换句话说任何使用SVG绘制的形状都能被记忆和操作，浏览器可以再次显示 | Canvas就像绘制和忘记，一旦绘制完成你不能访问像素和操作它   |
| SVG对于创建图形例如CAD软件是良好的，一旦东西绘制，用户就想去操作它 | Canvas在绘制和忘却的场景例如动画和游戏是良好的             |
| 因为为了之后的操作，需要记录坐标，所以比较缓慢               | 因为没有记住以后事情的意向，所以更快                       |
| 我们可以用绘制对象的相关事件处理                             | 我们不能使用绘制对象的相关事件处理，因为我们没有他们的参考 |
| 分辨率无关                                                   | 分辨率相关                                                 |

## 10. **如何使用Canvas和HTML5中的SVG去画一个矩形？**

HTML5使用SVG绘制矩形的代码

```html
<svg xmlns="http://www.w3.org/2000/svg"
 version="1.1">
<rect style="fill: rgb(0, 0, 255); 
stroke-width: 1px; stroke: rgb(0, 0, 0);
" height="[object SVGAnimatedLength]" 
width="[object SVGAnimatedLength]">
</rect>
```

HTML5使用Canvas绘制矩形的代码

> ```html
> var c=document.getElementById("mycanvas");
> var ctx=c.getContext("2d");
> ctx.rect(20,20,150,100);
> ctx.stroke();
> ```

## 11. HTML三种样式表插入方法

1. 外部样式表：

   ```html
   <link rel="stylesheet" type="text/css" href="mystyle.css">
   ```

2. 内部样式表：

   ```html
   <style>
       div{
           .....
       }
       </style>

   ```

3. 内联样式表：

   ```html
   <div style="color:red">
       ......
   </div>
   ```

## 12. `<a>`标签和`<img>`标签属性及href与src的区别

### **`<a>` 标签属性：** 

1. href 属性：指向另一个文档的链接或者一个具体的路径。

2. name 属性：创建文档内的链接。

   ```html
   <a href="http://www.baidu.con">百度</a>

   <a name="link">Hello</a>
   <a href="#link">跳转到Hello</a>
   ```

### **`<img>`标签属性：**

1. src 属性：指向图片的具体路径。

2. alt 属性：替换文本属性，当图片加载不出来时图片区域显示的文字

3. width： 图片显示的宽度

4. height：图片显示的高度

   ```html
   <img src="html.png" width="100px" height="100px" alt="主题">
   ```

### **href、src与url区别：**

1.  href 是Hypertext Reference的缩写，表示超文本**引用**。用来建立当前文档和外部资源之间的链接。常用的有：`<link>`、`<a>` 例如：

   ```html
   <link href="CSS3.css" type="text/css" rel="stylesheet">
   <a href="http://www.baidu.con">百度</a>
   ```

    浏览器会识别该文档为css文档，并行下载该文档，并且不会停止对当前文档的处理。这也是建议使用link，而不采用@import加载css的原因。

2.  src 是source的缩写，src 的内容是页面必不可少的一部分，是**引入**。src指向的内容会嵌入到文档中当前标签所在的位置。常用的有：img、script 例如

   ```javascript
   <script src="script.js"></script>  
   <img src="html.png">
   ```

   在浏览器下载，编译，执行这个文件之前页面的加载和处理会被暂停。这个过程与把js文件放到`<script>`标签里类似。这也是建议把JS文件放到底部加载的原因。当然，img标签页与此类似。浏览器暂停加载直到提取和加载图像。

3.  URL：统一资源定位符[详情](https://segmentfault.com/a/1190000002877022)

   ```css
   #div{  /*CSS中加载图片的方式*/
    background-image:url("img/bg.png");
   }
   ```


## 13. websocket的工作原理和机制 [详情](https://segmentfault.com/a/1190000014149542?utm_source=tag-newest)