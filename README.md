# 于可可 ｜ Part 1 | 模块一

## 简答题

### 第一题：请说出下面的最终执行结果，并解释为什么？

```
  var a = []
  for(var i=0;i<10;i++){
    a[i] = function (){
      console.log(i) 
    }
  }
  a[6]()
```
最终执行结果为：打印出 10。

原因是因为 for循环中打印的i是全局作用域中的i，再循环执行作用之后i已经被累加到10，无论访问哪一个,结果都是一样的。

### 第二题：请说出下面的最终执行结果，并解释为什么？

```
  var temp = 123
  if(true){
    console.log(temp)
    let temp
  }
```
最终执行的结果：报错

原因是:let 不存在变量提升，在声明变量temp之前，temp不存在，所以就会报错。

### 第三题：结合es6新语法，用最简单的方式找出数组中的最小值？

```
  var arr = [12,34,32,89,4]
  Math.min(...arr)
```
### 第四题 请详细说明 var，let，const 三种声明变量的方式之间的具体差别？

var 有变量提升，let 和const 没有
let 是在代码块内有效，var 是在全局范围内有效,let 只能声明一次 var 可以声明多次
let 和 const是块级作用域,只能在本块级作用域访问，外部访问不到。
const 声明的变量是不允许修改它的内存地址的，var 和 let 是可以的。

### 第五题
```
  var obj = {
    a:20,
    fn(){
      setTimeout(()=>{
      console.log(this.a)
      },)
    }
  }
  obj.fn()
```
最终执行的结果：打印20 

原因：普通的定时器函数的this是指向window的，如果是箭头函数的定时器是没有this的这个this是来源于他的上一级上下文环境。

### 第六题：简述Symbol类型的用途？

Symbol最主要的作用是为对象添加一个独一无二的属性，通过Symblo()创建的每一个都是唯一的永远不会重复
用它来借助对象属性名重复产生的问题。

### 第七题：说说什么是浅拷贝和深拷贝？

浅拷贝：浅拷贝只复制对象指针不复制对象本身，它们还是共享同一个内存，修改某一个对象的值，另一个对象的也会跟着改变。
深拷贝：深拷贝是创建一个一模一样的对象，不公用内存，修改新对象不会影响到新对象。

### 第八题：谈谈你是如何理解js异步编程的的，Event Loop是做什么，什么是宏任务，什么是微任务？

Event Loop：负责监听 调用栈和消息队列，一旦调用栈当中所以的任务都结束了，事件循环就会从消息队列当中取出第一个回调函数，然后压入到调用栈，消息队列发生变化，事件循环就会监听到。
宏任务：内部api 会有一个倒计时器，倒计时完毕，就会进入到事件循环
微任务：它是在本轮任务的末尾才会执行。

### 第九题：将下面的异步代码使用Promise改进？

```
  setTimeout(function() {
    var a = "hello"
    setTimeout(function() {
      var b = "lagou"
      setTimeout(function() {
        var c = "I ❤ U"
        console.log(a+b+c)
      }, 10);
    }, 10);
  }, 10);
```

```
    const promise = new Promise((resolve,reject)=>{
      var a = "hello"
      resolve(a)
    }).then((value,)=>{
      new Promise((resolve,reject)=>{
        var b = "lagou"
        resolve(value+b)
      }).then(value=>{
        var c = "I ❤ U"
        console.log(value+c)
      })
    })
```
### 第十题：请简述TypeScript与JavaScript之间的关系？

TypeScript是基于js之上的语言，，在JavaScript原有之上多了些扩展特性，多出来的实际上是一套更强大的类
型系统以及多EACMScript的新特性的支持、它最终会被编译为原始的JavaScript。TypeScript最终编译成JavaScript,所以任何一种JavaScript运行环境都支持typeScript去开发

### 第十一题：请谈谈你所认为的TypeScript优缺点？

优点：功能更强大，生态更加健全，更加完善, 是JavaScript的超集，支持es6,es7,可以直接使用最新特效,在编译时它会自动编译到ES3。

缺点：语言本身增加很多概念，学习成本比较高，需要理解接口（Interfaces）、泛型（Generics）、类（Classes）、枚举类型（Enums）。







