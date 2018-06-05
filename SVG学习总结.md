# SVG学习总结

## 1、svg 之 viewbox [详情](https://segmentfault.com/a/1190000007143300)

### viewport（视口）

在SVG中viewport主要是通过**width**和**height**属性来定义的。比如，我们定义一个**width="600"**和**height="600"**就表示我们定义了一个600X600的可视区域，这与html和css中还有一点不同，SVG本身定义这些属性并没有单位，不过基本上都是以像素px为单位的。

### viewbox 

  **[详情](http://www.zhangxinxu.com/wordpress/2014/08/svg-viewport-viewbox-preserveaspectratio/)**

viewbox简单的理解就是用来定义SVG的可视范围，那跟上面提到的viewbox有什么关系呢？这样来说吧，当没有设置viewbox的时候，viewbox就是整个viewport的大小，而当我们设定了viewbox，等于就是告诉SVG我指定的这个区域是我要显示的，SVG就会把这个区域放大到viewport的大小，比如电视机，电视机就是那么大（viewport），而电视机里的画面，可以特写也可以全景，这就是viewbox。

```javascript
viewBox="x, y, width, height"  // x:左上角横坐标，y:左上角纵坐标，width:宽度，height:高度
```

更形象的解释就是：SVG就像是我们的显示器屏幕，viewBox就是截屏工具选中的那个框框，最终的呈现就是把框框中的截屏内容再次在显示器中全屏显示！

### preserveAspectRatio属性

**[详情](https://segmentfault.com/a/1190000014697164)**

preserveAspectRatio和viewbox是一个绝配的搭档，特别是当viewbox的值和viewport的值（也就是宽和高）不一样的时候，preserveAspectRatio属性就直接决定浏览器怎么来显示图片。

```javascript
preserveAspectRatio="xMidYMid meet”   
```

第1个值表示，viewBox如何与SVG viewport对齐；第2个值表示，如何维持高宽比（如果有）。
其中，第1个值又是由两部分组成的。前半部分表示x方向对齐，后半部分表示y方向对齐。家族成员如下：（x, y自由合体就可以了）

![clipboard.png](https://segmentfault.com/img/bV9Pys?w=1018&h=524)

preserveAspectRatio属性第2部分的值支持下面3个：

![clipboard.png](https://segmentfault.com/img/bV9PyO?w=1022&h=278)

**此属性也是应用在<svg>元素上，且作用的对象都是viewBox。**