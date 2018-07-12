# ES6 专题篇

## 箭头函数需要注意的地方

**当要求动态上下文的时候，就不能够使用箭头函数。也就是 this 的固定化**

1.  在使用=>定义函数的时候，this 的指向是定义时所在的对象，而不是使用时所在的对象;
2.  不能够用作构造函数，这就是说，不能够使用 new 命令，否则就会抛出一个错误;
3. 不能够使用 arguments 对象;
4.  不能使用 yield 命令;

## 箭头有哪些新特点

1. 不需要function关键字来创建函数
2. 省略return关键字
3. 继承当前上下文的 this 关键字


## ES6 let、const

**let 是更完美的 var，不是全局变量，具有块级函数作用域,大多数情况不会发生变量提升。const 定义常量值，不能够重新赋值，如果值是一个对象，可以改变对象里边的属性值**

### let

1.  let 声明的变量具有块级作用域
2.  let 声明的变量不能通过 window.变量名进行访问
3.  形如 for(let x..)的循环是每次迭代都为 x 创建新的绑定

### const

## Set 数据结构

**es6 方法,Set 本身是一个构造函数，它类似于数组，但是成员值都是唯一的**

```
const set = new Set([1,2,3,4,4])
[...set] // [1,2,3,4]
Array.from(new Set())是将set进行去重
```

## promise 对象的用法,手写一个 promise

**promise 是一个构造函数，下面是一个简单实例**

```
var promise = new Promise((resolve,reject) => {
    if (操作成功) {
        resolve(value)
    } else {
        reject(error)
    }
})
promise.then(function (value) {
    // success
},function (value) {
    // failure
})
```
```
setTimeout(function() {
      console.log(1)
    }, 0);
    new Promise(function executor(resolve) {
      console.log(2);
      for( var i=0 ; i<10000 ; i++ ) {
        i == 9999 && resolve();
      }
      console.log(3);
    }).then(function() {
      console.log(4);
    });
    console.log(5);
```
首先先碰到一个 setTimeout，于是会先设置一个定时，在定时结束后将传递这个函数放到任务队列里面，因此开始肯定不会输出 1 。 然后是一个 Promise，里面的函数是直接执行的，因此应该直接输出 2 3 。 然后，Promise 的 then 应当会放到当前 tick 的最后，但是还是在当前 tick 中。 因此，应当先输出 5，然后再输出 4 。 最后在到下一个 tick，就是 1 。 “2 3 5 4 1”


## Class 的讲解

**class 语法相对原型、构造函数、继承更接近传统语法，它的写法能够让对象原型的写法更加清晰、面向对象编程的语法更加通俗**

```
class Animal {
    constructor () {
        this.type = 'animal'
    }
    says(say) {
        console.log(this.type + 'says' + say)
    }
}
 let animal = new Animal()
 animal.says('hello') // animal says hello

 class Cat extends Animal {
     constructor() {
         super()
         this.type = 'cat'
     }
 }
 let cat = new Cat()
 cat.says('hello') // cat says hello
```
contructor内部定义的方法和属性是实例对象自己的，不能通过extends 进行继承。在class cat中出现了super(),这是什么呢
在ES6中，子类的构造函数必须含有super函数，super表示的是调用父类的构造函数，虽然是父类的构造函数，但是this指向的却是cat

## Object.assign

`var n = Object.assign(a,b,c)`向n中添加a,b,c的属性

## 模版语法

就是这种形式`${varible}`,在以往的时候我们在连接字符串和变量的时候需要使用这种方式`'string' + varible + 'string'`但是有了模版语言后我们可以使用`string${varible}string`这种进行连接

## rest参数

es6引入rest参数，用于获取函数的多余参数，这样就不需要使用arguments对象了

```
function add(...values) {
    let sum = 0
    for(var val of values) {
        sum += val
    }
    return sum
}
```