# 异步 - jQuery的Deferred

* 是否用过 `jQuery` 的 `Deferred` (开放封闭原则)

	* `ajax` 回调

	```JavaScript
	$.ajax({
		url: './data.json',
		success: function(res){
			console.log(res)
		},
		fail: function(error){
			console.log(error)
		}
	})
	```
	想要基于成功或失败添加逻辑时，只能通过修改代码，而不能通过扩展的形式来操作。不符合 **开放封闭** 原则。

	* `Deferred`形式

	```JavaScript
	var ajax = $.ajax('./data.json')
	ajax.done(function(res){
		console.log(res)
	}).fail(function(error){
		console.log(error)
	})
	```
	想要基于成功或失败添加逻辑时，可以通过扩展的形式来完成，可以进行链式操作（**.done().fail()**），基本符合 **开放封闭** 原则

	```JavaScript
	function waitHandle(){
		// 定义
		var dtd = $.Deferred()
		var wait = function(dtd){
			var task = function(){
				console.log('success')
				// 成功
				dtd.resolve('dtd success')
				// 失败
				dtd.reject('new Error('fail')')
			}
			setTimeout(task, 1000)
			// wait 返回
			return dtd
		}
		// 最终返回
		return wait(dtd)
	}
	var w = waitHandle()
	w.then(res => {
		console.log(res)
	}, err => {
		console.log(err)
	})
	```
	
		* `dtd.resolve(res) dtd.reject(error)` 表示执行的状态

		* `dtd.then() dtd.done() dtd.fail()` 基于成功或失败逻辑进行的操作

		* `Deferred`形式存在问题： ** 可以修改执行的状态** 

	* `Promise`形式 - 相当于`ES6`中的`Promise`对象的前世
	
	**执行状态不可以再改变**
	
	```JavaScript
	function waitHandle(){
		// 定义
		var dtd = $.Deferred()
		var wait = function(dtd){
			var task = function(){
				console.log('success')
				// 成功
				dtd.resolve('dtd success')
				// 失败
				dtd.reject('new Error('fail')')
			}
			setTimeout(task, 1000)
			// wait 返回
			return dtd.promise() // 这里返回 promise对象，而不是 deferred 对象
		}
		// 最终返回
		return wait(dtd)
	}
	var w = waitHandle()
	w.then(res => {
		console.log(res)
	}, err => {
		console.log(err)
	})
	```

	