# ES6知识点汇总

## 1. ECMAScript 和 JavaScript 的关系

ECMAScript 和 JavaScript 的关系是，前者是后者的规格，后者是前者的一种实现（另外的 ECMAScript 方言还有 Jscript 和 ActionScript）。日常场合，这两个词是可以互换的。

## 2. let const的优点

### let命令

- let 声明的变量只在它所在的代码块有效。


- let 命令改变了语法行为，它所声明的变量一定要在声明后使用，否则报错。**不存在变量提升** 。


- ES6 明确规定，如果区块中存在 let 和 const 命令，这个区块对这些命令声明的变量，从一开始就形成了封闭作用域。凡是在声明之前就使用这些变量，就会报错。


- 在代码块内，使用 let 命令声明变量之前，该变量都是不可用的。这在语法上，称为**“暂时性死区”**

### const命令

- const 声明一个只读的常量。一旦声明就必须立即初始化，只声明不赋值就会报错，且常量的值就不能改变。


- const 的作用域与 let 命令相同：只在声明所在的块级作用域内有效。


- const 命令声明的常量也是不提升，同样存在暂时性死区，只能在声明的位置后面使用。


- const 声明的常量，也与 let 一样不可重复声明。
- **const 实际上保证的，并不是变量的值不得改动，而是变量指向的那个内存地址不得改动。** 

ES6 规定暂时性死区和 let 、 const 语句不出现变量提升，主要是为了减少运行时错误，防止在变量声明前就使用这个变量，从而导致意料之外的行为。这样的错误在 ES5 是很常见的，现在有了这种规定，避免此类错误就很容易了。

## 3.  ES6 新特性有哪些？区分ES6和 ES5如何区分？

### 区分ES6和 ES5

```
ES6 比 ES5 增加了很多特殊的方法，如果你遇到了这些特殊的方法，你就可以确定它是 ES6。
如果你的代码中没有引用这些特殊的方法，那我们就可以认为他是 ES5 的。
所以前提你需要了解 ES6 的语法才能做判断，高频使用的特性有箭头函数、解构赋值、let、const。
```

### 块级作用域

- let 实际上为 JavaScript 新增了块级作用域，使得外层代码块不受内层代码块的影响。


- ES6 允许块级作用域的任意嵌套。但外层作用域无法读取内层作用域的变量。
- 内层作用域可以定义外层作用域的同名变量。
- 块级作用域的出现，实际上使得获得广泛应用的**立即执行函数** 表达式（IIFE）不再必要了。


```javascript
// IIFE 写法  立即执行函数：避免创建全局变量，执行完立即销毁
(function () {
var tmp = ...;
...
}());
// 块级作用域写法
{
let tmp = ...;
...
}
```

ES6 引入了块级作用域，明确允许在块级作用域之中声明函数。ES6 规定，块级作用域之中，函数声明语句的行为类似于 let ，在块级作用域之外不可引用。

### do 表达式

本质上，块级作用域是一个语句，将多个操作封装在一起，没有返回值。

现在有一个提案，使得块级作用域可以变为表达式，也就是说可以返回值：在块级作用域之前加上 do ，
使它变为 do 表达式，然后就会返回内部最后执行的表达式的值。

```javascript
let x = do {
let t = f();
t * t + 1;
};
//变量 x 会得到整个块级作用域的返回值（ t * t + 1 ）
```

### ES6 声明变量的六种方法

ES5 只有两种声明变量的方法： var 命令和 function 命令。ES6 除了添加 let 和 const 命令，还有 import 命令和 class 命令。所以，ES6 一共有 6 种声明变量的方法。

### 变量的解构赋值

- 数组的解构赋值

ES6 允许按照一定模式，从数组和对象中提取值，对变量进行赋值，这被称为解构（Destructuring）。

