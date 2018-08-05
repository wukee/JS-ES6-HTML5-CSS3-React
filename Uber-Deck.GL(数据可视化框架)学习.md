# Deck.GL总结

# 简述

deck.gl是由uber开发并开源出来的基于WebGL的大数据量可视化框架。它具有提供不同类型可视化图层，GPU渲染的高性能，React和Mapbox GL集成，结合地理信息数据（GPS）的特点。deck.gl是根据功能性的UI编程原则设计的，通过React等框架进行设计。

>现在，无论你在做什么，都是由数据来驱动。在Uber，我们喜欢观察数据流动以便真正理解它。现在，任何拥有大数据集的人都可以在网络上做同样的事情。
>
>今天，我们开源了[deck.gl](http://uber.github.io/deck.gl/)，这是一个WebGL驱动的框架，专门用于大规模探索和可视化数据集。deck.gl让我们不经妥协就能可视化。

# **数据快速可视化**

虽然deck.gl的架构适合抽象和科学的可视化需求，在Uber，地图相关数据是最大的资产。在第一次发布之前，我们在许多不同的绘图环境中扩展和测试了deck.gl。

>在Uber，我们要处理许多公司每天传来的服务请求的GPS点。如果平台有问题，我们就可以通过探索历史地理位置数据进行诊断。如果在路上有意外，我们可以根据给定行程的GPS轨迹来获知来龙去脉。如果在城市中点取的位置点周围有“疼痛点”，我们可以通过可视化的方式，将计划传达给市政当局。我们要将这些数据变为基于网络、实时和可共享，如此一来，Uber的其他团队也可以使用。为满足这些需求，我们开发了[deck.gl](http://deck.gl/)。

**deck.gl为用户专注于以下关键方面：**

- **性能：**基于最新的WebGL技术，获得大数据集（数百万点或顶点）的高性能呈现，包括动态聚合和视觉探索等功能。
- **精度：**多亏我们定制的fp64数学库，在GPU上实现了高精度数值计算。据我们所知，当前基于WebGL的其他库并没有提供此功能，而该功能对地理数据集的完全交互至关重要。
- **可扩展性：**使用最新的编码标准，包括[ES2016](http://javascriptplayground.com/blog/2016/02/es2016-and-beyond/)，丰富的库生态系统，以及能够轻松地调试和分析WebGL应用程序的设置。

# **deck.gl提供什么样的绘图用例**

[deck.gl](http://deck.gl/)的特性集适用于广泛的用例，包括绘图。作为示例，deck.gl可以与MapboxGL的相机系统结合使用，因此数据可以显示在Mapbox地图的顶部并且以透视模式可视化（这是可选的）。用户还可以使用deck.gl的一组核心图层启动任何数据可视化项目，包括散点图、线、弧、等值线图和网格图层。也可以选择连接到其他第三方库，如流行的开源框架[react-map-gl](http://github.com/uber/react-map-gl)，一种MapboxGL JavaScript API的弱反应包装器。

为便于演示，我们开发了一组绘图用例的简单[示例](http://uber.github.io/deck.gl/#/examples/overview)。通过这个[演示](http://uber.github.io/deck.gl/#/examples/trip-routes)，窥探deck.gl与大数据集的性能：200万点和36000出租车在纽约城的出行的实时GPU插值。

![img](https://www.linuxidc.com/upload/2016_11/161121085059331.png)

我们还开发了可视化3D建筑结构、街道、点云数据等图层，将在未来版本中予以开源。让我们来深入了解deck.gl背后的一些设计和架构的决策。

## **实例存储分层**

通过组合实例和图层，deck.gl使复杂的可视化成为可能，而不会导致计算机崩溃。如果你过去曾经使用[D3可视化](https://github.com/d3/d3/wiki/Gallery)，那么你已经熟悉了[实例化](http://blog.tojicode.com/2013/07/webgl-instancing-with.html)的概念。实例化是渲染单个对象的多个副本时，在副本之间几乎没有调整。最终，你看起来是不同的对象，但由于[WebGL API的工作原理](http://blog.tojicode.com/2013/09/whats-coming-in-webgl-20.html)，所有这些显示都不很耗费资源。例如，要创建散点图，需要有圆形元素，并根据数据中每行的值对这些圆的半径、位置和颜色修改并应用。

![img](https://www.linuxidc.com/upload/2016_11/161121085059332.png)

为利用这种实例化特征，deck.gl具有覆盖不同数据集（使用[混合模式、剪切](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Compositing)等）的分层系统。用户可以在一张大型图片中推理出具备清晰语义分离的不同类型的数据，并根据需要添加和删除图层。例如，普通的Uber deck.gl应用可以包括拾取、放弃、请求、高度、3D建筑物和点云数据的层，因为几何图元都是副本，所以这些都以高性能来渲染。

分层还可以创建计算，如分组和聚合。这有助于创建人口密度、中值ETA等的即时热图。[该示例](http://uber.github.io/deck.gl/#/examples/screen-grid-layer)显示了网格中的动态聚合。计算是实时执行的，因此，粒度随缩放级别而变化。

![img](https://www.linuxidc.com/upload/2016_11/161121085059333.png)

## **高精度GPU计算**

>deck.gl有一个我们引以为傲的地方，就是它在GPU上处理高精度变换和其他数值计算的能力。WebGL和许多其他图形库，如苹果的Metal只支持32位单精度浮点数。WebGL对许多支持平台上的数值精度特别宽松。

由于deck.gl旨在提供高动态范围（HDR）、科学级数据的精度和性能，为了在所有支持WebGL 1.0的平台模拟64位的双精度浮点数，我们实现了强大的扩展。由于尾数中的有效数字（46位）的两倍，使得仿真高精度数据类型能够呈现GPU永远不能处理的图元。这点极为有用：以厘米级别呈现指定的地理要素的经纬度，或者呈现从城市级到地图的交叉点级别的交互式数据密集可视化。

大多数其他处理高缩放级别的库使用不同的坐标系统（例如[UTM](https://en.wikipedia.org/wiki/Universal_Transverse_Mercator_coordinate_system)）动态范围的精度，或执行基于CPU的计算以与整体地图对准的性能精度。通过在这种高精度类型的浮点数中做所有的数学运算，我们能够将所有计算移到GPU，同时获得准确性、性能和交互性。此[示例](http://uber.github.io/deck.gl/#/documentation/advanced-topics/64-layers)展示高精度GPU浮点运算。

![img](https://www.linuxidc.com/upload/2016_11/161121085059334.png)

## **使用最新编码标准**

为了尽可能与我们相似的其他用户相关，我们构建了deck.gl。因此，deck.gl使用最新的JavaScript编码标准，通过Babel移植支持ES6（ES2015）和ES7（ES2016）的类和其他概念。它包装为一个[npm](https://www.npmjs.com/package/deck.gl)模块，并与标准JavaScript一起打包，如如Browserify和webpack兼容。

为了使deck.gl易于使用，我们创建了一个名为[luma.gl](http://github.com/uber/luma.gl)的配套实用程序库，它使用与deck.gl相同的编码和设计约定。luma.gl包含以下内容：

- 最新的JavaScript编码标准，包括ES2016；
- 来自WebGL 2.0标准的良好支持的功能，如WebGL1应用程序中的实例化数组；
- 公开WebGL 2.0功能（如 转换反馈）的类，使用户能够在支持的浏览器上进行实验；*
- 高级调试、跟踪、错误检查和检查缓冲区和内存的工具，以简化WebGL应用程序的调试（这个调试过程原本非常困难）；
- 具有GPU64位浮点仿真封装包的着色器库，经过测试，它在大多数的GPU驱动程序上能够工作（fp64库在deck.gl中用于创建高精度图层）。

它将很快允许使用WebGL来运行计算着色器进行通用计算。

## **与React和Mapbox的互操作性**

使用由React推广的响应式编程模型原则构建了deck.gl，并与Mapbox的摄像机系统进行了全面的互操作。因此，透视模式和对齐方式为地图应用程序提供了开箱即用的功能。[此示例](http://uber.github.io/deck.gl/#/examples/arc-layer)在Mapbox中显示透视模式，并使用deck.gl中的核心弧层。它显示了美国的县级人口流动。用`Shift+拖放`可以改变地图的透视。

![img](https://www.linuxidc.com/upload/2016_11/161121085059335.png)