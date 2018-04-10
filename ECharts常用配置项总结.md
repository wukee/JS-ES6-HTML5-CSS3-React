# ECharts常用配置项总结       [配置项手册](http://echarts.baidu.com/option.html#title)

[TOC]

## 1. title: {...}

标题组件，包含主标题和副标题。

```javascript
title:{
     text:'dataZoom',    //主标题
     subtext:'招生情况',  //副标题
     itemGap:15,         //主副标题之间的间距
     textStyle:{fontSize:16,fontWeight:'bold'}   //主标题样式
     subtextStyle:{fontSize:16,fontWeight:'bold'}   //副主标题样式
   },
```

## 2. legend: {...}

图例组件，图例组件展现了不同系列的标记(symbol)，颜色和名字。可以通过点击图例控制哪些系列不显示。

```javascript
legend:{
     itemGap:20, //图例每项之间的间隔。横向布局时为水平间隔，纵向布局时为纵向间隔。
     top:10,     //图例组件离容器上侧的距离
     data:['本科生','硕士生','博士生'],//图例的数据数组。数组项通常为一个字符串，每一项代表一个series的 name，图例组件会自动根据对应系列的图形标记（symbol）来绘制自己的颜色和标记
     textStyle:{fontSize:20,fontWeight:'bold'}   //图例的公用文本样式。
     width:'auto',  //整个图例组件的宽度。默认自适应。如果设置则一般与容器宽度相同，
     itemWidth:10  //图例标记的图形宽度。只是标记图形的宽度，文字不变
        },
            
 //注意，data是一个对象数组，如果要设置单独一项的样式，也可以把该项写成配置项对象。此时必须使用 name 属性对应表示系列的 name。
 data: [{
    name: '本科生',  
    icon: 'circle', // 强制设置图形为圆。
    textStyle: { color: 'red'}  // 设置文本为红色
}]
```

## 3. grid: {...}

直角坐标系内绘图网格，单个 grid 内最多可以放置上下两个 X 轴，左右两个 Y 轴。在 ECharts 3 中单个 echarts 实例可以存在任意个 grid 组件。

1. 单个grid

   ```javascript
   grid:{   
      top: 60,             //grid 组件离容器上侧的距离，可以用 y:60 表示。默认60
      bottom: 60,          //grid 组件离容器下侧的距离。默认60
      left: '10%',         //grid 组件离容器左侧的距离，可以用 x:'10%' 表示。默认10%
      right: '10%',        //grid 组件离容器右侧的距离。默认10%
      width: 'auto',       //grid 组件的宽度。默认自适应。左右各距容器10%，则剩下80%。
      height: 'auto',      //grid 组件的高度。默认自适应。
      containLabel:false,  //grid 区域是否包含坐标轴的 axisLabel(刻度标签)。默认false，为false时是                          依据坐标轴线（不包括刻度内容）来对齐的。
    },
   ```