```javascript
//ES6 允许写成下面这样:
let [a, b, c] = [1, 2, 3];
//可以从数组中提取值，按照对应位置，对变量赋值。

let [head, ...tail] = [1, 2, 3, 4]; 
head // 1
tail // [2, 3, 4]

let [x, y, ...z] = ['a'];
x // "a"
y // undefined
z // []
//如果解构失败变量的值就等于underfined	
```

本质上，这种写法属于“模式匹配”，只要等号两边的模式相同，左边的变量就会被赋予对应的值。

- 对象的结构赋值

对象的解构与数组有一个重要的不同。数组的元素是按次序排列的，变量的取值由它的位置决定；而对象的属性没有次序，变量必须与属性同名，才能取到正确的值。

**【特别注意】对象的解构赋值的内部机制，是先找到同名属性，然后再赋给对应的变量**。

```javascript
let { foo: baz } = { foo: "aaa", bar: "bbb" };
baz // "aaa"
foo // error: foo is not defined
```

上面代码中， foo 是匹配的模式，foo先和右边的对象匹配，然后再把匹配到的值赋给 baz，所以baz 才是变量。真正被赋值的是变量 baz ，而不是模式 foo 。

对象的解构也可以指定默认值。默认值生效的条件是，对象的属性值严格等于 undefined 。

```javascript
var {x = 3} = {x: undefined};
x // 3
var {x = 3} = {x: null};
x // null, x 属性等于 null ，就不严格相等于 undefined ，导致默认值不会生效。

let {foo} = {bar: 'baz'};
foo // undefined
//如果解构失败，变量的值等于 undefined 。
```

- 字符串也可以解构赋值。这是因为此时，字符串被转换成了一个类似数组的对象。

```javascript
let {length : len} = 'hello';
len // 5
//类似数组的对象都有一个 length 属性，因此还可以对这个属性解构赋值。
```

**解构赋值的规则是，只要等号右边的值不是对象或数组，就先将其转为对象。**由于 undefined 和 null 无法转为对象，所以对它们进行解构赋值，都会报错。

---

#### 解构赋值的用途

（1）交换变量的值

```javascript
let x = 1;
let y = 2;
[x, y] = [y, x]; //交换变量x和y的值，这样的写法不仅简洁，而且易读，语义非常清晰。
```

（2）从函数返回多个值

```javascript
// 返回一个数组
function example() {
return [1, 2, 3];
} l
et [a, b, c] = example();
// 返回一个对象
function example() {
return {
foo: 1,
bar: 2
 };
}
let { foo, bar } = example();
//函数只能返回一个值，如果要返回多个值，只能将它们放在数组或对象里返回。有了解构赋值，取出这些值就非常方便。
```

（3）函数参数的定义

```javascript
// 参数是一组有次序的值
function f([x, y, z]) { ... }
f([1, 2, 3]);
// 参数是一组无次序的值
function f({x, y, z}) { ... }
f({z: 3, y: 2, x: 1});
//解构赋值可以方便地将一组参数与变量名对应起来。
```

（4）提取 JSON 数据

```javascript
let jsonData = {
id: 42,
status: "OK",
data: [867, 5309]
};
let { id, status, data: number } = jsonData;
console.log(id, status, number);
// 42, "OK", [867, 5309]
//解构赋值可以快速提取 JSON 数据的值。
```

（5）遍历 Map 结构

任何部署了 Iterator 接口的对象，都可以用 for...of 循环遍历。Map 结构原生支持 Iterator 接口，配合变量的解构赋值，获取键名和键值就非常方便。

```javascript
const map = new Map();
map.set('first', 'hello');
map.set('second', 'world');
for (let [key, value] of map) {
console.log(key + " is " + value);
} 
// first is hello
// second is world
```

如果只想获取键名，或者只想获取键值，可以写成下面这样。

```javascript
// 获取键名
for (let [key] of map) {
// ...
} 
// 获取键值
for (let [,value] of map) {
// ...
}
```

### 模板字符串

模板字符串（template string）是增强版的字符串，用反引号（``）标识。它可以当作普通字符串使用，也可
以用来定义多行字符串，或者在字符串中嵌入变量。

