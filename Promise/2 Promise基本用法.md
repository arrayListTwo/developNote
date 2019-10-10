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

* `resolve`函数的作用是，将`Promise`对象的状态从"未完成"变为"成功"(即从 pending 变为 resolved)，在异步操作成功时调用，并将异步操作的结果，作为参数传递出去

* `reject`函数的作用是，将`Promise`对象的状态从"未完成"变为"失败"(即从 pending 变为 rejected)，在异步操作失败时调用，并将异步操作报出的错误，作为参数传递出去