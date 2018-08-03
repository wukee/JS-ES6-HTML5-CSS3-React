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

## 13. Cookie与localStorage缓存机制的区别

| 特性           |                            Cookie                            |                        localStorage                         |                       sessionStorage                        |
| -------------- | :----------------------------------------------------------: | :---------------------------------------------------------: | :---------------------------------------------------------: |
| 数据的生命期   | 一般由服务器生成，可设置失效时间。如果在浏览器端生成Cookie，默认是关闭浏览器后失效 |                  除非被清除，否则永久保存                   |        仅在当前会话下有效，关闭页面或浏览器后被清除         |
| 存放数据大小   |                            4K左右                            |                          一般为5MB                          |                          一般为5MB                          |
| 与服务器端通信 | 每次都会携带在HTTP头中，如果使用cookie保存过多数据会带来性能问题 |     仅在客户端（即浏览器）中保存，不参与和服务器的通信      |     仅在客户端（即浏览器）中保存，不参与和服务器的通信      |
| 易用性         |          需要程序员自己封装，源生的Cookie接口不友好          | 源生接口可以接受，亦可再次封装来对Object和Array有更好的支持 | 源生接口可以接受，亦可再次封装来对Object和Array有更好的支持 |

---

## 14. Http/Https及websocket的工作原理和机制

### HTTP协议

概念：HTTP协议是一个客户端和服务器端请求和应答的标准（TCP），用于从服务器传输超文本到本地浏览器的传输协议，属于应用层的一个协议，由于其简捷、快速的方式成为互联网上应用最为广泛的一种网络协议。

**一次完整的HTTP事物的工作流程：**

1. 首先是域名解析
2. 发起TCP的三次握手
3. TCP链接成功后发起HTTP请求报文（报文格式：请求行get/post方法）、消息报头、请求正文）
4. 服务器响应HTTP请求
5. 拿到HTML后浏览器开始解析HTML代码
6. 浏览器对页面进行渲染呈献给用户

**注意点：**

1. TCP的三次握手；

   比如说，今天我想约一个朋友去吃饭，然后我要确定她有没有时间，所以我要给她发微信或者QQ 比如说“小李，在吗”，然后她收到消息回复我 “在的”，然后我这边收到她在的消息就可以给她说我今天想和她一起去吃饭这件事，再给她回复说“那今天一起去吃饭”。