```javascript
function authorize(user, action) {
if (!user.hasPrivilege(action)) {
throw new Error(
// 传统写法为
// 'User '
// + user.name
// + ' is not authorized to do '
// + action
// + '.'
`User ${user.name} is not authorized to do ${action}.`);
}
}

let greeting = `\`Yo\` World!`;//如果在模板字符串中需要使用反引号，则前面要用反斜杠转义。

// 如果使用模板字符串表示多行字符串，所有的空格和缩进都会被保留在输出之中。
`In JavaScript this is
not legal.`

//模板字符串调用函数。
function fn() {
return "Hello World";
} 
`foo ${fn()} bar`
// foo Hello World bar
```

### 数值的扩展

####  Number 对象

ES6 在 Number 对象上，新提供了 Number.isFinite() 和 Number.isNaN() 两个方法。

Number.isFinite() 用来检查一个数值是否为有限的（finite）。

Number.isNaN() 用来检查一个值是否为 NaN 。

```javascript
Number.isFinite(15); // true
Number.isFinite(0.8); // true
Number.isNaN(NaN) // true
Number.isNaN(15) // false
```

它们与传统的全局方法 isFinite() 和 isNaN() 的区别在于，传统方法先调用 Number() 将非数值的值转为数值，
再进行判断，而这两个新方法**只对数值有效**， Number.isFinite() 对于非数值一律返回 false , Number.isNaN()
只有对于 NaN 才返回 true ，非 NaN 一律返回 false 。

ES6 将全局方法 parseInt() 和 parseFloat() ，移植到 Number 对象上面，行为完全保持不变。

```javascript
// ES5的写法
parseInt('12.34') // 12
parseFloat('123.45#') // 123.45
// ES6的写法
Number.parseInt('12.34') // 12
Number.parseFloat('123.45#') // 123.45
```

Number.isInteger() 用来判断一个值是否为整数。

ES6 在 Number 对象上面，新增一个极小的常量 Number.EPSILON 。表示 1 与大于 1 的最小浮点数之间的差。Number.EPSILON 的实质是一个可以接受的最小误差范围。

#### Math 对象的扩展

ES6 在 Math 对象上新增了 17 个与数学相关的方法。所有这些方法都是静态方法，只能在 Math 对象上调用。

- **Math.trunc () **用于去除一个数的小数部分，返回整数部分。

````javascript
Math.trunc(4.1) // 4
Math.trunc(true) //1  对于非数值， Math.trunc 内部使用 Number 方法将其先转为数值。

//对于空值和无法截取整数的值，返回 NaN 。
Math.trunc(NaN); // NaN
Math.trunc('foo'); // NaN
Math.trunc(); // NaN
Math.trunc(undefined) // NaN
````

- **Math.sign()** 方法用来判断一个数到底是正数、负数、还是零。对于非数值，会先将其转换为数值。

```javascript
Math.sign(‐5) // ‐1    参数为负数，返回 -1 ；
Math.sign(5) // +1     参数为正数，返回 +1 ；
Math.sign(0) // +0     参数为 0，返回 0 ；
Math.sign(‐0) // ‐0    参数为-0，返回 -0 ;
Math.sign(NaN) // NaN  其他值，返回 NaN 。
```

- **Math.cbrt ()** 方法用于计算一个数的立方根。
- **Math.hypot()** 方法返回所有参数的平方和的平方根。

#### 指数运算符

ES2016 新增了一个指数运算符（ `*…* `）。

```javascript
2 ** 2 // 4
2 ** 3 // 8
//指数运算符可以与等号结合，形成一个新的赋值运算符（ **= ）。
let b = 4;
b **= 3;
// 等同于 b = b * b * b;
```

### 函数的扩展

#### 函数参数的默认值

ES6 允许为函数的参数设置默认值，即直接写在参数定义的后面。

```javascript
function foo(x = 5) {
}
```

参数默认值可以与解构赋值的默认值，结合起来使用。

```javascript
// 写法一:函数参数的默认值是空对象，但是设置了对象解构赋值的默认值
function m1({x = 0, y = 0} = {}) {
return [x, y];
}
// 写法二:函数参数的默认值是一个有具体属性的对象，但是没有设置对象解构赋值的默认值。
function m2({x, y} = { x: 0, y: 0 }) {
return [x, y];
}
```

通常情况下，定义了默认值的参数，应该是函数的尾参数。因为这样比较容易看出来到底省略了哪些参数。如果
**非尾部的参数设置默认值**，实际上这个参数是没法省略的。

```javascript
function f(x, y = 5, z) {
return [x, y, z];
}
f() // [undefined, 5, undefined]
f(1) // [1, 5, undefined]
f(1, ,2) // 报错，传参时不能省略该参数
f(1, undefined, 2) // [1, 5, 2]
```

指定了默认值以后，函数的 length 属性，将返回没有指定默认值的参数个数。如果设置了默认值的参数不是尾参数，那么 length 属性也不再计入后面的参数了。

```javascript
(function (a, b, c = 5) {}).length // 2
(function (a, b = 1, c) {}).length // 1, length 属性不再计入后面的参数了
```

一旦设置了参数的默认值，函数进行声明初始化时，参数会形成一个**单独的作用域**（context）。等到初始化结束，这个作用域就会消失。这种语法行为，在不设置参数默认值时，是不会出现的。

```javascript
let x = 1;  //如果没有此处定义，y=x时会形成暂时性死区，导致报错
function f(y = x) {
let x = 2;  //函数调用时，函数体内部的局部变量 x 影响不到默认值变量 x 。
console.log(y);
}
f() // 1，函数 f 调用时，参数 y = x 形成一个单独的作用域。这个作用域里面，变量 x 本身没有定义，所以指向外层的全局变量 x 。
```

#### rest 参数

ES6 引入 rest 参数（形式为 `...变量名` ），用于获取函数的多余参数，这样就不需要使用 arguments 对象了。rest参数搭配的变量是一个数组，该变量将多余的参数放入数组中。

### 箭头函数

ES6 允许使用“箭头”（` => `）定义函数。

```javascript
var f = () => 5;
// 等同于
var f = function () { return 5 };//箭头函数只有一行语句，且不需要返回值的写法

