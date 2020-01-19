---
title: let和const命令
date: 2020-01-15 14:24:00
tag: 'ES6'
category: 'ES6'
---
## Let命令
### 基本用法
``` javascript
    var a = [];
    for (var i = 0; i < 10; i++) {
    a[i] = function () {
        console.log(i);
    };
    }
    a[6](); // 10
```
变量i是var命令声明的，在全局范围内都有效，所以全局只有一个变量i。每一次循环，变量i的值都会发生改变，而循环内被赋给数组a的函数内部的console.log(i)，里面的i指向的就是全局的i。也就是说，所有数组a的成员里面的i，指向的都是同一个i，导致运行时输出的是最后一轮的i的值，也就是 10。
``` javascript
var a = [];
for (let i = 0; i < 10; i++) {
  a[i] = function () {
    console.log(i);
  };
}
a[6](); // 6
```
变量i是let声明的，当前的i只在本轮循环有效，所以每一次循环的i其实都是一个新的变量，所以最后输出的是6。
JavaScript 引擎内部会记住上一轮循环的值，初始化本轮的变量i时，就在上一轮循环的基础上进行计算。
```javascript
for (let i = 0; i < 3; i++) {
  let i = 'abc';
  console.log(i);
}
// abc
// abc
// abc
```
### 不存在变量提升
```javascript
// var 的情况
console.log(foo); // 输出undefined
var foo = 2;

// let 的情况
console.log(bar); // 报错ReferenceError
let bar = 2;
```
### 暂时性死区（temporal dead zone，简称 TDZ）
只要块级作用域内存在let命令，它所声明的变量就“绑定”（binding）这个区域，不再受外部的影响。
```javascript
var tmp = 123;

if (true) {
  //TDZ开始
  tmp = 'abc'; // ReferenceError
  console.log(tmp); // ReferenceError

  let tmp; // TDZ结束
  console.log(tmp); // undefined

  tmp = 123;
  console.log(tmp); // 123
}
```
在let命令声明变量tmp之前，都属于变量tmp的“死区”
“暂时性死区”也意味着typeof不再是一个百分之百安全的操作，作为比较，如果一个变量根本没有被声明，使用typeof反而不会报错。
```javascript
typeof x; // ReferenceError
let x;
typeof undeclared_variable // "undefined"
```

```javascript
//隐蔽死区,问题在哪里？？
function bar(x = y, y = 2) {
  return [x, y];
}

bar(); // 报错
```
```javascript
// 不报错
var x = x;
// 报错
let x = x;
// ReferenceError: x is not defined
```
**暂时性死区的本质就是，只要一进入当前作用域，所要使用的变量就已经存在了，但是不可获取，只有等到声明变量的那一行代码出现，才可以获取和使用该变量**

### 不允许重复声明
```javascript
// 报错
function func() {
  let a = 10;
  var a = 1;
}

// 报错
function func() {
  let a = 10;
  let a = 1;
}

----- split -----

function func(arg) {
  let arg;
}
func() // 报错

function func(arg) {
  {
    let arg;
  }
}
func() // 不报错
```
## 块级作用域
### 为什么需要块级作用域？
1. 内层变量可能会覆盖外层变量
2. 用来计数的循环变量泄露为全局变量
### ES6的块级作用域
```javascript
function f1() {
  let n = 5;
  if (true) {
    let n = 10;
  }
  console.log(n); // 5
}

----- split -----

//ES6 允许块级作用域的任意嵌套
{{{{
  {let insane = 'Hello World'}
  console.log(insane); // 报错
}}}};

----- split -----

//内层作用域可以定义外层作用域的同名变量
{{{{
  let insane = 'Hello World';
  {let insane = 'Hello World'}
}}}};

----- split -----

//匿名立即执行函数表达式（匿名 IIFE）不再必要了
// IIFE 写法
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
### 块级作用域与函数声明
ES5 规定，函数只能在顶层作用域和函数作用域之中声明，不能在块级作用域声明。
但是，浏览器没有遵守这个规定，为了兼容以前的旧代码，还是支持在块级作用域之中声明函数，因此下面两种情况实际都能运行，不会报错。
```javascript
// 情况一
if (true) {
  function f() {}
}

