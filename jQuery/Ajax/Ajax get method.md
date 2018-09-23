# Ajax应用

## 使用`get()`方法以`GET`方式从服务器获取数据

* 使用`get()`方法时，采用`GET`方式向服务器请求数据，并**通过方法中回调函数的参数返回请求的数据**，它的调用格式如下：
	```html
	$.get(url, [callback]);
	```
	* **`url`**：服务器请求地址
	* **可选项 `callback`**:请求成功后，执行的回调函数

* 代码演示
	* 前台JS代码
	```js
	$("#get").on('click', function() {
		var $this = $(this);
		$.get("/springmvctest/static_resource/new_json.json", 	function(data){
				$this.attr("disabled", true);
				$.each(data, function(index, sport) {
					console.log(index + " : " + sport["name"]);
					$("ul").append("<li>" + sport["name"] + "</li>");
				});
			});
	});
	```
	* 后台数据
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
	![](https://i.imgur.com/tjYCPyH.png)