var sum = (num1, num2) => { return num1 + num2; }
//箭头函数的代码块部分多于一条语句，需用{}，并且使用 return 语句返回。

let getTempItem = id => ({ id: id, name: "Temp" });
//箭头函数直接返回一个对象，必须在对象外面加上括号

const numbers = (...nums) => nums;
numbers(1, 2, 3, 4, 5)
// [1,2,3,4,5]    rest参数与箭头函数结合的例子。
```

箭头函数有几个使用注意点。
（1）函数体内的 this 对象，就是**定义时所在的对象**，而不是指向运行时所在的对象。
（2）不可以当作构造函数，也就是说，不可以使用 new 命令，否则会抛出一个错误。
（3）不可以使用 arguments 对象，该对象在函数体内不存在。如果要用，可以用 rest 参数代替。
（4）不可以使用 yield 命令，因此箭头函数不能用作 Generator 函数。

### 尾调用优化

尾调用（Tail Call）是函数式编程的一个重要概念，指某个函数的最后一步是调用另一个函数。

```javascript
function f(x){
return g(x);
}    //函数 f 的最后一步是调用函数 g ，这就叫尾调用。

//尾调用不一定出现在函数尾部，只要是最后一步操作即可。
function f(x) {
if (x > 0) {
 return m(x)
 } 
return n(x);
}   //函数 m 和 n 都属于尾调用，因为它们都是函数 f 的最后一步操作。
```

尾调用优化即只保留内层函数的调用帧。如果所有函数都是尾调用，那么完全可以做到每次执行时，调用帧只有一项，这将**大大节省内存**。这就是“尾调用优化”的意义。

**注意**: 只有不再用到外层函数的内部变量，内层函数的调用帧才会取代外层函数的调用帧，否则就无法进行“尾调
用优化”。

```javascript
function addOne(a){
  var one = 1;
  function inner(b){
    return b + one;
  } 
return inner(a);
}  //上面的函数不会进行尾调用优化，因为内层函数 inner 用到了外层函数 addOne 的内部变量 one 。
```

### 数组的扩展

扩展运算符（spread）是三个点（` ... `）。它好比 rest 参数的逆运算，将一个数组转为用逗号分隔的参数序列。

```javascript
console.log(...[1, 2, 3])  // 1 2 3

