# Ajax 应用

## 使用`getJSON()`方法异步加载JSON格式数据

* 使用`getJSON()`方法可以通过`Ajax`异步请求的方式，获取服务器中的数据，并对获取的数据进行解析，显示在页面中，调用格式为：
```html
jQuery.getJSON(url, [data], [callback]) 
			或 
$.getJSON(url, [data], [callback])
```

	* **`url`**：请求加载`json`格式文件的服务器地址
	* **`可选项 data`**：请求时发送的数据
	* **`callback`**：数据请求成功后，执行的回调函数

## 代码演示

* 前台JS
```html
	$("#getJSON").on('click', function() {
		var $this = $(this);
		$.getJSON("/springmvctest/static_resource/new_json.json", function(data) {
			$this.attr("disabled", true);
			/*原生JS将json对象转换成json字符串*/
			console.log(JSON.stringify(data));
			/*each方法是for循环的包装迭代器*/
			$.each(data, function(index, sport) {
				console.log(sport['name']);
				$("#json_json").append("<li>" + sport['name'] + "</li>");
			});
		});
	});
```

* 后台JSON数据
	```json
	[{ 
	  "name": "足球"
	},{ 
	  "name": "散步"
	},{ 
	  "name": "篮球"
	},{ 
	  "name": "乒乓球"
	},{ 
	  "name": "骑自行车"
	}]
	```
* 最终效果
