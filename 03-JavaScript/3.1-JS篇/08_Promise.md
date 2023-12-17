# Promise

Promise 对象构造器语法如下:

```js
let promise = new Promise((resolve,reject)=>{
     // executor（生产者代码）
    // 1. resolve(value)  —— 如果任务成功完成并带有结果的 value
	// 2. reject(error) —— 如果出现了 error，error 即为 error 对象
    // 它的参数 `resolve` 和 `reject` 是由 JavaScript 自身提供的回调。仅在 executor 的内部。
})
```
> **值得注意的是：在 executor 的内部调用 `resolve | reject` 之后的调用，会被无视**

返回的 `promise` 对象具有以下内部属性（无法直接访问）：

1. `state`

   最初状态为 `pending`，当 `resolve` 被调用时状态为 `fulfilled`，或者 `reject` 被调用时变为 `rejected`

2. `result`

   最初是 `undefined`，然后在 `resolve(value)` 被调用时变为 `value`，或者在`reject(error)` 被调用时变为 `error`。

如图所示：

<img src="../../.image/Promise对象状态图.drawio.svg"  />



## 获取状态 .then .catch .finally

Promise 对象充当的是 executor 和 消费函数之间的连接，后者将接收结果或 error。可以通过使用 `.then` 和 `.catch` 方法注册消费函数。总的来说，通过消费函数来获取 `promise` 对象的结果和状态

```js
let promise = new Promise((resolve,reject)=>{})
promise
    .finally(()=>{})
    .then(
        (result)=>{},
        (error)=>{}
	)
    .catch((error)=>{})
```

说明:

1. 调用 `.then(f,f)` 可以捕获成功/错误的结果
2. 调用 `.catch(f)` 等同于调用 `.then(null,(error)=>{})`
3. `.finally(f)` 当 promise settled 时 `f` 就会执行

>如果 `.then`（或 `catch/finally` 都可以）处理程序返回一个 promise，那么链的其余部分将会等待，直到它状态变为 settled。当它被 settled 后，其 result（或 error）将被进一步传递下去。

## Promise API

在 `promise` 类中，有6中静态方法。

### promise.all()

接受一个可迭代对象，等待所有给定的Promise对象都已经被解析（resolved）或 至少有一个被拒绝（rejected）后返回一个新的promise

```js
Promise.all([promise1, promise2, ...])
  .then((results) => {
    // 当所有Promise都解决时，results包含每个Promise的解决值，顺序与传入的Promise数组一致。
  })
  .catch((error) => {
    // 如果任何Promise被拒绝，将在这里捕获到第一个被拒绝的Promise的错误信息。
  });
```

> **如果任意一个 promise 被 reject，由 `Promise.all` 返回的 promise 就会立即 reject，并且带有的就是这个 error**

### Promise.allSettled

与 `promise.all` 不同的是，最后传入的 promise 无论是什么结果，都会被返回，结果数组具有：

- `{status:"fulfilled", value:result}` 对于成功的响应，
- `{status:"rejected", reason:error}` 对于 error。

### Promise.race

与 `Promise.all` 类似，但只返回第一个 settled 的 promise 并获取其结果（或 error）。

```js
let promise = Promise.race(iterable);
```

### Promise.any

与 `Promise.race` 类似，区别在于 `Promise.any` 只等待第一个 fulfilled 的 promise，并将这个 fulfilled 的 promise 返回。

如果给出的 promise 都 rejected，那么返回的 promise 会带有 [`AggregateError`](https://developer.mozilla.org/zh/docs/Web/JavaScript/Reference/Global_Objects/AggregateError) —— 一个特殊的 error 对象，在其 `errors` 属性中存储着所有 promise error。

```js
let promise = Promise.any(iterable);
```

### Promise.resolve/reject

> 在现代的代码中，很少需要使用 `Promise.resolve` 和 `Promise.reject` 方法，因为 `async/await` 语法，使它们变得有些过时了。

`Promise.resolve(value)` 用结果 `value` 创建一个 resolved 的 promise。

`Promise.reject(error)` 用 `error` 创建一个 rejected 的 promise。

等同于

```js
let promise = new Promise(resolve => resolve(value));
let promise = new Promise((resolve, reject) => reject(error));
```



## Async/Await

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