// 情况二
try {
  function f() {}
} catch(e) {
  // ...
}
```
ES6 引入了块级作用域，明确允许在块级作用域之中声明函数。
ES6 规定，块级作用域之中，函数声明语句的行为类似于let，在块级作用域之外不可引用。
```javascript
function f() { console.log('I am outside!'); }

(function () {
  if (false) {
    // 重复声明一次函数f
    function f() { console.log('I am inside!'); }
  }

  f();
}());
//I am inside!

----- 在ES5环境中等价于 -----

// ES5 环境
function f() { console.log('I am outside!'); }

(function () {
  function f() { console.log('I am inside!'); }
  if (false) {
  }
  f();
}());
//ES5环境得到：I am inside!

----- 在ES6环境中等价于 -----

// 浏览器的 ES6 环境
function f() { console.log('I am outside!'); }
(function () {
  var f = undefined;
  if (false) {
    function f() { console.log('I am inside!'); }
  }

  f();
}());
// ES6环境下报错：Uncaught TypeError: f is not a function

----- ES5、ES6建议写法 -----
//考虑到环境导致的行为差异太大，应该避免在块级作用域内声明函数。如果确实需要，也应该写成函数表达式，而不是函数声明语句。
// 块级作用域内部的函数声明语句，建议不要使用
{
  let a = 'secret';
  function f() {
    return a;
  }
}

// 块级作用域内部，优先使用函数表达式
{
  let a = 'secret';
  let f = function () {
    return a;
  };
}
```
以下三条规则只对 ES6 的浏览器实现有效：
1. 允许在块级作用域内声明函数。
2. 函数声明类似于var，即会提升到全局作用域或函数作用域的头部。
3. 同时，函数声明还会提升到所在的块级作用域的头部。

#### 注意点
ES6 的块级作用域必须有大括号，如果没有大括号，JavaScript 引擎就认为不存在块级作用域。
```javascript
// 第一种写法，报错
if (true) let x = 1;

// 第二种写法，不报错
if (true) {
  let x = 1;
}
// 不报错
'use strict';
if (true) {
  function f() {}
}

// 报错
'use strict';
if (true)
  function f() {}
```
## const命令
1. const声明一个只读的常量。一旦声明，常量的值就不能改变，改变常量的值会报错。
2. const一旦声明变量，就必须立即初始化，不能留到以后赋值，只声明不赋值，就会报错。
3. 只在声明所在的块级作用域内有效。
4. const命令声明的常量也是不提升，同样存在暂时性死区，只能在声明的位置后面使用。
5. const声明的常量，也与let一样不可重复声明。
6. **本质：const实际上保证的，并不是变量的值不得改动，而是变量指向的那个内存地址所保存的数据不得改动。对于简单类型的数据（数值、字符串、布尔值），值就保存在变量指向的那个内存地址，因此等同于常量。但对于复合类型的数据（主要是对象和数组），变量指向的内存地址，保存的只是一个指向实际数据的指针，const只能保证这个指针是固定的（即总是指向另一个固定的地址），至于它指向的数据结构是不是可变的，就完全不能控制了。**
```javascript
//exg.1 常量foo储存的是一个地址，这个地址指向一个对象。不可变的只是这个地址，即不能把foo指向另一个地址，但对象本身是可变的，所以依然可以为其添加新属性
const foo = {};
// 为 foo 添加一个属性，可以成功
foo.prop = 123;
foo.prop // 123
// 将 foo 指向另一个对象，就会报错
foo = {}; // TypeError: "foo" is read-only

//exg.2 常量a是一个数组，这个数组本身是可写的，但是如果将另一个数组赋值给a，就会报错
const a = [];
a.push('Hello'); // 可执行
a.length = 0;    // 可执行
a = ['Dave'];    // 报错

