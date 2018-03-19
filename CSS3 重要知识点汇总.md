# CSS3 重要知识点汇总

## · 盒模型、box-sizing属性

### 什么是盒模型？
盒模型是一种基础设计模式，定义了Web页面中的元素师如何看做盒子来解析的。

CSS中的每一个元素都是一个盒模型。网页设计中常听的属性名：content、padding、border、margin， CSS盒子模式都具备这些属性。这些属性我们可以用日常生活中的常见事物——盒子作一个比喻来理解，所以叫它盒子模式。

CSS盒子模型就是在网页设计中经常用到的CSS技术所使用的一种思维模型。

### box-sizing属性

Web前端设计师在制作布局效果时，常会因为给元素添加内距或边框二打破容器，破坏整个页面的布局。为了结局这个问题，CSS3添加了一个盒模型属性box-sizing，能够实现定义盒模型的解析方式，有content-box，border-box，inherit属性值。inherit：此值使用元素继承父元素的盒模型模式。

box-sizing属性主要用来控制元素的盒模型的解析模式，主要目的是控制元素的总宽度。有content-box和border-box属性值，content-box属性值内盒尺寸为：元素width/height=内容宽度/高度+padding+border+margin **内盒尺寸会发生变化** ；border-box内盒尺寸为：元素width/height=内容宽度/高度（包含了border和padding）**内盒尺寸不会发生变化** 。



