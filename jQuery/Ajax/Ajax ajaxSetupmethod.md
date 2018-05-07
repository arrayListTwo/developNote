# Ajax应用

## 使用`ajaxSetup()`方法设置全局`Ajax`默认选项

* 使用`ajaxSetup()`方法可以设置`Ajax`请求的一些**全局性选项值**，设置完成后，后面的`Ajax`请求将不需要再添加这些选项值，调用格式如下：
	```html
	jQuery.ajaxSetup([options])
			或
	$.ajaxSetup([options])
	```
	* **`options`**：一个对象，通过该对象设置`Ajax`请求时的全局选项值

* 代码演示
	* 前台JS代码
	```js
	$.ajaxSetup({
		dataType : 'json',
		success : function(data) {
			$("ul").empty();
			$.each(data, function(index, sport) {
				$("ul").append(sport["name"]);
			});
		}
	});
	$("#setup_one").on('click', function() {
		$.ajax({
			url : "/springmvctest/static_resource/new_json.json"
		});
	});
	$("#setup_two").on('click', function() {
		$.ajax({
			url : "/springmvctest/static_resource/test_json.json"
		});
	});
	```

	* 最终效果
	![](https://i.imgur.com/aWbbvA4.png)