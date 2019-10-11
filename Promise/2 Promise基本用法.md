# Promise 基本用法

> `Promise`对象是一个构造函数，用来生成`Promise`实例

### Promise实例

> `Promise`构造函数接受一个函数作为参数，该函数的两个参数分别是`resolve`和`reject`。它们是两个函数，由`JavaScript`引擎提供，不用自己部署

> `Promise`新建后就会立即执行

```JavaScript
const promise = new Promise(function(resolve, reject){
	// ... some code
	if(/* 异步操作成功 */){
		resolve(value)
	}else{
		reject(value)
	}
})
```

* `resolve`函数的作用是，将`Promise`对象的状态从"未完成"变为"成功"(即从 `pending` 变为 `resolved`)，在异步操作成功时调用，并将异步操作的结果，作为参数传递出去

* `reject`函数的作用是，将`Promise`对象的状态从"未完成"变为"失败"(即从 `pending` 变为 `rejected`)，在异步操作失败时调用，并将异步操作报出的错误，作为参数传递出去

### 回调函数的参数

> 如果调用`resolve`函数和`reject`函数时带有参数，那么它们的参数会被传递给回调函数。

* `reject`函数的参数通常是`Error`对象的实例，表示抛出的错误

* `resolve`函数的参数除了正常的值以外，还可能是另一个`Promise`实例（即一个异步操作的结果是返回另一个异步操作）

```JavaScript
// p1是一个Promise对象，3秒之后状态变为rejected
const p1 = new Promise(function(resolve, reject){
	setTimeout(() => reject(new Error('fail')), 3000)
})

// p2是一个Promise对象，p2的状态在1秒之后改变，resolve方法返回的是p1
const p2 = new Promise(function(resolve, reject){
	setTimeout(() => resolve(p1), 1000)
})

p2
	.then(result => console.log(result))
	.catch(error => console.log(error))

//执行结果 Error: fail
```

**代码分析：**
	
**理论**

* `p1`和`p2`都是`Promise`的实例，但是`p2`的`resolve`方法将`p1`作为参数，即一个异步操作的结果是返回另一个异步操作。

* `p1`的状态就会传递给`p2`，也就是说，`p1`的状态决定了`p2`的状态。如果`p1`的状态是`pending`，那么`p2`的回调函数就会等待`p1`的状态改变；如果`p1`的状态已经是`resolved`或者`rejected`，那么`p2`的回调函数将会立即执行

**具体代码分析**

* `p1`是一个`Promise`，3秒之后变为`rejected`

* `p2`的状态在1秒之后改变，`resolve`方法返回的是`p1`

* 由于`p2`返回的是另一个`Promise`，导致`p2`自己的状态无效了，由`p1`的状态决定`p2`的状态。所以，后面的`then`语句都变成针对后者（`p1`）。又过了2秒，`p1`变为`rejected`，导致触发`catch`方法指定的回调函数