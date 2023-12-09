# Promise

> 为了解决异步带来的问题,JS中推出了新对象`Promise`
>
> 一个Promise对象有三种状态:
>
> 1. `Pending(进行中)`:初始状态
> 2. `Fulfilled(成功)`:异步操作完成
> 3. `Rejected(失败)`:异步操作失败

`Promise`对象通过构造函数来进行创建,构造函数接受一个函数作为参数

该回调函数有两个参数:(一旦状态改变,就会固定)

1. `resove` 代码正常执行时,设置返回值
2. `reject`(可选) 代码执行出错时,设置错误信息

```js
//创建一个Promise实例,将执行代码通过函数形式传递
const myPromise = new Promise((resolve,reject)=>{
    setTimeout(()=>{
        //设置返回值,异步的不能通过return来设置返回值
        resolve('返回结果')
    },1000)
})
//获取Promise返回值,正常执行时,会自动通过then()方法内的回调函数来返回结果
myPromise.then((result)=>{
    
}).catch((err)=>{
    
})
//当执行代码出错时,会通过catch()方法内的回到函数来返回出错信息
```

> Promise可以链式调用，即使用`.then()`方法返回一个新的Promise对象，可以继续调用`.then()`或`.catch()`来处理后续的异步操作结果。

### Promise其他属性及方法

1. `Promise.all([p1,p2,p3...])`

```js
const p = new Promis.all([p1,p2,p3])
//p的状态,只有p1,p2,p3三个promise实例的状态都变成fulfiled,p的状态才是fulfiled
```

2. `Promise.race([p1,p2,p3...])`

3. `promise.resolve()`

   参数的几种情况:

       1. promise实例

      2. 参数是一个thenable对象,会直接执行thenable的then方法

      3. 
      4. 不带任何参数,会直接返回一个`resolved`状态的promise对象

``` js
promise.resolve('foo') == Promise((resolve)=>{resolve('foo')})+
```

4. `Promise.reject()`

## Async Await

ES7引入了async函数,以同步方式编写异步代码(最优解决方案)

在JS中 可以通过`async`关键字来快速的创建异步函数,返回一个`promise`对象

### async

1. async声明的异步函数,返回值会自动包装成promise
2. async声明的异步函数中,可以使用await来调用其他的异步函数

### await

1. 调用异步函数时,可以直接在函数前使用`await`关键字对其进行调用
2. 调用`awiat`,会等待promise函数执行出结果,可以通过变量接收结果
3. 注意: `awiat`并不是将异步函数改变为同步函数,只是改变了调用方式
   - await需要再async声明的异步函数中使用
   - 可以在模块的外层作用域中使用await

```js
async function fn(){
    let result = await fn1() 
}
```

> 可以使用try..catch方法来处理错误