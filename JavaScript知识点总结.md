# JavaScript知识点总结

[TOC]

## 1、js基本类型和引用类型、null 和undefined区别。

### 基本类型（原始数据类型）&引用类型：

ECMAScript变量包含两种不同类型的值：基本类型值、引用类型值。

- 基本类型值：指的是**保存在栈内存中**的简单数据段。`Number` ，`String` ，`Boolean`  ，`Null`  ,`undefined`。


- 引用类型值：指的是那些**保存在堆内存中**的对象，变量中保存的实际上只是一个指针，这个指针指向内存堆中实际的值。有 `Object`， `Array`，`Date`，`RegExp`，`Function` 。

**两种访问方式：**

1.  基本类型值：按值访问，操作的是他们实际保存的值。
2.  引用类型值：按引用访问，当查询时，我们需要先从栈中读取内存地址，然后再找到保存在堆内存中的值。

**两种变量类型检测：**

1. **Typeof 操作符是检测基本类型**的最佳工具；
2. 如果变量值是null或者对象，typeof将返回“object”；
3. **Instanceof用于检测引用类型**，可以检测到具体的、它是什么类型的实例。
4. 如果变量是给定引用类型的实例，instanceof操作符会返回true；

**两种类型复制：**

1. 基本类型变量的复制：从一个变量向另一个复制时，会在栈中创建一个新值，然后把值复制到为新变量分配的位置上。
2. 引用类型变量的复制：复制的是存储在栈中的指针，将指针复制到栈中为新变量分配的空间中，而这个指针副本和原指针指向存储在堆中的同一个对象，复制操作结束后，两个变量实际上将引用同一个对象，因此改变其中一个，将影响另一个。

### null和undefined的区别  [详情](http://www.ruanyifeng.com/blog/2014/03/undefined-vs-null.html)

- `null` 表示“没有对象”，即该处不应该有值。常用来表示函数企图返回一个不存在的对象。典型的用法是：

  （1）作为函数的参数，表示该函数的参数不是对象

  （2）作为对象原型链的终点。

  ```javascript
  Object.getPrototypeOf(Object.prototype)
  // null
  ```


- `undefined` 表示“缺少值”，就是此处应该有一个值，但是还没有定义。当声明的变量还未被初始化时，变量的默认值为 undefined。典型用法是：

  ```javascript
  var i;
  i // undefined                   （1）变量被声明了，但没有赋值时，就等于undefined。

  function f(x){console.log(x)}
  f() // undefined                 （2) 调用函数时，应该提供的参数没有提供，该参数等于undefined。

  var  o = new Object();
  o.p // undefined                 （3）对象没有赋值的属性，该属性的值为undefined。

  var x = f();
  x // undefined                   （4）函数没有返回值时，默认返回undefined。
  ```

---

## 2、解释一下事件冒泡和事件捕获、DOM0级和DOM2事件区别

事件冒泡和事件捕获分别由**微软**和**网景**公司提出，这两个概念都是为了解决页面中**事件流**（事件发生顺序）的问题。

```javascript
<div id="outer">
    <p id="inner">Click me!</p>
</div>
```

上面的代码当中一个div元素当中有一个p子元素，如果两个元素都有一个click的处理函数，那么我们怎么才能知道哪一个函数会首先被触发呢？

为了解决这个问题微软和网景提出了两种几乎完全相反的概念。

### 事件冒泡  [详细](https://segmentfault.com/a/1190000000749838)

微软提出了名为**事件冒泡**(event bubbling)的事件流。事件冒泡可以形象地比喻为把一颗石头投入水中，泡泡会一直从水底冒出水面。也就是说，<u>**事件会从最内层的元素开始发生，一直向上传播，直到document对象。**</u>

因此上面的例子在事件冒泡的概念下发生click事件的顺序应该是 ***p -> div -> body -> html -> document***

### 事件捕获

网景提出另一种事件流名为**事件捕获**(event capturing)。**<u>与事件冒泡相反，事件会从最外层开始发生，直到最具体的元素。</u>**

上面的例子在事件捕获的概念下发生click事件的顺序应该是 ***document -> html -> body -> div -> p***

### 事件委托  [详细](https://segmentfault.com/a/1190000004447905)

**事件委托**也称**事件代理**,不是自身元素触发的事件而是利用其父级元素来触发事件实现效果，**利用冒泡来实现。**

`事件委托`(`event delegation`)应该也是JS中比较火的一项技术.使用`事件委托技术`能避免对特定的每个节点添加事件监听,相反,事件监听器是被添加在他们的父元素上。

