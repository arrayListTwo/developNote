# Promise.prototype.then()

> `Promise`实例具有`then`方法。`then`方法是定义在原型对象`Promise.prototype`上的

`then`方法返回的是一个新的`Promise`实例（不是原来那个`Promise`实例）。因此可以采用链式写法，即`then`方法后面再调用另一个`then`方法

* 第一个回调函数完成以后，会将返回结果作为参数，传入第二个回调函数

* 前一个回调函数，如果返回的是`Promise`对象（即有异步操作），这时后一个回调函数，就会等待该`Promise`对象的状态发生变化，才会被调用

```JavaScript
// getJSON 函数会返回一个 Promise 对象
getJSON("/post/1.json")
	.then( post => getJSON(post.commentURL) )
	.then(
			comments => console.log("resolved: " + comments),
			err => console.log("rejected: ", err)
		)
```
**代码分析：**

第一个`then`方法指定的回调函数，返回的是另一个`Promise`对象。这时，第二个`then`方法指定的回调函数，就会等待这个新的`Promise`对象状态发生变化。如果状态变为`resolved`，就调用第一个回调函数；如果状态变为`rejected`，就调用第二个回调函数

#### 作用

* 为`Promise`实例添加状态改变时的回调函数

* `then`方法的第一个参数是`resolved`状态的回调函数，第二个参数（可选）是`rejected`状态的回调函数

	```JavaScript
	// 使用Promise对象实现封装Ajax操作
	const getJSON = function(url){
		const promise = new Promise(function(resolve, reject){
			const handler = function(){
				if(this.readyState !== 4){
					return;
				}
				if(this.status === 200){
					resolve(this.response)
				}else{
					reject(new Error(this.statusText))
				}
			};
			const client = new XMLHttpRequest();
			client.open("GET", url)
			client.onreadystatechange = handler
			client.responseType = "json"
			client.setRequestHeader("Accept", "application/json")
			client.send()
		});
		return promise;
	}
	// 使用
	getJSON("/posts.json").then(function(json){
		console.log('Contents: ' + json);
	}, function(error){
		console.log('出错了', error)
	})
	```