---
title: 读书笔记 - ECMAScript6入门
date: 2019-09-19 08:51:30
updated: 2019-09-23 21:44:03
categories:
  - web前端
tags:
  - ES6
  - ECMAScript 6
  - 阮一峰
---

[TOC]

## 1.ECMAScript 6 简介

### 1.ECMAScript 和 JavaScript 的关系

前者是后者的规格，后者是前者的一种实现（另外的 ECMAScript 方言还有 JScript 和 ActionScript）

### 2.ES6 与 ECMAScript 2015 的关系

### 3.语法提案的批准流程

### 4.ECMAScript 的历史

### 5.部署进度

https://kangax.github.io/compat-table/es6/

### 6.Babel 转码器

### 7.Traceur 转码器

## 2.let 和 const 命令

### 1.let 命令

- 基本用法 所声明的变量，只在`let`命令所在的代码块内有效
- 不存在变量提升
- 暂时性死区
- 不允许重复声明

### 2.块级作用域

### 3.const 命令

- 基本用法 `const`声明一个只读的常量，一旦声明，常量的值就不能改变
- 本质 变量指向的那个内存地址所保存的数据不得改动
- ES6 声明变量的六种方法
  1.  `var`
  2.  `function`
  3.  `let`
  4.  `const`
  5.  `import`
  6.  `class`

### 4.顶层对象的属性

### 5.globalThis 对象

## 3.变量的解构赋值

### 1.数组的解构赋值

### 2.对象的解构赋值

### 3.字符串的解构赋值

### 4.数值和布尔值的解构赋值

### 5.函数参数的解构赋值

### 6.圆括号问题

### 7.用途

## 4.字符串的扩展

### 1.字符串的 Unicode 表示法

### 2.字符串的遍历器接口

### 3.直接输入 U+2028 和 U+2029

### 4.JSON.stringify() 的改造

### 5.模板字符串

