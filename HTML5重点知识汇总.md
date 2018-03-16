# HTML5重点知识汇总

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

所谓语义化标签就是一种我们仅通过标签名就能判断出该标签内容的语义的标签。引入语义化标签的好处主要有下列两点：

- 比`<div>`标签有更加丰富的含义，方便开发与维护
- 搜索引擎能更方便的识别页面的每个部分

![html5-layout](C:\Users\Administrator\Desktop\html5-layout.jpg)

## 2. HTML5新增标签与废除标签有哪些？

### 新增的标签（部分）

- 新增的结构元素：section、article、aside、header、footer、nav、figure等
- 新增的主要媒体元素与绘图元素：video、audio、details、canvas等
- 新增的input元素类型：email、url、number、range、DatePicker等

### 废除的标签（部分）

- 能使用CSS替代的元素：basefont、big、center、font、s、tt、u等
- 不在使用frame框架
- 只有部分浏览器支持的元素

## 3. 新增全局属性

- contentEditable：规定是否允许用户编辑内容

- designMode：制定整个页面是否可编辑，可编辑时支持contentEditable属性都变为可编辑状态

- hidden：规定该元素是无关的。被隐藏的元素不会显示

- spellcheck：规定是否必须对元素进行拼写或语法检查

- tabindex：规定元素的 tab 键控制次序。

  ​