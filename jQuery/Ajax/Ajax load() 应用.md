# Ajax 应用

## 使用`load()`方法异步请求数据

* 使用`load()`方法通过**Ajax**请求加载服务器中的数据，并**把返回的数据放置到被选元素**中，它的调用格式为：
```html
load(url, [data], [callback])
```
	* **`url`**：加载服务器地址
	* **`可选项 data`**：请求时发送的数据
	* **`callback`**：数据请求成功后，执行的回调函数

* 代码演示
> 后台使用`SpringMVC`框架搭建项目`springmvctest`，在`webapp`目录下创建静态资源`static_resource/NewFile.html`

	* 前台界面
	
	```html
	<div class="container">
		<button id="ajax_load" class="btn btn-default">Ajax load()方法</button>
	</div>
	<div id="load_html" class="container"></div>
	```

	```js
	$(function() {
		$("#ajax_load").on(
			'click',
			function() {
				var $this = $(this);
				$("#load_html").html("<span>使用Ajax的load()方法加载数据</span>").load(
						"/springmvctest/static_resource/NewFile.html",
						function() {
							$this.attr("disabled", true);
				});
			});
	});
	```

	* 后台搭建

	![](https://i.imgur.com/NLwXZuC.png)

		* `NewFile.html`中的内容
		
			```html
			<h3>测试部分</h3>
			<li>橘子</li>
			<li>香蕉</li>
			<li>葡萄</li>
			<li>苹果</li>
			<li>西瓜</li>
			```
	* 最终效果
	![](https://i.imgur.com/p3kxvj8.png)