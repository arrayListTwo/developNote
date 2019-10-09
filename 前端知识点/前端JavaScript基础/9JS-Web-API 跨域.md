# 跨域

## 理论

* 什么是跨域

	* 浏览器有同源策略，不允许ajax访问其他域接口

	* 跨域条件：协议 域名 端口，有一个不同就算跨域

	* 可以跨域的三个标签
	
		* `<img>` 图片 用于打点统计，统计网站可能是其他域（百度统计）
		* `<link>` css 可以使用CDN
		* `<script>` js 可以使用CDN JSONP

	* 跨域注意事项

		* 所有的跨域请求都必须经过信息提供方允许

		* 如果未经允许即可获取，那是浏览器同源策略出现漏洞

* 前端可使用 JSONP 实现跨域

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

* 服务器端设置 http header(CORS跨域)