**优点：**

1. 提高性能(`事件委托`中并没有使用循环)
2. 后续添加的节点可以直接拥有事件行为

### DOM0级事件

（DOM0级事件的处理程序，又叫做事件监听器）

**特点：** 

1. 在DOM0级事件中，事件名均是以on开头的（click—>onclick）。 
2. DOM0级事件处理程序是在元素的作用域中运行的，也就是说，在事件处理程序中，this引用就是这个元素对象。 
3. 以这种方式添加的事件处理程序会在事件流的冒泡阶段被处理。 
4. 取消事件冒泡：event.stopPropagation()/event.cancleBubble = true(此方法为IE中)。 
5. 删除事件处理程序，将属性值设为null即可（btn.onclick=null）。 
6. **DOM0级事件不支持事件捕获。** 

**优点：**处理事件程序的传统方式，第四代web浏览器至今，**所有浏览器都支持。** 
**缺点：**一个事件处理程序只能对应一个处理函数，**同时绑定多个事件时，事件会被覆盖**（这是因为`btn.onclick`实际上就像一个指针，在执行第一个事件处理程序时它指向了内存中的一个引用，执行第二个事件处理程序时它又会指向另一个内存的引用，最终会指向最后一个事件处理函数的内存引用。）。

### DOM2级事件

DOM2级事件中规定的事件流同时支持了事件捕获阶段和事件冒泡阶段，并且每当某一事件发生时，都会经过：     ***捕获阶段->处理阶段->冒泡阶段*** ，而作为开发者，我们可以选择事件处理函数在哪一个阶段被调用。