2. get/post请求方法：[详情](http://www.techweb.com.cn/network/system/2016-10-11/2407736.shtml)

   get方式是把数据放到URL中，跟着网址一块来传递

   post 提交数据给指定的服务器处理，常用于提交表单。

### HTTPS协议

HTTP协议以明文方式发送内容，不提供任何方式的数据加密，因此使用HTTP协议传输隐私信息非常不安全，为了数据传输的安全，HTTPS在HTTP的基础上加入了SSL协议，SSL依靠证书来验证服务器的身份，并为浏览器和服务器之间的通信加密。

**1、客户端发起HTTPS请求**

这个没什么好说的，就是用户在浏览器里输入一个https网址，然后连接到server的443端口。

**2、服务端的配置**

采用HTTPS协议的服务器必须要有一套数字证书，这套证书其实就是一对公钥和私钥，如果对公钥和私钥不太理解，可以想象成一把钥匙和一个锁头，只是全世界只有你一个人有这把钥匙，你可以把锁头给别人，别人可以用这个锁把重要的东西锁起来，然后发给你，因为只有你一个人有这把钥匙，所以只有你才能看到被这把锁锁起来的东西。

**3、传送证书**

这个证书其实就是公钥，只是包含了很多信息，如证书的颁发机构，过期时间等等。

**4、客户端解析证书**

这部分工作是有客户端的TLS来完成的，首先会验证公钥是否有效，比如颁发机构，过期时间等等，如果发现异常，则会弹出一个警告框，提示证书存在问题。

如果证书没有问题，那么就生成一个随机值，然后用证书对该随机值进行加密，就好像上面说的，把随机值用锁头锁起来，这样除非有钥匙，不然看不到被锁住的内容。

**5、传送加密信息**

这部分传送的是用证书加密后的随机值，目的就是让服务端得到这个随机值，以后客户端和服务端的通信就可以通过这个随机值来进行加密解密了。

**6、服务段解密信息**

服务端用私钥解密后，得到了客户端传过来的随机值(私钥)，然后把内容通过该值进行对称加密，所谓对称加密就是，将信息和私钥通过某种算法混合在一起，这样除非知道私钥，不然无法获取内容，而正好客户端和服务端都知道这个私钥，所以只要加密算法够彪悍，私钥够复杂，数据就够安全。

**7、传输加密后的信息**

这部分信息是服务段用私钥加密后的信息，可以在客户端被还原。

**8、客户端解密信息**

客户端用之前生成的私钥解密服务段传过来的信息，于是获取了解密后的内容，整个过程第三方即使监听到了数据，也束手无策。

![img](https://pic002.cnblogs.com/images/2012/339704/2012071410212142.gif)

### WebSocket协议  [详情](https://segmentfault.com/a/1190000014149542?utm_source=tag-newest)

WebSocket协议是基于TCP的一种新的网络协议，不同于HTTP协议的短连接，它是一个全双工通讯可以实现客户端和服务器端的长连接，双向实时通信。WebSocket最大特点就是，服务器可以主动向客户端推送信息，客户端也可以主动向服务器发送信息，是真正的双向平等对话，广泛应用于社交聊天、直播、实况更新等。

**WebSocket和Http协议都属于应用层协议，两者都基于传输层的TCP协议。**
websocket协议本质上是一个基于tcp的协议，是先通过HTTP/HTTPS协议发起一条特殊的http请求进行握手后创建一个用于交换数据的TCP连接，或者说**借用**了HTTP的协议来完成一部分握手。在握手阶段是一样的此后服务端与客户端通过此TCP连接进行实时通信

---

## 15. git 分支管理方式

Git 是目前比较流行的一款代码管理工具，大量的软件项目由像 GitHub、GitLab这样的云服务平台或是私有的 Git 仓库来管理。在使用 Git 时通常会遇到分支管理方式的问题。目前有三种常见的git分支管理方式。

**TrunkBased 、 GitFlow和GitHub flow**  [详情](https://www.ibm.com/developerworks/cn/java/j-lo-git-mange/index.html)

### TrunkBased  单主干

**TrunkBased**  的特点是所有团队成员都在单个主干分支上进行开发。由于所有开发人员都在同一个分支上工作，团队需要合理的分工和充分的沟通来保证不同开发人员的代码尽可能少的发生冲突。持续集成和自动化测试是必要的，用来及时发现主干分支中的 bug。因为主干分支是所有开发人员公用的，一个开发人员引入的 bug 可能对其他很多人造成影响。不过好处是由于分支所带来的额外开销非常小。开发人员不需要频繁在不同的分支之间切换。

### **GitFlow** 

**GitFlow** 流程中包含 5 类分支，分别是 master、develop、新功能分支（feature）、发布分支（release）和 hotfix。这些分支的作用和生命周期各不相同。master 分支中包含的是可以部署到生产环境中的代码，这一点和 GitHub flow 是相同的。develop 分支中包含的是下个版本需要发布的内容。从某种意义上来说，develop 是一个进行代码集成的分支。当 develop 分支集成了足够的新功能和 bug 修复代码之后，通过一个发布流程来完成新版本的发布。发布完成之后，develop 分支的代码会被合并到 master 分支中。

### GitHub flow  提供了权限管理

 GithubFlow 是 GitHub 所使用的一种简单的流程。该流程只使用两类分支，并依托于 GitHub 的 pull request 功能。当需要进行修改时，从 master 分支创建一个新的分支。新分支的名称应该简单清晰地描述该分支的作用。所有相关的代码修改都在新分支中进行。开发人员可以自由地提交代码和 push 到远程仓库。当新分支中的代码全部完成之后，通过 GitHub 提交一个新的 pull request。

当然，代码分支模式的选择并没有绝对的正确和错误之分，关键是与项目的规模和发布节奏相匹配。

### Git使用规范

**[详情](https://blog.csdn.net/u010658879/article/details/50975084)**

![git使用规范](https://github.com/Hookee666/E6-H5-C3/blob/master/image/Git.jpg)

1. fork 将别人的仓库复制到自己的git上。 
2. clone 到本地仓库。 
3. 新建分支，修改提交A 
4. 修改提交B 
5. 远程master有更新C 
6. rebase操作 
7. push到自己的远程仓库 
8. 申请提交pull request 

### Gogs

**Gogs是我所了解的最棒的中国开发员开发自由软件的例子： 它是原创的，使用了先进的架构，基于Go语言和最新的JavaScript框架，它有着国际化的设计，并且尝试建立一个社区，它也没有企图推动任何商业化形式的专有版本。**

它还没有GitLab这样的开源平台成熟，但是它的轻量级设计是非常有前途的。一旦它开始支持pull-request和代码审查，

Gogs也专门提供了**组织**管理功能（组织可以代表一个公司，可以在**组织**下建立仓库、添加组织成员，然后通过创建和设置团队，将组织名下的仓库分别授权给不同的成员）



## 16. NodeJS、npm/yarn及webpack

### nodejs：

它是一个Javascript运行环境，依赖于Chrome V8引擎进行代码解释

最大的优势是借助JavaScript天生的事件驱动机制加V8高性能引擎，使编写高性能Web服务轻而易举。

其次，JavaScript语言本身是完善的函数式语言，在前端开发时，开发人员往往写得比较随意，让人感觉JavaScript就是个“玩具语言”。但是，在Node环境下，通过模块化的JavaScript代码，加上函数式编程，并且无需考虑浏览器兼容性问题，直接使用最新的ECMAScript 6标准，可以完全满足工程上的需求。

### npm/yarn

1. 首先npm/yarn是一个包管理工具，可以使开发者更方便地分享和重用代码、更方便地更新自己分享的代码。

   举例来说：

   如果我们在开发过程中使用jquery，那么是不是要引入react.js，你可能会下载这个react.js文件， 然后在代码中<script src="react.js"></script>是吧； 如果使用 npm  ，那么就方便了，直接在npm下使用命令：$ npm install react；就自动下载了；

2. 当我们引用了其他开发者的代码时，很容易检测出代码是否更新，可以很方便地下载更新代码。

**npm的功能**

1. 将特定功能的代码分享出去，以便他人重用
2. 当我们引用了其他开发者的代码时，很容易检测出代码是否更新，可以很方便地下载更新代码。

**npm的管理方式**

我们把代码组织成包package，有时也叫模块module。一个包是一个包含一个或多个文件的目录。在项目中会创建一个特殊的package.json的文件，package.json以元数据的形式定义了项目开发所需的依赖包。这样，便可以将这些小的解决单一问题的依赖包定义组织在一起，为这个项目提供大的可定制的依赖集。

**Yarn是由Facebook、Google、等联合推出了一个新的 JS 包管理工具 ，正如[官方文档](https://link.zhihu.com/?target=https%3A//code.facebook.com/posts/1840075619545360)中写的，Yarn 是为了弥补 npm 的一些缺陷而出现的。**

-  `npm install`的时候**巨慢**。特别是新的项目拉下来要等半天，删除node_modules，重新install的时候依旧如此。

- 同一个项目，安装的时候**无法保持一致性**。

### Yarn的优点

- **速度快** 。速度快主要来自以下两个方面：

1.  **并行安装**：无论 npm 还是 Yarn 在执行包的安装时，都会执行一系列任务。npm 是按照队列执行每个 package，也就是说必须要等到当前 package 安装完成之后，才能继续后面的安装。而 Yarn 是同步执行所有任务，提高了性能。
2. **离线模式**：如果之前已经安装过一个软件包，用Yarn再次安装时之间从缓存中获取，就不用像npm那样再从网络下载了。

- 安装**版本统一**：为了防止拉取到不同的版本，Yarn 有一个锁定文件 (lock file) 记录了被确切安装上的模块的版本号。每次只要新增了一个模块，Yarn 就会创建（或更新）yarn.lock 这个文件。这么做就保证了，每一次拉取同一个项目依赖时，使用的都是一样的模块版本。npm 和 Yarn 两者的不同之处在于，Yarn 默认会生成这样的锁定文件，而 npm 要通过 shrinkwrap 命令生成 npm-shrinkwrap.json 文件，只有当这个文件存在的时候，packages 版本信息才会被记录和更新。**
- **更简洁的输出**：npm 的输出信息比较冗长。在执行 npm install  的时候，命令行里会不断地打印出所有被安装上的依赖。相比之下，Yarn 简洁太多：默认情况下，结合了 emoji直观且直接地打印出必要的信息，也提供了一些命令供开发者查询额外的安装信息。
- **多注册来源处理：**所有的依赖包，不管他被不同的库间接关联引用多少次，安装这个包时，只会从一个注册来源去装，要么是 npm 要么是 bower, 防止出现混乱不一致。
- **更好的语义化**： yarn改变了一些npm命令的名称，比如 yarn add/remove，感觉上比 npm 原本的 install/uninstall 要更清晰。

### **webpack** [详情](https://segmentfault.com/a/1190000006178770)

WebPack可以看做是**模块打包机**：它做的事情是，分析你的项目结构，找到JavaScript模块以及其它的一些浏览器不能直接运行的拓展语言（TypeScript，Scss等），并将其转换和打包为合适的格式供浏览器使用。

Webpack的工作方式是：把你的项目当做一个整体，通过一个给定的主文件（如：index.js），Webpack将从这个文件开始找到你的项目的所有依赖文件，使用loaders处理它们，最后打包为一个（或多个）浏览器可识别的JavaScript文件。

## 17. React

React 是一个用于构建用户界面的 JAVASCRIPT 库， 起源于 Facebook 的内部项目，主要用于构建UI。React 拥有较高的性能，代码逻辑非常简单。

1. **组件化分工、合作**，通过 React 构建组件，使得代码更加容易得到复用，
2. **灵活** −React可以与其他库或框架很好地配合。
3. 虚拟DOM—性能高，React通过对DOM的模拟，最大限度地减少与DOM的交互。
4. 跨平台—ReactNative可以用于移动端

**MVC：MVC模式的意思是，软件可以分成三个部分**

1. View 传送指令到 Controller
2. Controller 完成业务逻辑后，要求 Model 改变状态
3. Model 将新的数据发送到 View，用户得到反馈

#### 虚拟DOM

- 在传统的 Web 应用中，我们往往会把数据的变化实时地更新到用户界面中，于是每次数据的微小变动都会引起 DOM 树的重新渲染。频繁的操作很可能会引发性能问题。React 为了解决这个问题，引入了虚拟 DOM 技术。React 通过渲染虚拟 DOM 到浏览器，使得用户界面得以显示。与此同时，React 在虚拟的 DOM 上实现了一个 diff 算法，当要更新组件的时候，会通过 diff 寻找到要变更的 DOM 节点，再把这个修改更新到浏览器实际的 DOM 节点上，所以在 React 中，当页面发生变化时实际上不是真的渲染整个 DOM，React 会通过自身的逻辑和算法，转化为真正的 DOM 节点。也正是因为这样的结构，虚拟 DOM 的性能要比原生 DOM 快很多。

## 18. TypeScript

[TypeScript](http://www.typescriptlang.org/) 是 JavaScript 的一个超集，主要提供了**类型系统**和**对 ES6 的支持**

**TypeScript 增加了代码的可读性和可维护性**

- 类型系统实际上是最好的文档，大部分的函数看看类型的定义就可以知道如何使用了
- 可以在编译阶段就发现大部分错误，这总比在运行时候出错好
- 增强了编辑器和 IDE 的功能，包括代码补全、接口提示、跳转到定义、重构等

**TypeScript 非常包容**

- TypeScript 是 JavaScript 的超集，`.js` 文件可以直接重命名为 `.ts` 即可
- 即使不显式的定义类型，也能够自动做出[类型推论](https://ts.xcatliu.com/basics/type-inference.html)
- 可以定义从简单到复杂的一切类型
- 即使 TypeScript 编译报错，也可以生成 JavaScript 文件
- 兼容第三方库，即使第三方库不是用 TypeScript 写的，也可以编写单独的类型文件供 TypeScript 读取

---

## 19. 在浏览器输入一个地址后都发生了什么？

![加载过程](https://github.com/Hookee666/E6-H5-C3/blob/master/image/resources.png)

1. 对于一个请求来说无论是地址栏输入的还是代码里加载的它都会有一个URL。加载资源的第一步就是把这URL解析，提取出里面的信息。
2. 第二步就是拿到上一步解析的域名，去DNS服务器上查找该域名对应的IP。
3. 第三步带着所有的请求信息去这个IP地址上请求资源，然后再从服务器上把返回的资源下载下来。
4. 最后一步，就是浏览器拿到这些资源以后，根据不同类型做不同方式的解析。