# Ajax应用

## 使用`ajax()`方法加载服务器数据

* 使用`ajax()`方法是**最底层、功能最强大**的请求服务器数据的方法，它不仅可以获取服务器返回的数据，还能向服务器发送请求并传递数值，调用格式如下：
	```html
	jQuery.ajax([settings])
			或
	$.ajax([settings])
	```
	* **`settings`**：发送`ajax`请求时的配置对象
		* **`url`**：表示服务器请求的路径
		* **`data`**：请求时传递的数据
		* **`dataType`**：服务器返回的数据类型
		* **`success`**：请求成功时，执行的回调函数
		* **`type`**：发送数据请求的方式，默认为 `get`

* 代码演示
	* 前台JS代码
	```js
	$("#ajax").on('click', function(){
		var $this = $(this);
		$.ajax({
			url: "/springmvctest/static_resource/new_json.json",
			dataType: "json",
			success: function(data) {
				$this.attr("disabled", "true");
				$.each(data, function(index, sport){
					console.log(sport["name"]);
					$("ul").append(sport["name"]);
				});
			}
		});
	});
	```

	* 最终效果
	![](https://i.imgur.com/6OM65Iw.png)