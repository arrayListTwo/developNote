# Promise.prototype.catch()

> `Promise.prototype.catch` 方法是 `.then(null, rejection)` 或  `.then(undefined, rejection)` 的别名，用于指定发生错误时的回调函数

* 代码示例

```JavaScript
p()
	.then( val => console.log('fulfilled', val) )
	.catch( err => console.log('rejected:', err) )

// 等同于

p()
	.then( val => console.log('fulfilled', val) )
	.then( null, err  => console.log('rejected:', err) )
```

**代码分析**

* `p` 方法返回一个 `Promise` 对象
	
	* 该对象状态变为 `resolved` ，则会调用 `then` 方法指定的回调函数
	
	* 如果异步操作抛出错误，状态就会变为`rejected`，就会调用`catch`方法指定的回调函数，处理这个错误

	* 如果 `then` 方法指定的回调函数，运行中抛出错误，也会被 `catch` 方法捕获