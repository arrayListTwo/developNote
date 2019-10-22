# Promise.prototype.finally()

> `finally` 方法用于指定不管 `Promise` 对象最后状态如何，都会执行的操作

```JavaScript
// 不管promise最后的状态，
// 在执行完then或catch指定的回调函数以后，
// 都会执行finally方法指定的回调函数
promise
	.then( result => {...} )
	.catch( error => {...} )
	.finally( () => {...} )
```

* `finally` 方法的回调函数不接受任何参数，这也意味着没有办法知道，前面的 `Promise` 状态到底是 `fulfilled` 还是 `rejected`。 这表明， `finally` 方法里面的操作，应该是与状态无关的，不依赖于 `Promise` 的执行结果