模板字符串 ( template string ) 是增强版的字符串，用反引号 ( \` ) 标识
模板字符串中嵌入变量，需要将变量名写在 `${}` 之中

### 6.实例:模板编译

### 7.标签模板

模板字符串紧跟在一个函数名后面

### 8.模板字符串的限制

## 5.字符串的新增方法

### 1.String.fromCodePoint()

### 2.String.raw()

### 3.实例方法: codePonitAt()

### 4.实例方法: normalize()

### 5.实例方法: includes(), startsWith(), endsWith()

### 6.实例方法: repeat()

### 7.实例方法: padStart(), padEnd()

### 8.实例方法: trimStart(), trimEnd()

### 9.实例方法: matchAll()

## 6.正则的扩展

### 1.RegExp 构造函数

### 2.字符串的正则方法

### 3.u 修饰符

### 4.RegExp.prototype.unicode 属性

### 5.y 修饰符

### 6.RegExp.prototype.sticky 属性

### 7.RegExp.prototype.flags 属性

### 8.s 修饰符:dotAll 模式

### 9.后行断言

### 10.Unicode 属性类

### 11.具名组匹配

### 12.String.prototype.matchAll

## 7.数值的扩展

### 1.二进制和八进制表示法

### 2.Number.isFinite(), Number.isNaN()

### 3.Number.parseInt(), Number.parseFloat()

### 4.Number.isInteger()

### 5.Number.EPSILON

一个极小的常量，表示 1 与大于 1 的最小浮点数之间的差

```JavaScript
Number.EPSILON === Math.pow(2, -52)
// true
Number.EPSILON
// 2.220446049250313e-16
Number.EPSILON.toFixed(20)
// "0.00000000000000022204"
```

`Number.EPSILON`实际上是 JavaScript 能够表示的最小精度

### 6.安全整数和 Number.isSafeInteger()

```JavaScript
Number.MAX_SAFE_INTEGER === Math.pow(2, 53) - 1
// true
Number.MAX_SAFE_INTEGER === 9007199254740991
// true

Number.MIN_SAFE_INTEGER === -Number.MAX_SAFE_INTEGER
// true
Number.MIN_SAFE_INTEGER === -9007199254740991
// true
```

### 7.Math 对象的扩展

- Math.trunc()
- Math.sign()
- Math.cbrt()
- Math.clz32()
- Math.imul()
- Math.fround()
- Math.hypot()
- 对数方法
  - Math.expm1()
  - Math.log1p()
  - Math.log10()
  - Math.log2()
- 双曲函数方法
  - Math.sinh(x)
  - Math.cosh(x)
  - Math.tanh(x)
  - Math.asinh(x)
  - Math.acosh(x)
  - Math.atanh(x)

### 8.指数运算符

`**` 右结合

```JavaScript
// 相当于 2 ** (3 ** 2)
2 ** 3 ** 2
// 512
```

## 8.函数的扩展

### 1.函数参数的默认值

参数变量时默认声明的，在函数体中，不能用`let`或`const`再次声明，否则会报错。  
使用参数默认值时，函数不能有同名参数。  
**应用**：指定某一个参数不得省略

```JavaScript
function throwIfMissing() {
  throw new Error('Missing parameter');
}

function foo(mustBeProvided = throwIfMissing()) {
  return mustBeProvided;
}

foo()
// Error: Missing parameter
```

### 2.rest 参数

ES6 引入 rest 参数(形式为`...变量名`)， 用于获取函数的多余参数，这样就不需要使用`arguments`对象了

### 3.严格模式

只要函数使用了默认值、解构赋值、或者扩展运算符，那么函数内部就不能显式地设定为严格模式，否则会报错

### 4. name 属性

### 5.箭头函数

- 基本用法 `=>`
- 使用注意点
  1.  函数体内的`this`对象，就是定义时所在的对象,而不是使用时所在的对象
  2.  不可以当作构造函数，也就是说，不可以使用`new`命令，否则会抛出一个错误
  3.  不可以使用`arguments`对象，该对象在函数体内不存在，如果要用，可以用 rest 参数代替
  4.  不可以使用`yield`命令，因此箭头函数不能用作 Generator 函数

由于箭头函数没有自己的`this`，所以当然也就不能用`call()`、`apply()`、`bind()`这些方法去改变`this`的指向

### 6.尾调用优化

### 7.函数参数的尾逗号

### 8.Function.prototypr.toString()

### 9.catch 命令的参数省略

## 9.数组的扩展

### 1.扩展运算符

- 含义

扩展运算符 ( spread ) 是三个点 ( `...` )， 它好比 rest 参数的逆运算，将一个数组转为用逗号分隔的参数序列

该运算符主要用于函数调用

- 替代函数的 apply 方法
- 扩展运算符的应用
  - (1) 复制数组 (浅拷贝)
  - (2) 合并数组 (浅拷贝)
  - (3) 与结构赋值结合
  - (4) 字符串
  - (5) 实现了 Iterator 接口的对象
  - (6) Map 和 Set 结构，Generator 函数

### 2.Array.from()

`Array.from`方法用于将两类对象转为真正的数组:类似数组的对象 ( array-like object ) 和可遍历 ( iterable ) 的对象 ( 包括 ES6 新增的数据结构 Set 和 Map )

### 3.Array.of()

### 4.数组实例的 copyWithin()

### 5.数组实例的 find() 和 findIndex()

数组实例的`find`方法，用于找出第一个符合条件的数组成员，它的参数是一个回调函数，所有数组成员依次执行该回调函数,直到找出第一个返回值为`true`的成员，然后返回该成员，如果没有符合条件的成员,则返回`undefined`

### 6.数组实例的 fill()

### 7.数组实例的 entries(), keys() 和 values()

### 8.数组实例的 includes()

### 9.数组实例的 flat(), flatMap()

### 10.数组的空位

## 10.对象的扩展

### 1.属性的见解表示法

### 2.属性名表达式

### 3.方法的 name 属性

### 4.属性的可枚举性和遍历

### 5.super 关键字

### 6.对象的扩展运算符

## 11.对象的新增方法

### 1. Object.is()

`Object.is`是部署 "Same-value equality" (同值相等) 算法的方法，用来比较两个值是否严格相等

```JavaScript
+0 === -0 //true
NaN === NaN // false

Object.is(+0, -0) // false
Object.is(NaN, NaN) // true
```

### 2.Object.asign()

- 基本用法 `Object.asign`方法用于对象的合并，将源对象( source ) 的所有可枚举属性，复制到目标对象 ( target )
- `Object.asign`方法的第一个参数是目标对象，后面的参数都是源对象
- 注意点

  - (1) 浅拷贝 `Object.asign`方法实行的是浅拷贝，而不是深拷贝
  - (2) 同名属性的替换
  - (3) 数组的处理 `Object.asign`可以用来处理数组，但是会把数组视为对象
  - (4) 取值函数的处理 `Object.asign`只能进行值的复制，如果要复制的值是一个取值函数，那么将求值后再复制

  ```JavaScript
  const source = {
    get foo() { return 1 }
  };
  const target = {};

  Object.assign(target, source)
  // { foo: 1 }
  ```

- 常见用途
  - (1) 为对象添加属性
  - (2) 为对象添加方法
  - (3) 克隆对象
  - (4) 合并多个对象
  - (5) 为属性指定默认值

### 3.Object.getOwnPropertyDescriptors()

ES2017 引入了`Object.getOwnPropertyDescriptors`方法，返回指定对象的所有自身属性(非继承属性)的描述对象

### 4.**proto**属性，Object.setPrototypeOf()， Object.getPrototypeOf()

- `Object.setPrototypeOf`方法的作用与`__proto__`相同，用来设置一个对象的`prototype`对象，返回参数对象本身
- `Object.getPrototypeOf`方法与`Object.setPrototypeOf`方法配套，用于读取一个对象的原型对象

### 5.Object.keys(), Object.values(), Object.entries()

- `Object.keys`方法返回一个数组，成员是参数对象自身的(不含继承的)所有可遍历(enumerable)属性的键名
- `Object.values`方法返回一个数组，成员是参数对象自身的(不含继承的)所有可遍历(enumerable)属性的键值
- `Object.entries`方法返回一个数组，成员是参数对象自身的（不含继承的）所有可遍历（enumerable）属性的键值对数组

### 6.Object.fromEntries()

`Object.fromEntries`方法是`Object.entries`的逆操作，用于将一个键值对数组转为对象

## 12.Symbol

### 1.概述

`Symbol`表示独一无二的值，是一种类似于字符串的数据类型

```JavaScript
let s = Symbol();

typeof s
// "symbol"
```

Symbol 值不能与其他类型的值进行运算，会报错；但是可以显示转为字符串，也可以转为布尔值，不能转为数值

```JavaScript
let sym = Symbol('My symbol');

String(sym) // 'Symbol(My symbol)'
sym.toString() // 'Symbol(My symbol)'
```

```JavaScript
let sym = Symbol();
Boolean(sym) // true
!sym  // false

if (sym) {
  // ...
}

Number(sym) // TypeError
sym + 2 // TypeError
```

### 2.Symbol.prototype.

ES2019 提供了一个实例属性`description`，直接返回 Symbol 的描述

```JavaScript
const sym = Symbol('foo');

sym.description // "foo"
```

### 3.作为属性名的 Symbol

注意: Symbol 值作为对象属性名时，不能用点运算符

### 4.实例：消除魔术字符串

魔术字符串指的是，在一个代码之中多次出现，与代码形成强耦合的某一个具体的字符串或者数值

```JavaScript
const shapeType = {
  triangle: Symbol()
}
function getArea(shape, options) {
  let area = 0;
  switch (shape) {
    case shapeType.triangle:
      area = .5 * options.width * options.height;
      break;
  }
  return area;
}
getArea(shapeType.triangle, { width: 100, height: 100 });
```

### 5.属性名的遍历

Symbol 作为属性名，该属性不会出现在`for...in`、`for...of`循环中，也不会被`Object.keys()`、`Object.getOwnPropertyNames()`、`JSON.stringify()`返回。但是，它也不是私有属性，有一个`Object.getOwnPropertySymbols`方法，可以获取指定对象的所有 Symbol 属性名  
`Object.getOwnPropertySymbols`方法返回一个数组，成员是当前对象的所有用作属性名的 Symbol 值

### 6.Symbol.for(), Symbol.keyFor()

`Symbol.for()`与`Symbol()`这两种写法，都会生成新的 Symbol。它们的区别是，前者会被登记在全局环境中供搜索，后者不会。  
`Symbol.for()`不会每次调用就返回一个新的 Symbol 值，而是会先检查给定的`key`是否已经存在，如果不存在才会新建一个值。  
`Symbol.keyFor`方法返回一个已登记的 Symbol 类型的`key`

```JavaScript
let s1 = Symbol.for("foo");
Symbol.keyFor(s1) // "foo"

let s2 = Symbol("foo");
Symbol.keyFor(s2) // undefined
```

### 7.实例：模块的 Singleton 模式

Singleton 模式指的是调用一个类，任何时候返回的都是同一个实例。

### 8.内置的 Symbol 值

- `Symbol.hasInstance` 对象的该属性，指向一个内部方法，当其他对象使用`instanceof`运算符，判断是否为该对象的实例时，会调用这个方法
- `Symbol.isConcatSpreadable` 对象的该属性等于一个布尔值，表示该对象用于`Array.prototype.concat()`时，是否可以展开
- `Symbol.species` 对象的该属性，指向一个构造函数，创建衍生对象时，会使用该属性。

  ```JavaScript
  class T1 extends Promise {
  }

  class T2 extends Promise {
    static get [Symbol.species]() {
      return Promise;
    }
  }

  new T1(r => r()).then(v => v) instanceof T1 // true
  new T2(r => r()).then(v => v) instanceof T2 // false
  ```

- `Symbol.match` 对象的该属性，指向一个函数，当执行`str.match(myObject)`时，如果该属性存在，会调用它，返回该方法的返回值
- `Symbol.replace` 对象的该属性，指向一个方法，当该对象被`String.prototype.replace`方法调用时，会返回该方法的返回值
- `Symbol.search`
- `Symbol.split`
- `Symbol.iterator`
- `Symbol.toPrimitive`
- `Symbol.toStringTag`
- `Symbol.unscopables`

## 13.Set 和 Map 数据结构

### 1.Set

- 基本用法 数据结构 Set 类似于数组，但是成员的值都是唯一的
- 向 Set 加入值的时候，不会发生类型转换
- Set 实例属性
  - `Set.prototype.constructor`
  - `Set.prototype.size`
- Set 实例操作方法
  - `Set.prototype.add(value)`
  - `Set.prototype.delete(value)`
  - `Set.prototype.has(value)`
  - `Set.prototype.clear()`
- Set 实例遍历方法 `Set`结构的遍历顺序就是插入顺序
  - `Set.prototype.keys()`
  - `Set.prototype.values()`
  - `Set.prototype.entries()`
  - `Set.prototype.forEach()`
  - 应用
  ```JavaScript
  let a = new Set([1, 2, 3]);
  let b = new Set([4, 3, 2]);

  // 并集
  let union = new Set([...a, ...b]);
  // Set {1, 2, 3, 4}

  // 交集
  let intersect = new Set([...a].filter(x => b.has(x)));
  // set {2, 3}

  // 差集
  let difference = new Set([...a].filter(x => !b.has(x)));
  // Set {1}
  ```

### 2.WeakSet

- WeakSet 的成员只能是对象，而不能是其他类型的值
- WeakSet 中的对象都是弱引用，即垃圾回收机制不考虑 WeakSet 对该对象的引用

### 3.Map

**注意** 只有对同一个对象的引用，Map 结构才将其视为同一个键

```JavaScript
const map = new Map();

map.set(['a'], 555);
map.get(['a']) // undefined
```

- （1）size 属性
- （2）`Map.prototype.set(key,value)`
- （3）`Map.prototype.get(key)`
- （4）`Map.prototype.has(key)`
- （5）`Map.prototype.delete(key)`
- （6）`Map.prototype.clear()`  
  遍历方法
- `Map.prototype.keys()`
- `Map.prototype.values()`
- `Map.prototype.entries()`
- `Map.prototype.forEach()`  
  与其他数据结构的转换
- （1）Map 转为数组
- （2）数组转为 Map
- （3）Map 转为对象
- （4）对象转为 Map
- （5）Map 转为 JSON
- （6）JSON 转为 Map

### 4.WeakMap

- `WeakMap`只接受对象作为键名（`null`除外）
- `WeakMap`的键名所指向的对象，不计入垃圾回收机制
- **应用** DOM 节点作为键名

## 14.Proxy

### 1.概述

Proxy 用于修改某些操作的默认行为，等同于在语言层面做出修改，所以属于一种“元编程”（meta programming）

Proxy 实际上重载了（overload）了点运算符，即用自己的定义覆盖了语言的原始定义

`var proxy = new Proxy(target, handler)`

`new Proxy()`表示生成一个`Proxy`实例，`target`参数表示所要拦截的目标对象，`handler`参数也是一个对象，用来定制拦截行为

**注意** 要使得`Proxy`起作用，必须针对`Proxy`实例进行操作，而不是针对目标对象进行操作

一个技巧是将 Proxy 对象，设置到`object.proxy`属性，从而可以在`object`对象上调用  
`var object = { proxy: new Proxy(target, handler) }`

Proxy 支持的拦截操作,一共 13 种

1. **get(target,propKey,receiver)**
2. **set(target,propKey,value,receiver)**
3. **has(target,propKey)**
4. **deleteProperty(target,propKey)**
5. **ownKeys(target)**
6. **getOwnPropertyDescriptor(target,propkey)**
7. **defineProperty(target,propKey,propDesc)**
8. **preventExtensions(target)**
9. **getPrototypeOf(target)**
10. **isExtensible(target)**
11. **setPrototypeOf(target,proto)**
12. **apply(target,ctx,args)**
13. **construct(target,args)**

### 2.Proxy 实例的方法

如果一个属性不可配置（configurable）且不可写（writable）,则 Proxy 不能修改该属性，否则通过 Proxy 对象访问该属性会报错

```JavaScript
const target = Object.defineProperties({}, {
  foo: {
    value: 123,
    writable: false,
    configurable: false
  },
});

const handler = {
  get(target, propKey) {
    return 'abc';
  }
};

const proxy = new Proxy(target, handler);

proxy.foo
// TypeError: Invariant check failed
```

### 3.Proxy.revocable()

`Proxy.revcoable`方法返回一个可取消的 Proxy 实例

```JavaScript
let target = {};
let handler = {};

let {proxy, revoke} = Proxy.revocable(target, handler);

proxy.foo = 123;
proxy.foo // 123

revoke();
proxy.foo // TypeError: Revoked
```

### 4.this 问题

在 Proxy 代理的情况下，目标对象内部的`this`关键字会指向 Proxy 代理

```JavaScript
const target = {
  m: function () {
    console.log(this === proxy);
  }
};
const handler = {};

const proxy = new Proxy(target, handler);

target.m() // false
proxy.m()  // true
```

### 5.实例：Web 服务的客户端

## 15.Reflect

### 1.概述

- （1）将`Object`对象的一些明显属于语言内部的方法（比如`Object.defineProperty`），放到`Reflect`对象上
- （2）修改某些`Object`方法的返回结果，让其变得合理
- （3）让`Object`操作都变成函数行为
- （4）`Reflect`对象的方法与`Proxy`对象的方法一一对应

### 2.静态方法

`Reflect`对象一共有 13 个静态方法

1. Reflect.apply(target, thisArg, args)

2. Reflect.construct(target, args)

3. Reflect.get(target, name, receiver)

4. Reflect.set(target, name, value, receiver)

5. Reflect.defineProperty(target, name, desc)

6. Reflect.deleteProperty(target, name)

7. Reflect.has(target, name)

8. Reflect.ownKeys(target)

9. Reflect.isExtensible(target)

10. Reflect.preventExtensions(target)

11. Reflect.getOwnPropertyDescriptor(target, name)

12. Reflect.getPrototypeOf(target)

13. Reflect.setPrototypeOf(target, prototype)

### 3.实例：使用 Proxy 实现观察者模式

观察者模式（Observer mode）指的是函数自动观察数据对象，一旦对象有变化，函数会自动执行

```JavaScript
const queuedObservers = new Set();

const observe = fn => queuedObservers.add(fn);
const observable = obj => new Proxy(obj, {set});

function set(target, key, value, receiver) {
  const result = Reflect.set(target, key, value, receiver);
  queuedObservers.forEach(observer => observer());
  return result;
}

const person = observable({
  name: '张三',
  age: 20
});

function print() {
  console.log(`${person.name}, ${person.age}`)
}

observe(print);
person.name = '李四';
// 输出
// 李四, 20
```

## 16.Promise 对象

### 1.Promise 的含义

### 2.基本用法

### 3.Promise.prototype.then()

### 4.Promise.prototype.catch()

### 5.Promise.prototype.finally()

### 6.Promise.all()

### 7.Promise.race()

### 8.Promise.resolve()

### 9.Promise.reject()

### 10.应用

### 11.Promise.try()

## 17.Iterator 和 for...of 循环

### 1.Iterator(遍历器)的概念

作用

1. 为各种数据结构，提供一个统一分、简便的访问接口

2. 使得数据结构的成员能够按某种次序排列

3. 供`for...of`消费

### 2.默认 Iterator 接口

原生具备 Iterator 接口的数据结构如下

- Array
- Map
- Set
- String
- TypedArray
- 函数的 Arguments 对象
- NodeList 对象

下面是通过遍历器实现指针结构的例子

```JavaScript
function Obj(value) {
  this.value = value;
  this.next = null;
}

Obj.prototype[Symbol.iterator] = function() {
  var iterator = { next: next };

  var current = this;

  function next() {
    if (current) {
      var value = current.value;
      current = current.next;
      return { done: false, value: value };
    } else {
      return { done: true };
    }
  }
  return iterator;
}

var one = new Obj(1);
var two = new Obj(2);
var three = new Obj(3);

one.next = two;
two.next = three;

for (var i of one){
  console.log(i); // 1, 2, 3
}
```

### 3.调用 Iterator 接口的场合

1. 解构赋值

2. 扩展运算符

3. yield\*

4. 其他场合 任何接受数组作为参数的场合
   可以覆盖原生的`Symbol.iterator`方法，达到修改遍历器行为的目的

### 4.字符串的 Iterator 接口

### 5.Iterator 接口与 Generator 函数

### 6.遍历器对象的 return(), throw()

`return()`方法的使用场合是，如果`for...of`循环提前退出，就会调用`return`方法
**注意** `return`方法必须返回一个对象

### 7.for...of 循环

遍历所有数据结构的统一方法

遍历数组

```JavaScript
let arr = [3, 5, 7];
arr.foo = 'hello';

for (let i in arr) {
  console.log(i); // "0", "1", "2", "foo"
}

for (let i of arr) {
  console.log(i); //  "3", "5", "7"
}
```

无法使用`break`或`return`命令中途跳出`forEach`循环

## 18.Generator 函数的语法

### 1.简介

Generator 函数是一个状态机，封装了多个内部状态  
Generator 函数会返回一个遍历器对象，是一个遍历器对象生成函数
特征:

1. `function`关键字与函数名之间有一个星号

2. 函数体内部使用`yield`表达式
   调用 Generator 函数，返回一个遍历器对象，代表 Generator 函数的内部指针。以后每次调用遍历器对象的`next`方法，就返回一个有着`value`和`done`两个属性的对象

```JavaScript
function* helloWorldGenerator() {
  yield 'hello';
  yield 'world';
  return 'ending';
}

var hw = helloWorldGenerator();
hw.next()
// { value: 'hello', done: false }

hw.next()
// { value: 'world', done: false }

hw.next()
// { value: 'ending', done: true }

hw.next()
// { value: undefined, done: true }
```

### 2.next 方法的参数

`yield`表达式本身没有返回值，或者说总是返回`undefineed`，`next`方法恩罗带一个参数，该参数就会被当做上一个`yield`表达式的返回值

```JavaScript
function* foo(x) {
  var y = 2 * (yield (x + 1));
  var z = yield (y / 3);
  return (x + y + z);
}

var a = foo(5);
a.next() // Object{value:6, done:false}
a.next() // Object{value:NaN, done:false}
a.next() // Object{value:NaN, done:true}

var b = foo(5);
b.next() // { value:6, done:false }
b.next(12) // { value:8, done:false }
b.next(13) // { value:42, done:true }
```

### 3.for...of 循环

`for...of`循环可以自动遍历 Generator 函数运行时生成的`Iterator`对象，且此时不再需要调用`nest`方法

### 4.Generator.prototype.throw()

Generator 函数返回的遍历器对象，都有一个`throw`方法，可以在函数体外抛出错误，然后在 Generator 函数体内捕获

`throw`方法抛出的错误要被内部捕获，前提示必须至少执行过一次`next`方法

### 5.Generator.prototype.return()

Generator 函数返回的遍历器对象，还有一个`return`方法，可以返回给定的值，并且终结遍历 Generator 函数

如果 Generator 函数内部有`try...finally`代码块，且正在执行`try`代码块，那么`return`方法会推迟到`finally`代码块执行完再执行

### 6.next()、throw()、return() 的共同点

**作用** 让 Generator 函数恢复执行，并且使用不同的语句替换`yield`表达式

### 7.yield\* 表达式

用来在一个 Generator 函数里面执行另一个 Generator 函数

```JavaScript
// 下面是二叉树的构造函数，
// 三个参数分别是左树、当前节点和右树
function Tree(left, label, right) {
  this.left = left;
  this.label = label;
  this.right = right;
}

// 下面是中序（inorder）遍历函数。
// 由于返回的是一个遍历器，所以要用generator函数。
// 函数体内采用递归算法，所以左树和右树要用yield*遍历
function* inorder(t) {
  if (t) {
    yield* inorder(t.left);
    yield t.label;
    yield* inorder(t.right);
  }
}

// 下面生成二叉树
function make(array) {
  // 判断是否为叶节点
  if (array.length == 1) return new Tree(null, array[0], null);
  return new Tree(make(array[0]), array[1], make(array[2]));
}
let tree = make([[['a'], 'b', ['c']], 'd', [['e'], 'f', ['g']]]);

// 遍历二叉树
var result = [];
for (let node of inorder(tree)) {
  result.push(node);
}

result
// ['a', 'b', 'c', 'd', 'e', 'f', 'g']
```

### 8.作为对象属性的 Generator 函数

```JavaScript
let obj = {
  * myGeneratorMethod() {
    ···
  }
};
```

### 9.Generator 函数的 this

Generator 函数总是返回一个遍历器，ES6 规定这个遍历器是 Generator 函数的实例，也继承了 Generator 函数的`prototype`对象上的方法

```JavaScript
function* gen() {
  this.a = 1;
  yield this.b = 2;
  yield this.c = 3;
}

function F() {
  return gen.call(gen.prototype);
}

var f = new F();

f.next();  // Object {value: 2, done: false}
f.next();  // Object {value: 3, done: false}
f.next();  // Object {value: undefined, done: true}

f.a // 1
f.b // 2
f.c // 3
```

### 10.含义

Generator 是实现状态机的最佳机构

```JavaScript
var clock = function* () {
  while (true) {
    console.log('Tick!');
    yield;
    console.log('Tock!');
    yield;
  }
};
```

### 11.应用

- 异步操作的同步化表达
- 控制流管理
- 部署 Iterator 接口
- 作为数据结构

## 19.Generator 函数的异步应用

### 1.传统方法

- 回调函数
- 事件监听
- 发布/订阅
- Promise 对象

### 2.基本概念

**异步** 一个任务不是连续完成的

**回调函数** 把任务的第二段单独写在一个函数里，等到重新执行这个任务的时候，就直接调用这个函数

**Promise** 解决"回调函数地狱"（callback hell）

### 3.Generator 函数

**协程** 多个线程互相协作，完成异步任务

**协程的 Generator 函数实现** 最大特点就是可以交出函数的执行权

**Generator 函数的数据交换和错误处理**

### 4.Thunk 函数

参数的求值策略

- 传值调用（call by value）C、JavaScript
- 传名调用（call by name）Haskell

**含义** 编译器的“传名调用”实现，往往是将参数放到一个临时函数之中，再将这个临时函数传入函数体，这个临时函数就叫做 Thunk 函数

在 JavaScript 语言中，Thunk 函数替换的不是表达式，而是多参数函数，将其替换成一个只接受回调函数作为参数的单参数函数

Thunk 函数转换

```javascript
// ES5版本
var Thunk = function (fn) {
  return function () {
    var args = Array.prototype.slice.call(arguments)
    return function (callback) {
      args.push(callback)
      return fn.apply(this, args)
    }
  }
}

// ES6版本
const Thunk = function (fn) {
  return function (...args) {
    return function (callback) {
      return fn.call(this, ...args, callback)
    }
  }
}
```

**Thunkify 模块**

使用

```javascript
var thunkify = require('thunkify')
var fs = require('fs')

var read = thunkify(fs.readFile)
read('package.json')(function (err, str) {
  // ...
})
```

Thunk 自动执行 Generator 函数

```javascript
function run(fn) {
  var gen = fn()

  function next(err, data) {
    var result = gen.next(data)
    if (result.done) return
    result.value(next)
  }

  next()
}

var g = function* () {
  var f1 = yield readFileThunk('fileA')
  var f2 = yield readFileThunk('fileB')
  // ...
  var fn = yield readFileThunk('fileN')
}

run(g)
```

### 5. co 模块

**前提** Generator 函数的`yield`命令后面，只能是 Thunk 函数或 Promise 对象

Stream 模式使用 EventEmitter API 会释放三个事件

- `data`事件：下一块数据块已经准备好了
- `end`事件：整个“数据流”处理完了
- `error`事件：发生错误

## 20.async 函数

### 1.含义

Generator 函数的语法糖

`async`函数将 Generator 函数的星号（`*`）替换成`async`，将`yield`替换成`await`

改进

1. 内置执行器
2. 更好的语义
3. 更广的适用性
4. 返回值是 Promise

进一步说，`async`函数完全可以看做多个异步操作，包装成的一个 Promise 对象，而`await`命令就是内部`then`命令的语法糖

### 2.基本用法

### 3.语法

### 4. async 函数的实现原理

### 5.与其他异步处理方法的比较

### 6.实例: 按顺序完成异步操作

### 7.顶层 await

## 21.Class 的基本语法

### 1.简介

ES6 的类，完全可以看做构造函数的另一种写法

```javascript
class Point {
  // ...
}

typeof Point // "function"
Point === Point.prototype.constructor // true
```

类的内部所有定义的方法，都是不可枚举的（non-enumerable）

类必须使用`new`调用，否则会报错，普通构造函数不用`new`也可以执行

在“类”的内部可以使用`get`和`set`关键字，对某个属性设置存值函数和取值函数，拦截该属性的存取行为

存值函数和取值函数是设置在属性的 Descriptor 对象上的

```JavaScript
class CustomHTMLElement {
  constructor(element) {
    this.element = element;
  }

  get html() {
    return this.element.innerHTML;
  }

  set html(value) {
    this.element.innerHTML = value;
  }
}

var descriptor = Object.getOwnPropertyDescriptor(
  CustomHTMLElement.prototype, "html"
);

"get" in descriptor  // true
"set" in descriptor  // true
```

类的属性名，可以采用表达式

**注意点**

1. 严格模式

   默认就是严格模式

2. 不存在提升（hoist）

   ```javascript
   {
     let Foo = class {}
     class Bar extends Foo {}
   }
   ```

3. name 属性

   `name`属性总是返回紧跟在`class`关键字后面的类名

4. Generator 方法

   方法前面加上星号（`*`）

   ```javascript
   class Foo {
     constructor(...args) {
       this.args = args
     }
     *[Symbol.iterator]() {
       for (let arg of this.args) {
         yield arg
       }
     }
   }

   for (let x of new Foo('hello', 'world')) {
     console.log(x)
   }
   // hello
   // world
   ```

5. this 的指向

   默认指向类的实例，但 2 必须非常小心，一旦单独使用该方法，很可能报错

### 2.静态方法

如果在一个方法前，加上`static`关键字，表示该方法不会被实例继承，而是直接通过类来调用，这就称为“静态方法”

**注意** 如果静态方法中包含`this`关键字，这个`this`指的是类，而不是实例

静态方法可以与非静态方法重名

父类的静态方法，可以被子类继承

### 3.实例属性的新写法

实例属性除了定义在`constructor()`方法里面的`this`上面，也可以定义在类的最顶层

### 4.静态属性

```javascript
// 老写法
class Foo {
  // ...
}
Foo.prop = 1

// 新写法
class Foo {
  static prop = 1
}
```

### 5.私有方法和私有属性

解决方案

1. 命名前加下划线

2. 将私有方法移出模块

   ```javascript
   class Widget {
     foo(baz) {
       bar.call(this, baz)
     }

     // ...
   }

   function bar(baz) {
     return (this.snaf = baz)
   }
   ```

3. 将私有方法的名字命名为一个`Symbol`值

提案 属性名、方法名前加`#`

### 6. new.target 属性

该属性一般用在构造函数之中，返回`new`命令作用于的那个构造函数

如果构造函数不是通过`new`命令或`Reflect.construct()`调用的，`new.target`会返回`undefined`

```javascript
function Person(name) {
  if (new.target !== undefined) {
    this.name = name
  } else {
    throw new Error('必须使用 new 命令生成实例')
  }
}

// 另一种写法
function Person(name) {
  if (new.target === Person) {
    this.name = name
  } else {
    throw new Error('必须使用 new 命令生成实例')
  }
}

var person = new Person('张三') // 正确
var notAPerson = Person.call(person, '张三') // 报错
```

## 22.Class 的继承

### 1.简介

Class 可以通过`extends`关键字实现继承

子类必须在`constructor`方法中调用`super`方法，否则新建实例会报错

> 这是因为子类自己的`this`对象，必须先通过父类的构造函数完成塑造，得到与父类同样的实例属性和方法，然后再对其进行加工，加上子类自己的实例属性和方法。
>
> 如果不调用`super`方法，子类就得不到`this`对象。

> 只有调用`super`之后，才能使用`this`关键字

### 2.Object.getPrototypeOf()

`Object.getPrototypeOf`方法可以用来从子类上获取父类

### 3. super 关键字

1. 作为函数是，`super()`只能用在子类的构造函数之中，用在其他地方就会报错
2. `super`作为对象时，在普通方法中，指向父类的原型对象；在静态方法中，指向父类

### 4.类的 prototype 属性和 **proto** 属性

### 5.原生构造函数的继承

ES5 是先新建子类的实例对象`this`，再将父类的属性添加到子类上，由于父类的内部属性无法获取，导致无法继承原生的构造函数

ES6 允许继承原生构造函数定义子类，因为 ES6 是先新建父类的实例对象`this`，然后再用子类的构造函数修饰`this`,使得父类的所有行为都可以继承

### 6.Mixin 模式的实现

Mixin 指的是多个对象合成一个新的对象，新对象各个组成成员的接口

```javascript
function mix(...mixins) {
  class Mix {
    constructor() {
      for (let mixin of mixins) {
        copyProperties(this, new mixin()) // 拷贝实例属性
      }
    }
  }

  for (let mixin of mixins) {
    copyProperties(Mix, mixin) // 拷贝静态属性
    copyProperties(Mix.prototype, mixin.prototype) // 拷贝原型属性
  }

  return Mix
}

function copyProperties(target, source) {
  for (let key of Reflect.ownKeys(source)) {
    if (key !== 'constructor' && key !== 'prototype' && key !== 'name') {
      let desc = Object.getOwnPropertyDescriptor(source, key)
      Object.defineProperty(target, key, desc)
    }
  }
}

class DistributedEdit extends mix(Loggable, Serializable) {
  // ...
}
```

## 23.Module 的语法

### 1.概述

```javascript
// CommonJS模块
let { stat, exists, readFile } = require('fs')
```

整体加载`fs`模块（加载所有方法），“运行时加载”

```javascript
// ES6模块
import { stat, exists, readFile } from 'fs'
```

从`fs`模块加载 3 个方法，其他方法不加载，“编译时加载”，“静态加载”

### 2.严格模式

ES6 的模块自动采用严格模式

> **注意** ES6 模块之中，顶层的`this`指向`undefined`,即不应该在顶层代码使用`this`

### 3. export 命令

> **注意** `export`命令规定的是对外的接口，必须与模块内部的变量建立一一对应关系

通常情况下，`export`输出的变量就是本来的名字，但是可以使用`as`关键字重命名

### 4. import 命令

`import`命令输入的变量都是只读的，可以使用`as`关键字重命名

> **注意** import 命令具有提升效果

如果多次重复执行同一句`import`语句，那么只会执行一次，而不会执行多次

### 5.模块的整体加载

```javascript
import * as circle from './circle'
```

### 6. export default 命令

本质上，`export default`就是输出一个叫做`default`的变量或方法，然后系统允许你为它取任意名字

正是因为`export default`命令其实只是输出一个叫做`default`的变量，所以它后面不能跟变量声明语句

### 7. export 与 import 的复合写法

```javascript
// 接口改名
export { foo as myFoo } from 'my_module'

// 整体输出
export * from 'my_module'
```

### 8.模块的继承

### 9.跨模块常量

### 10. import()

`import()`动态加载，类似于 Node 的`require`方法

`import()`异步加载，`require`同步加载

`import()`返回一个 Promise 对象

适用场合

1. 按需加载
2. 条件加载
3. 动态的模块路径

**注意** `import()`加载模块成功以后，这个模块会作为一个对象，当做`then`方法的参数

## 24.Module 的加载实现

### 1.浏览器加载

- 传统方法 `<script>`

  - `defer`
  - `async`

- 加载规则

  `type="module"`，异步加载

### 2.ES6 模块与 CommentJS 模块的差异

1. CommonJS 模块输出的是一个值的拷贝，ES6 模块输出的是值的引用
2. CommonJS 模块是运行时加载，ES6 模块是编译时输出接口

### 3.Node 加载

Node 要求 ES6 模块采用`.mjs`后缀文件名

Node 规定 ES6 模块之中不能使用 CommonJS 模块的特有的一些内部变量

- `this`
- `arguments`
- `module`
- `exports`
- `__filename`
- `__dirname`

### 4.循环加载

1. CommonJS 模块的循环加载

   只输出已经执行的部分，还未执行的部分不会输出

2. ES6 模块的循环加载

### 5.ES6 模块的转码

ES6 module transplier

SystemJS

## 25.编程风格

### 1.块级作用域

1. let 取代 var
2. 全局常量和线程安全

### 2.字符串

- 静态字符串一律使用单引号或反引号，不使用双引号

- 动态字符串使用反引号

### 3.解构赋值

- 使用数组成员对变量赋值时，优先使用解构赋值
- 函数的参数如果是对象的成员，优先使用解构赋值
- 如果函数返回多个值，优先使用对象的解构赋值

### 4.对象

- 单行定义的对象，最后一个成员不以逗号结尾

- 多行定义的对象，最后一个成员以逗号结尾
- 对象尽量静态化，一旦定义，就不得随意添加新的属性。如果添加属性不可避免，要使用`Object.assign`方法
- 如果对象的属性名时动态的，可以在创造对象的时候，使用属性表达式定义
- 对象的属性和方法，尽量采用简洁表达式法

### 5.数组

- 使用扩展运算符（…）拷贝数组
- 使用 Array.from 方法，将类似数组的对象转为数组

### 6.函数

- 立即执行函数可以写成箭头函数的形式

- 使用匿名函数当作参数的场合，尽量使用箭头函数代替

- 箭头函数取代`Function.prototype.bind`，不应该再用 self/\_this/that 绑定 this

- 简单的、单行的、不会复用的函数，建议采用箭头函数

- 所有配置项都应该集中在一个对象，放在最后一个参数，布尔值不可以直接作为参数

  ```javascript
  // bad
  function divide(a, b, option = false) {}

  // good
  function divide(a, b, { option = false } = {}) {}
  ```

- 不要在函数体内使用 arguments 变量，使用 rest 运算符（…）代替
- 使用默认值语法设置函数参数的默认值

### 7.Map 结构

只有模拟现实世界的实体对象时，才使用 Object 。如果只是需要 `key:value`的数据结构，使用 Map 结构

### 8.Class

- 总是使用 Class 取代需要 prototype 的操作
- 使用 `extends`实现继承

### 9.模块

- 使用`import`取代`require`
- 使用`export`取代`module.exports`
- 如果模块只有一个输出值，就使用`export default`，`export default`与`export`不要同时使用
- 不要在模块输入中使用通配符
- 如果模块默认输出一个函数，函数名的首字母应该小写
- 如果模块默认输出一个对象，对象名的首字母应该大写

### 10.ESLint 的使用

[GitHub - airbnb/javascript: JavaScript Style Guide](https://github.com/airbnb/javascript)

## 26.读懂规格

### 1.概述

[ECMAScript 6](<[www.ecma-international.org/ecma-262/6.0/](http://www.ecma-international.org/ecma-262/6.0/)>)

### 2.术语

### 3.抽象操作的标准流程

### 4.相等运算符

### 5.数组的空位

### 6.数组的 map 方法

## 27.异步遍历器

### 1.同步遍历器的问题

### 2.异步遍历的接口

### 3.for await...of

### 4.异步 Generator 函数

### 5.yield\* 语句

## 28.ArrayBuffer

### 1.ArrayBuffer 对象

### 2.TypedArray 视图

### 3.复合视图

### 4.DataView 视图

### 5.二进制数组的应用

### 6.SharedArrayBuffer

### 7.Atomics 对象

## 29.最新提案

### 1. do 表达式

### 2. throw 表达式

### 3.链判断运算符

### 4.Null 判断运算符

### 5.函数的部分执行

### 6.管道运算符

### 7.数值分隔符

### 8.BigInt 数据类型

### 9.Math.signbit()

### 10.双冒号运算符

### 11.Realm API

### 12.#!命令

### 13. import.meta

## 30.Decorator

### 1.类的装饰

### 2.方法的装饰

### 3.为什么装饰不能用于函数?

### 4. core-decorator.js

### 5.使用装饰器自动发布事件

### 6.Mixin

### 7.Trait
