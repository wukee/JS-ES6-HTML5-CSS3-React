# Ajax知识点总结

[TOC]

[XMLHttpRequest只用指南](http://www.ruanyifeng.com/blog/2012/09/xmlhttprequest_level_2.html)    [浏览器同源政策及其规避方法](http://www.ruanyifeng.com/blog/2016/04/same-origin-policy.html)  [跨域资源共享 CORS 详解](http://www.ruanyifeng.com/blog/2016/04/cors.html) 

## 1、什么是AJAX?

AJAX是“Asynchronous JavaScript and XML”的缩写。**是一种在无需重新加载整个网页的情况下，能够更新部分网页的技术。** 

Ajax包含下列技术：

- 基于web标准（standards-basedpresentation）XHTML+CSS的表示；

- 使用 DOM（Document ObjectModel）进行动态显示及交互；

- 使用 XML 和 XSLT 进行数据交换及相关操作；

- 使用 XMLHttpRequest 进行异步数据查询、检索；

- 使用 JavaScript 将所有的东西绑定在一起。

## 2、为什么要用ajax：

Ajax应用程序的优势在于：

1. 通过异步模式，提升了用户体验
2. 优化了浏览器和服务器之间的传输，减少不必要的数据往返，减少了带宽占用
3. Ajax引擎在客户端运行，承担了一部分本来由服务器承担的工作，从而减少了大用户量下的服务器负载。

## 3、AJAX最大的特点是什么。

Ajax可以实现动态不刷新（局部刷新）

就是能在不更新整个页面的前提下维护数据。这使得Web应用程序更为迅捷地回应用户动作，并避免了在网络上发送那些没有改变过的信息。

## 4、AJAX都有哪些优点和缺点？

1、最大的一点是页面无刷新，用户的体验非常好。

2、使用异步方式与服务器通信，具有更加迅速的响应能力。

3、可以把以前一些服务器负担的工作转嫁到客户端，利用客户端闲置的能力来处理，减轻服务器和带宽的负担，节约空间和宽带租用成本。并且减轻服务器的负担，ajax的原则是“按需取数据”，可以最大程度的减少冗余请求，和响应对服务器造成的负担。

4、基于标准化的并被广泛支持的技术，不需要下载插件或者小程序。

**ajax的缺点**

1、ajax不支持浏览器back按钮。

2、安全问题 AJAX暴露了与服务器交互的细节。

3、对搜索引擎的支持比较弱。

4、破坏了程序的异常机制。

5、不容易调试。

## 5、请介绍一下XMLHttpRequest对象。

Ajax的核心是JavaScript对象XmlHttpRequest。该对象在Internet Explorer 5中首次引入，它是一种支持异步请求的技术。简而言之，XmlHttpRequest使您可以使用JavaScript向服务器提出请求并处理响应，而不阻塞用户。通过XMLHttpRequest对象，Web开发人员可以在页面加载以后进行页面的局部更新。

## 6、介绍一下XMLHttpRequest对象的常用方法和属性。

**open(“method”,”URL”) 建立对服务器的调用，**

第一个参数是HTTP请求方式一般为GET，POST

第二个参数是请求页面的URL。

第三个参数是一个布尔值，默认true表示异步，false表示同步

​    send()方法，发送具体请求

​    abort()方法，停止当前请求

> readyState的五种状态：
> 0  （未初始化）还没有调用open()方法
> 1   (载入) 已调用send()方法，正在发送请求
> 2   (载入完成）send()方法完成，已收到全部响应内容
> 3   (解析) 正在解析响应内容
> 4   (完成) 响应内容解析完成，可以在客户端调用了

- ​    responseText 属性  服务器的响应，表示为一个串
- ​    reponseXML 属性 服务器的响应，表示为XML
- ​    status   服务器的HTTP状态码，200对应ok  400对应not found

## 7、Ajax主要包含了哪些技术？

Ajax（Asynchronous JavaScript + XML）的定义

基于web标准（standards-based presentation）XHTML+CSS的表示；

使用 DOM（Document Object Model）进行动态显示及交互；

使用 XML 和 XSLT 进行数据交换及相关操作；

使用XMLhttpRequest 进行异步数据查询、检索；

## 8、AJAX应用和传统Web应用有什么不同。

在传统的Javascript编程中，如果想得到服务器端数据库或文件上的信息，或者发送客户端信息到服务器，需要建立一个HTML form然后GET或者POST数据到服务器端。用户需要点击”Submit”按钮来发送或者接受数据信息，然后等待服务器响应请求，页面重新加载。

因为服务器每次都会返回一个新的页面， 所以传统的web应用有可能很慢而且用户交互不友好。

使用AJAX技术， 就可以使Javascript通过XMLHttpRequest对象直接与服务器进行交互。

通过HTTP Request， 一个web页面可以发送一个请求到web服务器并且接受web服务器返回的信息(不用重新加载页面)，展示给用户的还是通一个页面，用户感觉页面刷新，也看不到到Javascript后台进行的发送请求和接受响应。

## 9、AJAX请求总共有多少种回调函数。

Ajax请求总共有八种Callback

- onSuccess
- onFailure
- onUninitialized
- onLoading
- onLoaded
- onInteractive
- onComplete
- onException

## 10.Ajax和javascript的区别。

javascript是一种在浏览器端执行的脚本语言，Ajax是一种创建交互式网页应用的开发技术 ，它是利用了一系列相关的技术其中就包括javascript。

在一般的web开发中，javascript是在浏览器端执行的，我们可以用javascript控制浏览器的行为和内容。

**在 Ajax应用中信息是如何在浏览器和服务器之间传递的**

​      **通过XML数据或者字符串**

## 11、在浏览器端如何得到服务器端响应的XML数据。

​       XMLHttpRequest对象的responseXMl属性

## 12、 XMLHttpRequest对象在IE和Firefox中创建方式有没有不同。

  有，IE中通过new ActiveXObject()得到，Firefox中通过newXMLHttpRequest()得到

## 13、什么是XML

  XML是扩展标记语言，能够用一系列简单的标记描述数据

## 14、XML的解析方式

   常用的用dom解析和sax解析。dom解析是一次性读取xml文件并将其构造为DOM对象供程序使用，优点是操作方便，但是比较耗内存。Sax是按事件驱动的方式解析的，占用内存少，但是编程复杂