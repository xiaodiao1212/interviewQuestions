# ES6 专题篇

## 箭头函数需要注意的地方

**当要求动态上下文的时候，就不能够使用箭头函数。也就是 this 的固定化**

1.  在使用=>定义函数的时候，this 的指向是定义时所在的对象，而不是使用时所在的对象;
2.  不能够用作构造函数，这就是说，不能够使用 new 命令，否则就会抛出一个错误;
3. 不能够使用 arguments 对象;
4.  不能使用 yield 命令;

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
