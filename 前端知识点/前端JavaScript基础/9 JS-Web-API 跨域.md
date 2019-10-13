# 跨域

## 理论

* 什么是跨域

	* 浏览器有同源策略，不允许`ajax`访问其他域接口

	* 跨域条件：协议 域名 端口，有一个不同就算跨域

	* 可以跨域的三个标签
	
		* `<img>` 图片 用于打点统计，统计网站可能是其他域（百度统计）
		* `<link>` css 可以使用CDN
		* `<script>` js 可以使用CDN JSONP

	* 跨域注意事项

		* 所有的跨域请求都必须经过信息提供方允许

		* 如果未经允许即可获取，那是浏览器同源策略出现漏洞

## 使用 JSONP 实现跨域

* 利用`<script>`标签没有跨域限制的漏洞，网页可以得到从其他来源动态产生的`JSON`数据。`JSONP`请求一定需要对方的服务器做支持才可以

* `JSONP`优点是简单兼容性好，可用于解决主流浏览器的跨域数据访问的问题。缺点是仅支持`get`方法，具有局限性，不安全可能会遭受`XSS`攻击

* 实现流程

	* 声明一个回调函数，其函数名（如show）当做参数值，要传递给跨域请求数据的服务器，函数形参为要获取目标数据（服务器返回的data）

	* 创建一个`<script>`标签，把那个跨域的`API`数据接口地址，赋值给`<script>`的`src`属性，还要在这个地址中向服务器传递该函数名（可以通过问号传参：`?callback=show`）
	
	* 服务器接收到请求后，需要进行特殊的处理：把传递进来的函数名和它需要给你的数据拼接成一个字符串，例如：传递进去的函数名是`show`，它准备好的数据是`show('i love you')`
	
	* 最后服务器把准备好的数据通过`HTTP`协议返回给客户端，客户端再调用执行之前声明的回调函数（`show`），对返回的数据进行操作

```JavaScript
<script>
	window.callback = function(data){
		// 跨域得到的信息
		console.log(data)
	}
</script>
// script标签可以实现跨域，返回的数据是：callback({x:100})
<script src="http://www.test.com/api.js"></script>
```

* 使用`Promise`封装`JSONP`

```JavaScript
// 封装
function jsonp({url, params, callback}){
	return new Promise((resolve, reject) => {
		let script = document.createElement('script')
		window[callback] = function(data){
			resolve(data)
			document.body.removeChild(script)
		}
		params = {...params, callback}
		let arrs = []
		for(let key in params){
			arrs.push(`${key}=${params[key]}`)	
		}
		script.src = `${url}?${arrs.join('&')}`
		document.body.appendChild(script)
	})
}
// 使用
jsonp({
	url: 'http://localhost:3000/say',
	params: {wd: 'i love you'},
	callback: 'show'
}).then(data => {
	console.log(data)
})
```

## 服务器端设置 http header(CORS跨域)

* `CORS` 需要浏览器和后端同时支持

## NODE代理实现跨域

## nginx 反向代理实现跨域

## 参考

[跨域资源共享 CORS 详解  -- 阮一峰](http://www.ruanyifeng.com/blog/2016/04/cors.html)

[九种跨域方式实现原理（完整版）](https://github.com/ljianshu/Blog/issues/55)