function add(x, y) {
  return x + y;
} 
const numbers = [4, 38];
add(...numbers) // 42  主要用于函数调用
```

由于扩展运算符可以展开数组，所以可以替代数组的 `apply() `方法

```javascript
function f(x, y, z) {
// ...
} 
let args = [0, 1, 2];
f(...args);

// ES6 的写法
let arr1 = [0, 1, 2];
let arr2 = [3, 4, 5];
arr1.push(...arr2);  //通过 push 函数，将一个数组添加到另一个数组的尾部。
```

扩展运算符的应用

```javascript
//(1)复制数组
const a1 = [1, 2];
const a2 = [...a1];   // 写法一
const [...a2] = a1;  // 写法二
//（2）合并数组
var arr1 = ['a', 'b'];
var arr2 = ['c'];
[...arr1, ...arr2]  // [ 'a', 'b', 'c']
//(3)与解构赋值结合
const [first, ...rest] = [1, 2, 3, 4, 5]; 
first // 1    注意：扩展运算符用于数组赋值，只能放在参数的最后一位，否则会报错。
rest // [2, 3, 4, 5]
//(4)将字符串转为真正的数组
[...'hello']   // [ "h", "e", "l", "l", "o" ]
//(5)实现了 Iterator 接口的对象
//（6）Map 和 Set 结构，Generator 函数
let map = new Map([
   [1, 'one'],
   [2, 'two'],
   [3, 'three'],
  ]);
let arr = [...map.keys()]; // [1, 2, 3]
```

**`Array.from`** 方法用于将两类对象转为真正的数组：类似数组的对象和可遍历的对象.

```javascript
let arrayLike = {
    '0': 'a',
    '1': 'b',
    '2': 'c',
    length: 3
 };
let arr2 = Array.from(arrayLike); // ['a', 'b', 'c']
```

**`Array.of`** 方法用于将一组值，转换为数组，这个方法的主要目的，是弥补数组构造函数 Array() 的不足。因为参数个数的不同，会导致 Array() 的行为有差异。

```javascript
Array.of(3, 11, 8) // [3,11,8]
//Array.of 基本上可以用来替代 Array() 或 new Array()，并且不存在由于参数不同而导致的重载。它的行为非常统一。
Array.of() // []
Array.of(undefined) // [undefined]
Array.of(1) // [1]
Array.of(1, 2) // [1, 2]
//ES5
Array() // []
Array(3) // [, , ,]
Array(3, 11, 8) // [3, 11, 8]
//Array 方法没有参数、一个参数、三个参数时，返回结果都不一样。只有当参数个数不少于 2 个时， Array() 才会返回由参数组成的新数组。参数个数只有一个时，实际上是指定数组的长度。
```

### 对象的扩展

#### 属性写法的变化

ES6 允许直接写入变量和函数，作为对象的属性和方法。这样的书写更加简洁。

```javascript
const foo = 'bar';
const baz = {foo};
baz  // {foo: "bar"}， ES6 允许在对象之中，直接写变量。这时，属性名为变量名, 属性值为变量的值。
// 等同于 
const baz = {foo: foo};