//exg.3 对象冻结Object.freeze
const foo = Object.freeze({});
// 常规模式时，下面一行不起作用；
// 严格模式时，该行会报错
foo.prop = 123;

//exg.4 对象属性冻结
//将对象本身冻结，对象的属性也应该冻结。下面是一个将对象彻底冻结的函数
var constantize = (obj) => {
  Object.freeze(obj);
  Object.keys(obj).forEach( (key, i) => {
    if ( typeof obj[key] === 'object' ) {
      constantize( obj[key] );
    }
  });
};
```
## ES6声明变量6种方法
1. var
2. function
3. let
4. const
5. import
6. class

## 顶层对象属性
### 顶层对象
在浏览器环境指的是window对象，
在 Node 指的是global对象。
ES5 之中，顶层对象的属性与全局变量是等价的，顶层对象的属性赋值与全局变量的赋值，是同一件事。
```javascript
window.a = 1;
a // 1

a = 2;
window.a // 2
```
**顶层对象的属性与全局变量挂钩，被认为是 JavaScript 语言最大的设计败笔之一。**
### ES5的问题
1. 没法在编译时就报出变量未声明的错误，只有运行时才能知道（因为全局变量可能是顶层对象的属性创造的，而属性的创造是动态的）。
2. 程序员很容易不知不觉地就创建了全局变量（比如打字出错）。
3. 顶层对象的属性是到处可以读写的，这非常不利于模块化编程。
4. window对象有实体含义，指的是浏览器的窗口对象，顶层对象是一个有实体含义的对象，也是不合适的。

### ES6的改变
1. 为了保持兼容性，var命令和function命令声明的全局变量，依旧是顶层对象的属性。
2. let命令、const命令、class命令声明的全局变量，不属于顶层对象的属性。也就是说，从 ES6 开始，全局变量将逐步与顶层对象的属性脱钩。
```javascript
//全局变量a由var命令声明，所以它是顶层对象的属性；全局变量b由let命令声明，所以它不是顶层对象的属性，返回undefined
var a = 1;
// 如果在 Node 的 REPL 环境，可以写成 global.a
// 或者采用通用方法，写成 this.a
window.a // 1

let b = 1;
window.b // undefined
```

## globalThis 对象
1. JavaScript 语言存在一个顶层对象，它提供全局环境（即全局作用域），所有代码都是在这个环境中运行。但是，顶层对象在各种实现里面是不统一的。
- 浏览器里面，顶层对象是window。
- 浏览器和 Web Worker 里面，self也指向顶层对象。
- Node 里面，顶层对象是global，但其他环境都不支持。

2. 同一段代码为了能够在各种环境，都能取到顶层对象，现在一般是使用this变量，但是有局限性。
- 全局环境中，this会返回顶层对象。但是，Node 模块和 ES6 模块中，this返回的是当前模块。
- 函数里面的this，如果函数不是作为对象的方法运行，而是单纯作为函数运行，this会指向顶层对象。但是，严格模式下，这时this会返回undefined。
- 不管是严格模式，还是普通模式，new Function('return this')()，总是会返回全局对象。但是，如果浏览器用了 CSP（Content Security Policy，内容安全策略），那么eval、new Function这些方法都可能无法使用。

3. 取到顶层对象的方法：
```javascript
// 方法一
(typeof window !== 'undefined'
   ? window
   : (typeof process === 'object' &&
      typeof require === 'function' &&
      typeof global === 'object')
     ? global
     : this);

// 方法二
var getGlobal = function () {
  if (typeof self !== 'undefined') { return self; }
  if (typeof window !== 'undefined') { return window; }
  if (typeof global !== 'undefined') { return global; }
  throw new Error('unable to locate global object');
};
```

4. [ES2020](https://github.com/tc39/proposal-global) 在语言标准的层面，引入globalThis作为顶层对象。也就是说，任何环境下，globalThis都是存在的，都可以从它拿到顶层对象，指向全局环境下的this。
垫片库[global-this](https://github.com/ungap/global-this)模拟了这个提案，可以在所有环境拿到globalThis。