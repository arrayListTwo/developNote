# Ajax

## 理论

* XMLHttpRequest

	```JavaScript
	var xhr = new XMLHttpRequest()
	// false 代表异步
	xhr.open('GET', '/api', false)
	xhr.onreadystatechange = function(){
		// 异步执行
		if(xhr.readyState === 4){ // ajax请求已经完成
			if(xhr.status === 200){ // 表示服务端返回成功
				console.log(xhr.responseText)
			}	
		}
	}
	xhr.send(null)
	```

	* IE 低版本使用 ActiveXObject ，和 W3C标准一样

* 状态码说明

	```JavaScript
	xhr.readyState
		0  (未初始化)，还没有调用send()方法
		1 （载入）已调用send()方法，正在发送请求
		2 （载入完成）send()方法执行完成，已经接收到全部相应内容
		3 （交互）正在解析响应内容
		4 （完成）响应内容解析完成，可以在客户端调用了

	xhr.status
		2xx 表示成功处理请求
		3xx 需要重定向，浏览器直接调用
		4xx 客户端请求错误
		5xx 服务端错误
	```

* 跨域

## 题目

* 手动编写一个ajax，不依赖第三方库

	```JavaScript
	var xhr = new XMLHttpRequest()
	// false 代表异步
	xhr.open('GET', '/api', false)
	xhr.onreadystatechange = function(){
		// 异步执行
		if(xhr.readyState === 4){ // ajax请求已经完成
			if(xhr.status === 200){ // 表示服务端返回成功
				console.log(xhr.responseText)
			}	
		}
	}
	xhr.send(null)
	```