const obj = {
  method() {}     //等同于 method: function()…… 
};
```

ES6 允许字面量定义对象时，表达式作为对象的属性名，即把表达式放在方括号内。

```javascript
let obj = {
   [propKey]: true,
   ['a' + 'bc']: 123  //['a' + 'bc']为属性名表达式
};
```

**`Object.is()`** 用来比较两个值是否严格相等，与严格比较运算符（===）的行为基本一致。解决ES5中运算符（==和===）的缺点。

```javascript
//ES5中 "=="会自动转换数据类型，"===" 的 NaN 不等于自身，以及 +0 等于 -0 。
+0 === ‐0 //true
NaN === NaN // false

Object.is(+0, ‐0) // false
Object.is(NaN, NaN) // true
```

#### Object.assign()

**`Object.assign`** 方法用于对象的合并，将源对象（source）的所有可枚举属性，复制到目标对象（target）。

```javascript
const target = { a: 1 ,b:2};
const source1 = { b: 4 };
const source2 = { c: 3 };
Object.assign(target, source1, source2); 
//Object.assign 方法的第一个参数是目标对象，后面的参数都是源对象。有同名属性会覆盖
target // {a:1, b:4, c:3}   

const v1 = 'abc';
const v2 = true;
const v3 = 10;
const obj = Object.assign({}, v1, v2, v3); 
console.log(obj); // { "0": "a", "1": "b", "2": "c" }
//除了字符串会以数组形式，拷贝入目标对象，其他值都不会产生效果。
```

**注意点**

```javascript
//（1）浅拷贝：目标对象拷贝得到的是这个对象的引用。
const obj1 = {a: {b: 1}};
const obj2 = Object.assign({}, obj1);
obj1.a.b = 2;
obj2.a.b // 2 如果源对象某个属性的值是对象，那么目标对象拷贝得到的是这个对象的引用。

//（2）同名属性的替换：一旦遇到同名属性， Object.assign 的处理方法是替换，而不是添加。
onst target = { a: { b: 'c', d: 'e' } }
const source = { a: { b: 'hello' } }
Object.assign(target, source)
// { a: { b: 'hello' } },
//target 对象的 a 属性被 source 对象的 a 属性整个替换掉了，而不会得到{ a: { b: 'hello', d:'e' } } 的结果。需要特别小心。

//（3）数组的处理：会把数组视为对象
Object.assign([1, 2, 3], [4, 5])
// [4, 5, 3],把数组视为属性名为 0、1、2 的对象，因此源数组的 0 号属性 4 覆盖了目标数组的0 号属性 1 。
```

**常见用途**

（1）为对象添加属性;（2）为对象添加方法;（3）克隆对象;（4）合并多个对象;（5）为属性指定默认值

**`Object.setPrototypeOf()`**用来设置一个对象的 prototype 对象，返回参数对象本身

```javascript
let proto = {};
let obj = { x: 10 };
Object.setPrototypeOf(obj, proto);
proto.y = 20;
proto.z = 40;
obj.x // 10
obj.y // 20
obj.z // 40 ,上面代码将 proto 对象设为 obj 对象的原型，所以从 obj 对象可以读取 proto 对象的属性
```

**`Object.getPrototypeOf()`**该方法与 `Object.setPrototypeOf` 方法配套，用于读取一个对象的原型对象。

```javascript
function Rectangle() {
// ...
} 
const rec = new Rectangle();
Object.getPrototypeOf(rec) === Rectangle.prototype // true

//如果参数不是对象，会被自动转为对象。
Object.getPrototypeOf(1) === Number.prototype // true
Object.getPrototypeOf('foo') === String.prototype // true
Object.getPrototypeOf(true) === Boolean.prototype // true
```

### Set 和 Map 数据结构

#### Set

ES6 提供了新的数据结构 Set。它类似于数组，但是成员的值都是唯一的，没有重复的值。

```javascript
const s = new Set([2, 3, 5, 4, 5, 2, 2]);
console.log(s) //Set{2,3,5,4}

