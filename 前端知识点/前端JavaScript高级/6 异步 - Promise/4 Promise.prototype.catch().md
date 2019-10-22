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

	* 如果 `then` 方法指定的回调函数，运行中抛出错误，也会被 `catch` 方法捕获。
	
		* `Promise` 对象的错误具有“冒泡”性质，会一直向后传递，直到被捕获为止

		* 如果没有使用 `catch` 方法指定错误处理的回调函数， `Promise` 对象抛出的错误不会传递到外层代码
 
## `reject` 方法等同于抛出错误

```JavaScript
// 写法 一 
const promise = new Promise(function(resolve, reject){
	try{
		throw new Error('error')
	} catch(e){
		reject(e)
	}
});
promise.catch(function(err){
	console.log(err)
})

// 写法 二 （等同于写法一）
const promise = new Promise(function(resolve, reject){
	reject(new Error('error'))
});
promise.catch(function (error){
	console.log(error)
})
```