![img](http://files.jb51.net/file_images/article/201210/20121031173236106.jpg)

**特点：** 

1. 存在两个方法，用于处理制定和删除事件处理程序的操作（addEventListener和removeEventListener），

   ```javascript
   element.addEventListener(event, function, useCapture)
   ```

   接受三个参数：第一个参数是需要绑定的事件，第二个参数是触发事件后要执行的函数。而第三个参数默认值**是false，表示在事件冒泡的阶段调用事件处理函数**，**如果参数为true，则表示在事件捕获阶段调用处理函数。**

2. DOM2级事件处理程序也会依附在元素的作用域中运行。 

**优点：**可同时绑定几个事件，且不会 被覆盖； 
**缺点：**不兼容 。

1. IE不支持DOM2级事件，但是有两个类似的方法attachEvent()/detachEvent()。 
2. attachEvent()/detachEvent()只接受两个参数，没有最后一个布尔值，该事件只能发生在冒泡阶段。

---

## 3、如何阻止冒泡？如何阻止默认事件？

**1. event.stopPropagation()方法**

这是阻止事件的冒泡方法，不让事件向documen上蔓延，但是默认事件任然会执行，当你掉用这个方法的时候，如果点击一个连接，这个连接仍然会被打开，

**2. event.preventDefault()方法**

这是阻止默认事件的方法，调用此方法是，连接不会被打开，但是会发生冒泡，冒泡会传递到上一层的父元素；

**3. return false ；**

这个方法比较暴力，**它会同时阻止事件冒泡也会阻止默认事件**；写上此代码，连接不会被打开，事件也不会传递到上一层的父元素；可以理解为return false就等于同时调用了`event.stopPropagation()`和`event.preventDefault()`。

---

## 4、对闭包的理解？什么时候构成闭包？闭包的实现方法？闭包的优缺点？

### **作用域链、垃圾回收**  [详情](https://segmentfault.com/a/1190000009026788)

- **作用域链：**

  内部环境可以通过作用域链访问所有的外部环境，但外部环境不能访问内部环境中的任何变量和函数。每个环境都可以向上搜索作用域链，但任何环境都不能向下搜索作用域链而进入另一个执行环境。


- **垃圾回收原理：**

  (1) javascript中如果一个对象不再被引用，那么这个对象就会被回收。
  (2) 如果两个对象互相引用，而不再被第3者引用，那么这两个互相引用的对象也会被回收


- **闭包：**

  闭包是指有权访问另一个函数作用域中的变量的函数。创建闭包的常见方式，就是在一个函数内部创建另一个函数。个人的理解是：函数中嵌套函数。

  > 闭包是指有权访问另一个函数作用域中的变量的函数。创建闭包的常见方式，就是在一个函数内部创建另一个函数。
  >
  > **闭包的缺点是常驻内存，会增大内存的使用量，使用不当会造成内存泄漏。**
  >
  > 应用闭包主要是为了：设计私有变量和方法。
  >
  > 一般来讲，函数执行完毕后，局部活动对象就会被销毁，内存中仅保存全局作用域，但是闭包的情况有所不同！

### 闭包的特性和使用闭包的好处   [详情](https://segmentfault.com/a/1190000009026788)

闭包有三个特性：

1. 函数嵌套函数
2. 函数内部可以引用外部的参数和变量
3. 参数和变量不会被垃圾回收机制回收

使用闭包的好处：

1. 希望一个变量长期驻扎内存
2. 避免全局变量污染
3. 私有成员变量的存在（**可形成块级作用域**）

**通俗理解：**

**优点：**  解决外部无法获取内部函数的值
**缺点：** 闭包会使得这个变量一直占据内存中。

---

## 5、this有哪些使用场景？跟C/Java中的this有什么区别？如何改变this的值？

**一句话：*<u>当前的方法属于谁，this就指向谁！</u>***  

**函数内部有一个特殊的对象this,this引用的是函数执行的环境对象，也就是说this的值是函数的执行环境对象**

JavaScript 语言之中，一切皆对象，运行环境也是对象，所以函数都是在某个对象之中运行，`this`就是函数运行时所在的对象（环境）。但是 JavaScript 支持运行环境动态切换，也就是说，`this`的指向是动态的，没有办法事先确定到底指向哪个对象。

**如何改变this的值： [阮一峰 this](http://javascript.ruanyifeng.com/oop/this.html)**

1. 由于对象的属性可以赋给另一个对象，所以属性所在的当前对象是可变的，即`this`的指向是可变的。
2. **只要函数被赋给另一个变量，`this`的指向就会变**。

> **this 是 C++ 中的一个关键字，也是一个 const 指针，它指向当前对象，通过它可以访问当前对象的所有成员。**

### 使用场合： 

**（1）全局环境：** 全局环境使用`this`，它指的就是顶层对象`window`。

**（2）构造函数：** 构造函数中的`this`，指的是实例对象。

**（3）对象的方法：** 如果对象的方法里面包含`this`，`this`的指向就是方法运行时所在的对象。该方法赋值给另一个对象，就会改变`this`的指向。

### 使用注意点：

**（1）避免多层 this：**

- 由于`this`的指向是不确定的，所以切勿在函数中包含多层的`this`。可以使用一个变量固定`this`的值，然后内层函数调用这个变量，可以避免this指向问题。
- JavaScript 提供了严格模式，也可以硬性避免这种问题。严格模式下，如果函数内部的`this`指向顶层对象，就会报错。

**（2）避免数组处理方法中的 this**

数组的`map`和`foreach`方法，允许提供一个函数作为参数。这个函数内部不应该使用`this`。

**（3）避免回调函数中的 this**

## 6、绑定 this 的方法 `call`，`apply`，`bind`  [阮一峰 this](http://javascript.ruanyifeng.com/oop/this.html)

1. **`call`方法，可以指定函数内部`this`的指向（即函数执行时所在的作用域），然后在所指定的作用域中，调用该函数。**

   `call`方法的参数，应该是一个对象。如果参数为空、`null`和`undefined`，则默认传入全局对象。

   ```javascript
   var n = 123;
   var obj = { n: 456 };

   function a() {
     console.log(this.n);
   }

   a.call() // 123
   a.call(null) // 123
   a.call(undefined) // 123
   a.call(window) // 123
   a.call(obj) // 456
   a.call(this) //123    call方法指定函数 a 内部的this绑定当前环境（对象），
   ```

2. `apply`方法的作用与`call`方法类似，**唯一的区别就是，它接收一个数组作为函数执行时的参数**

   ```javascript
   function f(x, y){
        console.log(x + y);
   }
   var a=[1,1]
   f.call(null, 1, 1);  // 2  call方法中也可以接受函数的参数，但必须一个个添加，
   f.apply(null, a);    // 2  apply方法可以接受数组作为函数执行时的参数
   ```

   注意：`apply`方法（或者`call`方法）不仅绑定函数执行时所在的对象，**还会立即执行函数**，因此不得不把绑定语句写在一个函数体内。

3. `bind`方法用于将函数体内的`this`绑定到某个对象，然后返回一个新函数。

**总结：**

1. call，apply 都是改变函数执行上下文。
2. call与apply就一个区别就是传入参数的问题。call是一个个传入，apply是以数组的形式传入。
3. 而bind是返回一个函数副本，**它不会执行函数，**需要自己手动执行函数。`apply`方法（或者`call`方法）不仅绑定函数执行时所在的对象，还会立即执行函数。

**使用场和**

1. 当我们使用一个函数需要改变`this`指向的时候才会用到`call``apply``bind`
2. 如果你要传递的参数不多，则可以使用`fn.call(thisObj, arg1, arg2 ...)`
3. 如果你要传递的参数很多，则可以用数组将参数整理好调用`fn.apply(thisObj, [arg1, arg2 ...])`
4. 如果你想生成一个新的函数长期绑定某个函数给某个对象使用，则可以使用`const newFn = fn.bind(thisObj); newFn(arg1, arg2...)`

---

## 7、显式原型和隐式原型，原型链是什么？为什么要有原型链  [详情1](https://segmentfault.com/a/1190000013655817?utm_source=tag-newest) [详情2](https://segmentfault.com/a/1190000013017881)

### (1) `prototype`  (显式原型)

JS中每个函数都可以看成一个对象，而 **`prototype` （显式原型）**就是函数中的其中一个属性。这里要很清楚，原型是函数上面的一个属性，这个属性只有函数对象才能拥有，别的类型是没有prototype属性。**这个prototype的属性值是一个对象（属性的集合，再次强调！） *这个对象就是我们说的原型对象*。默认的只有一个叫做constructor的属性，指向这个函数本身。**

**用途：[详情](https://blog.csdn.net/qq_33488484/article/details/67053742)**

这个原型对象就相当于一个公共的区域当我们去调用一个对象的属性或方法时，它会先去对象自身中寻找,如果找到了则直接使用，如果没找到则去原型对象中寻找，如果原型中有则返回原型中的值，如果原型中没有，则去原型的原型中寻找，找到了则直接使用依次类推。	

注意：Object的原型的原型为null，所以会一直找Object的原型，如果他里面依然没有，则返回undefined

### (2)`__proto__` ( 隐式原型)

`__proto__` 是一个***实例对象拥有的内置属性*** （请注意：prototype是函数的内置属性，`__proto__`是实例对象的内置属性），是JS内部使用**寻找原型链**的属性。

前面说道**构造函数** 上面的 **prototype（原型对象）能够被 通过构造函数而创建的实例化对象所访问**。至于具体怎么访问的细节没有说明。**其实就是通过`__proto__`这个属性作为桥梁进行的联接。**

【 **个人理解：就是说， 构造函数是一个模板，通过 *prototype* 可以往模板里添加属性，然后通过 这个模板生产出（new的方式）了一个产品，这个产品就是一个实例化对象，它带有这个模板通过 *prototype* 添加的所有属性。想了解这个产品出厂时带有什么功能（属性），则可以用 `__proto__` 来访问 出厂时这个模板给它 的属性（就是原型对象里的属性）。**】

实践是检验真理的唯一标准，如下编程：

```javascript
function Person() {  //声明一个构造函数 注意函数名大写
    //有了prototype就不必在构造函数中定义对象实例的信息（prototype把实例信息转移到了构造函数的外部）。  而构造函数就变成了空函数。当然也仍然可以通过构造函数定义实例信息。
    this.age=25; //注意：构造函数创建的实例对象的属性要比prototype创建的属性等级高。实例对象首先会在构造函数中找该属性，如果没有找到才会在prototype中找。
}                          
Person.prototype.name = 'hello';       //将name属性直接添加到Person 的 prototype 属性中
Person.prototype.age = 27;           //将age属性再添加prototype 中，注意：不会覆盖构造函数中的age
Person.prototype.getYear = function () {     //将getYear方法直接添加到Person 的 prototype属性中
    return 2018;
};
/* 可以写成对象字面量的形式，因为 prototype的属性值就是一个对象（属性的集合）
Person.prototype={
     name:'hello',
     getYear:function () {
         return 2018;
    }
 }
 */

var obj1 = new Person();                        //用new的方式 生产一个实例对象 obj1
var obj2 = new Person();                        //用相同构造函数生产处另一个实例对象 obj2         
console.log(obj1.name);   // hello,  实例对象能够访问原型对象（prototype）中的属性
console.log(obj1.age);    //25, 先在构造函数中找age属性，找到后则不会再在原型对象（prototype）中找
console.log(obj1.getYear); //2018,   实例对象能够访问原型对象（prototype）中的方法
console.log(obj1.constructor); // [Function: Person], constructor 属性，指向Fn本身。

obj2.__proto__.age = 27;  //相当于Fn.prototype.age=27
console.log(obj1.age); //27
/用obj2的__proto__添加了一个age属性，结果obj1也能访问到，这是什么？/
//因为只有构造函数才有prototype 属性，而实例对象并没有 prototype 属性，但实例对象有自己__proto__属性，实例对象通过__proto__属性来访问 构造函数的 prototype 属性，即：obj.__proto__ === Person.prototype。所以obj2.__proto__.age===Fn.prototype.age,即往他两共同的构造函数Fn里添加了一个age属性，所以obj1可以放到。
console.log(obj1.__proto__===Person.prototype); //true

```

### (3) 原型链

>ECMAScript中描述了原型链的概念，并将原型链作为实现继承的主要方法。其基本思想是利用原 型让一个引用类型继承另一个引用类型的属性和方法。简单回顾一下**构造函数、原型和实例的关系**:每个构造函数都有一个原型对象，原型对象都包含一个指向构造函数的指针，而实例都包含一个指向原型对象的内部指针（即，`__proto__`）。那么，假如我们让原型对象等于另一个类型的实例，结果会怎么样呢? 显然，此时的 原型对象将包含一个指向另一个原型的指针，相应地，另一个原型中也包含着一个指向另一个构造函数 的指针。假如另一个原型又是另一个类型的实例，那么上述关系依然成立，如此层层递进，就构成了实 例与原型的链条。这就是所谓原型链的基本概念。

## 8、创建对象的多种方式

### (1) 字面量对象

javascript语言级别快速创建对象的实例

```javascript
var obj = {foo: 'foo', bar: 'bar'}; // Object对象字面量
var obj2 = [obj, 'foo', 'bar']; // Array数组字面量
var obj3 = /^[a-zA-Z0-9]$/; // RegExp正则字面量
var obj4 = function(){}; // Function函数字面量
```

### (2) new 构造函数

通过**原生构造函数**，或者**自定义的构造函数**。 使用 `new` 操作符，创建一个对象，并且执行构造函数方法。

```javascript
//四种原生的构造函数
var obj = new Object();
var obj2 = new Array(1000);
var obj3 = new RegExp('^[a-zA-Z0-9]$');
var obj4 = new Function('a', 'b', 'return a + b;');

//自定义构造函数
function Fn() { }                          
Fn.prototype.name = 'hello';               
Fn.prototype.getYear = function () {       
    return 2018;
};
var obj1 = new Fn(); 
```

>**注意：new 一个对象具体做了什么？**
>
>通过关键字new + **函数调用**，就可以创建一个新的对象。被调用的函数被称为构造函数。 根据`高程`中描述，使用 new + **调用函数** 创建一个对象，这种方式会经历以下 4 个步骤:
>
>(1) 创建一个新对象;
>(2) 将构造函数的作用域赋给新对象（因此 this 就指向了这个新对象）;
>(3) 执行构造函数中的代码（为这个新对象添加属性）;
>(4) 返回新对象。



### (3) 函数声明

函数声明创造的对象. 函数属于特殊的对象.

```javascript
function Foo() {}
Foo instanceof Object;
Foo instanceof Function;
```

### (4) Object.create

传入一个对象作为返回对象的原型，创建一个新对象, 并将新对象的原型指向传入的对象中。

```javascript
var foo = {
    'foo': 'foo',
    'bar': 'bar'
};
var o = Object.create(foo); // o.__proto__ = foo
console.log(o.foo); // o.__proto__.foo
```

使用`Object.create(null)` 可以返回一个字典型对象.

```javascript
var o = Object.create(null);
o instanceof Object; // return false;
o.toString(); // Uncaught TypeError
```

## 9、函数的作用域是什么？js 的作用域有几种？

### 作用域：

它是指对某一变量和方法具有访问权限的代码空间, 在JS中, 作用域是在函数中维护的。表示变量或函数起作用的区域，指代了它们在什么样的上下文中执行，亦即上下文执行环境。Javascript的作用域只有两种：**全局作用域和局部作用域**，**局部作用域是按照函数来区分的** ，每个函数就是一个**局部环境。**

### 作用域链：

当代码在一个环境中执行时，会创建变量对象的一个**作用域链（scope chain）**。**作用域链的用途，是保证对执行环境有权访问的所有变量和函数的有序访问。**

```javascript
var color='blue';   //全局环境（window对象）

function changeColor(){     //局部环境
    var anotherColor='red';//用var定义的变量会被分配内存，在作用域整中执行完会立刻被释放（销毁）
    var anotherColor1=color;//这里可以访问color 和本地环境的anotherColor，但不能访问下层的tempColor
    function swapColors(){  //局部环境
        var tempColor1=anotherColor;
        var tempColor2=color;   //这里可以访问 color、anotherColor 和本地环境的tempColor
    }
}
```

**该环境中形成的作用域链：**

![img](http://img.bitscn.com/upimg/allimg/c161216/14QU9B40-44603.jpg)

**局部环境开始时会在自己的变量对象中搜索变量和函数名，如果搜索不到则再搜索上一级作用域链，在作用域链中找到它。**

### ES5中有全局作用域和局部作用域两种（没有块级作用域）

**全局变量**：声明在函数外部的变量（所有没有var直接赋值的变量都属于全局变量）

**局部变量**：声明在函数内部的变量（所有没有var直接赋值的变量都属于全局变量）

**全局作用域**针对于全局变量来说，全局变量在整个上下文都有效只是在没有赋值之前调用，会输出undefin。

**函数作用域**是针对局部变量来说的，在函数中定义的变量在函数外不能获取

---

## 10、实现继承的多种方式和优缺点

### 原型继承

实现方法：是让子原型对象等于父类型的实例，本质是重写原型对象

**缺点: 子类实例共享属性，造成实例间的属性会相互影响，实际中很少用** 

```javascript
function Parent() {
    this.colors=['red','blue','green'];
}
function Child() {
}
Child.prototype=new Parent();        //让原型对象等于另一个类型的实例
var obj=new Child();
obj.colors.push('black');
console.log(obj.colors);   //[ 'red', 'blue', 'green', 'black' ]

var obj2=new Child();     //所有实例都会共享这一个colors属性，造成实例间的属性会相互影响
console.log(obj2.colors);  //[ 'red', 'blue', 'green', 'black' ]
```

### 构造函数继承

实现方法：在子类型构造函数的内部调用超类型构造函数。

缺点: **方法**都在构造函数中定义，因此函数复用就无从谈起，即：父类的**方法**没有被共享，造成内存浪费

```javascript
function Parent() {
    this.name=['wuke'];
    this.fn=function () {
        this.name.push('hello')
    }
}
function Child() {
    //继承了Person，同时还可以传递参数
    Parent.call(this);
    
    //实例属性
    this.age=25;
}
var obj1=new Child();
var obj2=new Child();
 obj1.fn();
console.log(obj1.name,obj2.name); //[ 'wuke', 'hello' ],[ 'wuke' ] 子类实例不会相互影响
console.log(obj1.age);  //25
console.log(obj1.fn===obj2.fn); //false, 实例方法也是独立的，没有共享同一个方法
```

### 组合继承

实现方式：将原型链和构造函数继承结合到一块，思路是使用原型链实现对原型属性和方法的继承，而通过构造函数来继承来实现对实例属性的继承。

缺点: **父类构造函数被调用两次，一次是在创建子类型原型的时候，另一次是在子类型构造函数内部。**子类实例的属性存在两份，造成内存浪费。

```javascript
function Parent() {
    this.name=['wuke'];
}
Person.prototype.fn=function () {
    this.name.push('hello')
}
function Child() {
    Parent.call(this);   //第二次调用Person()
    this.age=25;
}
Child.prototype=new Parent();// 第一次调用Person()继承父类的属性和方法(副作用: 父类的构造函数被调用的                                  多次，且属性也存在两份造成了内存浪费)
var obj1=new Child();
var obj2=new Child();
obj1.fn();
console.log(obj1.name,obj2.name); //[ 'wuke', 'hello' ],[ 'wuke' ] 子类实例不会相互影响
console.log(obj1.age);//25
console.log(obj1.fn===obj2.fn);  //true, 共享了父类的方法
```

### 寄生继承

完美：子类都有各自的实例不会相互影响，且共享了父类的方法

```javascript
function Parent() {
  this.name = ['wuke']
}
Parent.prototype.fn = function() {
  this.name.push('hello')
}
function Child() {
  Parent.call(this) // 生成子类的实例属性(但是不包括父对象的方法)
}
Child.prototype = Object.create(Parent4.prototype) // 该方法会使用指定的原型对象及其属性去创建一个新的对象
var obj1 = new Child()
var obj2 = new Child()
obj1.fn();
console.log(obj1.name, obj2.name) //[ 'wuke', 'hello' ],[ 'wuke' ] 子类实例不会相互影响
console.log(obj1.fn===obj2.fn);  //true, 共享了父类的方法
```

### ES6 class

和寄生继承实现的效果一致

```javascript
class Parent {
  constructor() {
    this.name = ['wuke']
  }
  reName() {
    this.name.push('hello')
  }
}

class Child extends Parent {
  constructor() {
    super()  
  }
}

var obj1 = new Child()
var obj2 = new Child()
obj1.fn();
console.log(obj1.name, obj2.name) //[ 'wuke', 'hello' ],[ 'wuke' ] 子类实例不会相互影响
console.log(obj1.fn===obj2.fn);  //true, 共享了父类的方法
```

**注意 `super()`用法：**

## 11、JS中浅拷贝与深拷贝

**概念：**

- 浅拷贝：拷贝的值为**引用**而非其真实值 


- 深拷贝：拷贝的值为真实值而非引用。当拷贝的元素是对象是，深拷贝相当于会重新创建一个对象，并对对象的值一个一个复制过来，而不是仅仅获得该对象的引用值。

**注意：** 浅拷贝会带来一个很大的问题。就是，如果我复制的值是一个引用地址，那么我通过一个变量去修改这个对象，会导致所有该对象的引用都发生变化。

**浅拷贝** 

```javascript
var m = { a: 10, b: 20 }
var n = m;   //复制的值是一个引用地址
n.a = 15;
console.log(m.a) // 这时m.a的值是15,改变了该对象的值

//m.a会输出15，因为这是浅拷贝，n和m指向的是同一个堆，对象复制只是复制的对象的引用。
```

**深拷贝**

```javascript
var m = { a: 10, b: 20 }
var n = {a:m.a,b:m.b};  //拷贝的是具体的值而非引用
n.a = 15;
console.log(m.a) // 10,

//这时发现 m.a 的值还是10,并没有改变，m对象和n对象是虽然所有的值都是一样的，但是在堆里面，对应的不是同一个了，这个就是深拷贝。深拷贝就是彻底copy一个对象，而不是copy对象的引用
```

浅拷贝只复制指向某个对象的指针，而不复制对象本身，新旧对象还是共享同一块内存。但深拷贝会另外创造一个一模一样的对象，新对象跟原对象不共享内存，修改新对象不会改到原对象。

---

## 12、正则表达式

## 13、变量提升

>**首先 javascript 是一种弱类型、动态的、解释型的脚本语言。**
>
>**弱类型**：类型检查不严格，偏向于容忍隐式类型转换。 
>**强类型**：类型检查严格，偏向于不容忍隐式类型转换。 
>**动态类型**：运行的时候执行类型检查。 
>**静态类型**：编译的时候就知道每个变量的类型。 
>**解释型**：程序不需要编译，程序在运行的时候才翻译成机器语言，每执行一次都要翻译一次，因此效率比较低，但是跨平台性好。 
>**编译型**：程序在执行之前需要一个专门的翻译过程，把程序编译为机器语言的文件，运行时直接使用编译的结果就行了。 
>标记语言：标记语言的存在就是用来被读取(浏览)的，而其本身是没有行为能力的，在标记语言里你会看到<和>这些尖括号，这是用来写出“层次”和”属性”的，换句话说，它是被动的。并不具备与访问者互动的能力。 
>**编程语言**：它是具有逻辑性和行为能力，这是主动的。说通俗一点，它是有思想的。
>
>**脚本语言**：它介于标记语言和编程语言之间，脚本语言不需要编译，可以直接用，由解释器来负责解释。

**js引擎在读取js代码时会进行两个步骤，第一个步骤是解释，第二个步骤是执行。 所谓解释就是会先通篇扫描所有的Js代码，然后把所有声明提升到顶端，第二步是执行，执行就是操作一类的。**

1. 变量提升：把 **变量声明** 提升到当前执行环境的最顶端

   ```javascript
   console.log(a);//输出结果 undefined
   var a=10;

   //相当于
   var a; 
   console.log(a);//由于未赋值 所以输出undefined 
   a=10
   ```

2. 函数声明提升 ：函数声明提升直接把 **整个函数** 提到执行环境的最顶端

   ```javascript
    foo();
       function foo(){
           console.log("aaa");
       }  //结果输出 aaa

   //相当于
   function foo(){
           console.log("aaa");
       }
       foo();
   ```

3. **变量提升只提升函数名 而函数提升会提升整个函数体。**

   ```javascript
   foo();
       var foo = function(){
           console.log("aaa");
       } 
   //运行结果是： foo is not a function   原因：把函数赋给一个变量，还是进行了变量提升。
    
   //相当于
   var foo;
   console.log(foo);      //undefined  因为变量提升后并没有赋值因此输出undefined
   foo();                 //foo is not a function  因为 js解析遇到 foo()时会默认当做函数来解析
   foo = function(){
       console.log("aaa");
   } 
   ```

4. **函数提升在变量提升上面。**

   ```javascript
   console.log(foo);
   var foo=10;
   console.log(foo);  //输出的是函数提升的 foo函数   而不是变量的10 
   function foo(){
       console.log(10);
   }
   console.log(foo);
   // 输出 [Function: foo]  10   10

   //相当于
   function foo(){
           console.log(10);
       }
   var foo;
   console.log(foo);
   foo=10;
   console.log(foo);
   console.log(foo);
   //注意： 函数提升在变量提升上面，第一个console.log(foo);为什么会输出函数体呢？原因在于 var foo; 并未有赋值只是声明，因此他会调用上面的值
   ```

**总之，就是要牢记，函数提升在变量提升之上。** 

---

## 14、指出JS的宿主对象和原生对象的区别，为什么扩展JS内置对象不是好的做法？有哪些内置对象和内置函数？[详情](https://blog.csdn.net/weixin_40387601/article/details/80431670)

### 1、宿主对象和原生对象的区别

1. **原生对象（new后的对象）**

   ECMA-262 把原生对象（native object）定义为 “**独立于宿主环境的 ECMAScript 实现提供的对象**”。包括：

   ```
   Object、Function、Array、String、Boolean、Number、Date、RegExp、Error、EvalError、RangeError、ReferenceError、SyntaxError、TypeError、URIError、ActiveXObject(服务器方面)、Enumerator(集合遍历类)、RegExp（正则表达式）
   ```

   简单来说，原生对象就是 ECMA-262 定义的类（引用类型）

2. **内置对象(不要new  直接引用——只有Math  Global)**

   >ECMA-262 把内置对象（built-in object）定义为“由 ECMAScript 实现提供的、独立于宿主环境的所有对象，在 ECMAScript 程序开始执行时出现”。这意味着开发者不必明确实例化内置对象，它已被实例化了。
   >
   >js中的内部对象包括Array、Boolean、Date、Function、Global、Math、Number、Object、RegExp、String以及各种错误类对象，包括Error、EvalError、RangeError、ReferenceError、SyntaxError和TypeError。
   >
   >其中Global和Math这两个对象又被称为“内置对象”，这两个对象在脚本程序初始化时被创建，不必实例化这两个对象。

   **内置（Build-in）对象与原生（Naitve）对象的区别在于：前者总是在引擎初始化阶段就被创建好的对象，是后者的一个子集；而后者包括了一些在运行过程中动态创建的对象。**

3. **宿主对象(BOM  DOM  &  自定义对象)**

   宿主对象就是执行JS脚本的环境提供的对象，**即浏览器提供的对象，所有的BOM和DOM都是宿主对象。**对于嵌入到网页中的JS来说，其宿主对象就是浏览器提供的对象，所以又称为浏览器对象，如IE、Firefox等浏览器提供的对象。不同的浏览器提供的宿主对象可能不同，即使提供的对象相同，其实现方式也大相径庭！这会带来浏览器兼容问题，增加开发难度。

   浏览器对象有很多，如Window和Document等等。

**总结**

**本地对象，就是那些官方定义好了的对象。内置对象是本地对象的一种，其只包含Global对象和Math对象。而宿主对象则是那些官方未定义，你自己构建的对象加上DOM和BOM对象组成的。**

### 2、为什么扩展JS内置对象不是好的做法？

因为你不知道哪一天浏览器或javascript本身就会实现这个方法，而且和你扩展的实现有不一致的表现。到时候你的javascript代码可能已经在无数个页面中执行了数年，而浏览器的实现导致所有使用扩展原型的代码都崩溃了。

### 3、有哪些内置对象和内置函数[详情](https://blog.csdn.net/weixin_40387601/article/details/80431670)

String对象：字符串对象，提供了对字符串进行操作的属性和方法。

Array对象：数组对象，提供了数组操作方面的属性和方法。

Date对象：日期时间对象，可以获取系统的日期时间信息。

Boolean对象：布尔对象，一个布尔变量就是一个布尔对象。(没有可用的属性和方法)

Number对象：数值对象。一个数值变量就是一个数值对象。

Math对象：数学对象，提供了数学运算方面的属性和方法。

RegExp:正则。