2. 多个grid    [代码示例](http://www.echartsjs.com/gallery/editor.html?c=scatter-anscombe-quartet)

   ```javascript
   grid: [
           {x: '7%', y: '7%', width: '38%', height: '38%'}, //gridIndex:0， x=left，y=top
           {x2: '7%', y: '4%', width: '38%', height: '38%'},//gridIndex:1， x2等同right
           {x: '7%', y2: '7%', width: '38%', height: '38%'},//gridIndex:2， y2等同bottom
           {x2: '7%', y2: '7%', width: '38%', height: '38%'}//gridIndex:3，
       ],
   ```

## 4. xAxis: {...}

直角坐标系 grid 中的 x 轴，一般情况下单个 grid 组件最多只能放上下两个 x 轴，多于两个 x 轴需要通过配置 [offset](http://echarts.baidu.com/option.html#xAxis.offset) 属性防止同个位置多个 x 轴的重叠。

```javascript
xAxis:[{
    gridIndex:0,         //x 轴所在的 grid 的索引，默认位于第一个 grid。
    type: 'category',    //坐标轴类型。'value' 数值轴，适用于连续数据。'category' 类目轴，适用于离散                            的类目数据，为该类型时必须通过 data 设置类目数据。'time' 时间轴，
    name: '年份',        //坐标轴名称
    nameGap: 15,        //坐标轴名称与轴线之间的距离
    position: '',       //x 轴的位置。有'top','bottom'，默认 grid 中的第一个 x 轴在 grid 的下方                              （'bottom'），第二个 x 轴视第一个 x 轴的位置放在另一侧。
    offset: 80,         //X 轴相对于默认位置的偏移，在相同的 position 上有多个 X 轴的时候有用。
    axisLabel:{fontSize:16,fontWeight:'bold'}, //设置坐标轴刻度标签的样式，注意与textStyle区别
    data: ['2016年',"2017年","2018年"]
	},
      
    {
    gridIndex:1,        //x 轴所在的 grid 的索引，默认位于第二个 grid。
    type: 'category',
    data: ["2016年","2017年","2018年"]  //类目数据，在类目轴（type: 'category'）中有效。
  }],
```

## 5. yAxis: {...}

直角坐标系 grid 中的 y 轴，一般情况下单个 grid 组件最多只能放左右两个 y 轴，多于两个 y 轴需要通过配置 `offset` 属性防止同个位置多个 Y 轴的重叠。

[代码示例](http://www.echartsjs.com/gallery/editor.html?c=multiple-y-axis)

```javascript
yAxis:[{
                         //注意一个 grid 有多个y轴情况
    position: 'right',  //可选'left'，'right'，默认 grid 中的第一个 y 轴在 grid 的左侧（'left'），                          第二个 y 轴视第一个 y轴的位置放在另一侧。
    offset: 80,  //在 position: 'right'时，距右边y轴的距离为80
    min:1,
    max:100,    
    //坐标轴刻度最大值。可以设置成特殊值 'dataMax'，此时取数据在该轴上的最大值作为最大刻度。不设置时会自      动计算最大值保证坐标轴刻度的均匀分布。
    type:'value',
    name:'招生人数',   //坐标轴名称
    nameTextStyle:{fontSize:18,fontStyle:'italic',fontWeight:'bold'},  //坐标轴名称的样式
    axisLabel:{fontSize:16,fontWeight:'bold'},
}],
```

## 6. series: {...} 

系列列表。每个系列通过 `type` 决定自己的图表类型  [详细](http://echarts.baidu.com/option.html#series)

```javascript
series: [{
    name: '本科生',  //系列名称，用于tooltip的显示，legend 的图例筛选
    type: 'bar',    //选择使用柱状图
    xAxisIndex:0,   //有多个grid时，选择使用第一个x轴。（其实就是把该系列放到哪个坐标系）
    yAxisIndex:0,   //有多个grid时，选择使用第一个y轴。
    data: [5, 20, 36] //系列中的数据内容数组。数组项通常为具体的数据项，一般通过json数据引入
},
{
    name: '硕士生',
    type: 'line',  //选择使用折线图
    xAxisIndex:1,  //选择使用第二个x轴
    yAxisIndex:1,
    data: [6, 25, 30]
}]
......
```

## 7. dataZoom: {...}

`dataZoom` 组件 用于区域缩放，从而能自由关注细节的数据信息，或者概览数据整体，或者去除离群点的影响。

 [详细](http://echarts.baidu.com/option.html#dataZoom)

```javascript
dataZoom:[
    {
        type:'slider',      //有单独的滑动条，用户在滑动条上进行缩放或漫游。
        xAxisIndex:[0],     //给第一个X轴下加一个slider,不写则默认
        start:0,            //数据窗口范围的起始百分比。范围是：0 ~ 100。表示 0% ~ 100%。
        end:50,             //数据窗口范围的结束百分比。范围是：0 ~ 100。
        bottom:1,           //dataZoom-slider组件离容器下侧的距离。
        textStyle:{fontSize:15,fontWeight:'bold'},//数据窗口两边字体样式
        handleSize:8        //控制手柄的尺寸，
    },
    {
        type:'inside',   //内置于坐标系中，使用户可以在坐标系上通过鼠标拖拽、鼠标滚轮、手指滑动（触屏                          上）来缩放或漫游坐标系。
        xAxisIndex:[0], //给第一个x轴内置
        start:94,
        end:100,
    },
    {
        type:'slider', 
        yAxisIndex:[0],         //给y轴旁添加一个slider
        filterMode:'filter',    //dataZoom 的运行原理是通过 数据过滤 来达到 数据窗口缩放 的效果。数据                                   过滤模式的设置不同，效果也不同,有:filter, weakFilter, empty, none
        width:28,               //滑动条宽度
        height:'80%',           //滑动条高度
        start:1,        
        end:60,
        textStyle:{fontSize:15},  
        handleSize:8,
        right:'6%',             //距离容器右侧距离
    }],
```

