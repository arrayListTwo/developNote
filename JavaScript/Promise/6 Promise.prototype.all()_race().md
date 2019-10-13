# Promise.all()、Promise.race()

> `Promise.all()` 和 `Promise.race()` 方法用于将多个 `Promise` 实例，包装成一个新的 `Promise` 实例

## Promise.all()

* 代码

	```JavaScript
	const p = Promise.all([p1, p2, p3]);
	p
		.then(( [books, user]) => {...} )
		.catch( reason => {...} )
	```

	**代码分析**

	`p`的状态由`p1`、`p2`、`p3` 决定，分成两种情况

	* 只有`p1`、`p2`、`p3`的状态都变成 `fulfilled`，`p`的状态才会变成 `fulfilled` ，此时 `p1`、`p2`、`p3` 的返回值组成一个数组，传递给 `p` 的回调函数

	* 只要 `p1`、`p2`、`p3` 之中有一个被 `rejected` ，`p` 的状态就会变成 `rejected`，此时第一个被 `reject` 的实例的返回值，就会传递给 `p` 的回调函数

* 如果作为参数的 `Promise` 实例，自己定义了 `catch` 方法，那么它一旦被 `rejected` ，并不会触发 `Promise.all()` 的 `catch` 方法

	```JavaScript
	// p1
	const p1 = new Promise((resolve, reject) => {
		resolve('hello')
	})
	.then(result => result)
	.catch(e => e)

	// p2
	const p2 = new Promise((resolve, reject) => {
		throw new Error('报错了')
	})
	.then(result => result)
	.catch(e => e)

	Promise.all([p1, p2])
	.then(result => console.log(result))
	.catch(e => console.log(e))
	
	// 结果： ["hello", Error:报错了]
	```	

	**代码解析**

	* `p1` 会 `resolved`

	* `p2` 首先会 `rejected`， 但是`p2`有自己的`catch`方法，该方法返回的是一个新的`Promise`实例，`p2`指向的实际上是这个实例。该实例执行完`catch`方法后，也会变成`resolved`，导致`Promise.all()`方法参数里面的两个实例都会`resolved`
	
	* 因此，`Promise.all()`会调用`then`方法指定的回调函数，而不会调用 `catch` 方法指定的回调函数

	* 如果`p2`没有自己的`catch`方法，就会调用`Promise.all()`的`catch`方法

## Promise.race()

```JavaScript
const p = Promise.race([p1, p2, p3])
```

只要 `p1`、`p2`、`p3` 之中有一个实例率先改变状态， `p` 的状态就跟着改变。那个率先改变的 `Promise` 实例的返回值，就传递给 `p` 的回调函数