# Rect-router

1. 介绍

指浏览器中一种处理访问先后关系的机制，简单点说就是允许我们在不同页面之间跳转，然后记录跳转关系，还能够退回去的机制。包含了三个主要部分。一个是**路由历史**，是一种栈的数据结构，通过入栈和出栈的方式记录页面访问过程。第二个是**跳转**，负责在不同页面跳转动作，并可以传递参数。第三个是**事件**，这个事件是用来打开新页面或者退回上个页面时触发的逻辑。

2. 集中常见的Router

- 页面router

  这种router是真正的页面跳转，跳转以后整个页面都会按着新的路径重新加载，回退的时候也是整个页面重新渲染。是最传统的一种路由方式。

- Hash Router（哈希路由）

  这种路由在跳转的时候只有路径的hash值在变化，而页面没有重新加载，只是跳到了当前页面hash指定的状态，后退的时候也跳到上一个hash状态，整个页面不会刷新。是单页应用最早的方法。

- H5 Router

  他在JS history对象里提供了一个新的方法（history API : `pushStatere`、`placeState`和` popstate` 事件)  用来手动的在路由历史推进一个新值，点击浏览器**后退**按钮的时候可以通过H5 Router提供的onpopstate（只处理后退，退栈的时候才触发）事件截获浏览器按钮触发的事件，保证在模拟路由的同时不做页面的跳转。这样才能完成一个单页应用的要求。相对hash路由而言能操作整个路径（可以跳转到新的地址而不刷新页面），它的功能和hash路由是类似的，只不过hash路由操作的是hash，而H5路由既能操作hash也能操作路径，但兼容性差一些。

  ```javascript
  //页面路由写法
  window.location.href = 'http://baidu.com';
  history.back();//退回操作
  
  //hash路由
  window.location ='#hash';
  window.onhashchang = function(){
      consoloe.log('current hash:',window.location.hash)
  }
  
  //H5 路由
  //推进一个状态
  history.pushState('test','title','/path');
  //替换一个状态
  history.replaceState('test','title','/path');//只是替换当前路径，不会增加没有历史记录
  //popstate事件
  window.onpopstate=function(e){
      console.log('h5 router change:',e.state) // #test;e.state取的是hash状态
     //几种常用location对象值
      console.log(window.location.href);//取得是全路径
      console.log(window.location.pathname)
      console.log(window.location.hash)
      console.log(window.location.serch)
  }
  
  
  ```

  