//set有自己的属性与方法
//Set.prototype.constructor ：构造函数，默认就是 Set 函数。
s.size;      //4  返回 Set 实例的成员总数。相当于数据的length
//方法
s.add(6);    //Set{2,3,5,4,6}  添加某个值，返回 Set 结构本身。  
s.delete(2); //Set{3,5,4,6}    删除某个值，返回一个布尔值，表示删除是否成功。
s.has(5);    //ture    返回一个布尔值，表示该值是否为 Set 的成员。
s.clear();   //Set{}   清除所有成员，没有返回值。

//Array.from 方法可以将 Set 结构转为数组,并且可以去除数组中的重复成员
const arr1 = [1,2,2,3,3,4,5];
const items = new Set(arr1);
const arr2 = Array.from(items); //[1,2,3,4,5],注意Set不是一个数组，用的时候需转化成数组

//与扩展运算符结合可以去除数组的重复成员
let arr = [3, 5, 2, 2, 5, 5]; 
let arr2 = [...new Set(arr)]; // [3, 5, 2]


```

遍历操作：

- `keys()` ：返回键名的遍历器
- `values()` ：返回键值的遍历器
- `entries()` ：返回**键值对**的遍历器，注意Set机构键名和键值相同
- `forEach() `：使用回调函数遍历每个成员，用于对每个成员执行某种操作，没有返回值。

由于 **Set 结构没有键名**，只有键值（或者说键名和键值是同一个值），所以 keys 方法和 values 方法的行为完全一致。

```javascript
let set = new Set(['red', 'green', 'blue']);
for (let item of set.keys()) {  // 注意：for(let item of set)...,简写默认的是此处的返回值
console.log(item);
} 
// red
// green
// blue

for (let item of set.entries()) {
console.log(item);
}
// ["red", "red"]   返回简键值对的形式
// ["green", "green"]
// ["blue", "blue"]
```

#### Map

ES6 提供了 Map 数据结构，类似于JSON数据，Map 结构提供了“值—值”的对应，是一种更完善的 Hash （键值对的集合）结构实现。为了和for…of循环配合而生。

```javascript
const map = new Map([['a','red'],['b','blue'],['c','green']]) //也可以通过set()方法设置
map.size//3
//设置 set(key, value)，返回整个 Map 结构。
const m = new Map();
m.set('a','apple');   //键是字符串
m.set(262, 'standard') // 键是数值
m.set(undefined, 'nah') // 键是 undefined

//获取 get(key)
m.get(a)  //apple

//has(key) 表示某个键是否在当前 Map 对象之中。返回布尔值
m.has(262) //true, 注意检查的是键名

//delete(key) 删除某个键 返回布尔值
//clear() 清除所有成员，没有返回值。
```

遍历方法和Set一样

- Map 结构原生提供三个遍历器生成函数和一个遍历方法。
- keys() ：返回键名的遍历器。
- values() ：返回键值的遍历器。
- entries() ：返回所有成员的遍历器。
- forEach() ：遍历 Map 的所有成员。

```javascript
const map = new Map([['a','red'],['b','blue'],['c','green']])
for(let name of map){ //是entries()的简写
    console.log(name) // [ 'a', 'red' ] [ 'b', 'blue' ] ['c','green']
}

for(let key of map.keys()){ //只是循环 key
    console.log(key)  // a  b  c
}

for(let key of map.values()){ //只是循环 value
    console.log(key)  // red blue green
}
```

#### `for…in`和`for…of`区别

```javascript
const arr = ['red','blue','green'];
//for…in
for(let i in arr){
    console.log(i) //0 1 2， 循环的是索引值
}    //注意：for…in 不能用于 Set和Map，没有效果

//for…of
for(let i of arr){ //默认替代arr.values()
    console.log(i) //red blue green， 循环的是值
}
//也可以用arr.keys()循环数组的索引
for(let i of arr.keys()){
    console.log(i) //0 1 2， 
}
```

