# Ajax应用

## 使用`getScript()`方法异步加载并执行JS文件

* 使用`getScript()`方法**异步请求并执行**服务器中的`JavaScript`格式的文件，它的调用格式如下所示：
	```html
	JQuery.getScript(url, [callback]);
				或
	$.getScritp(url, [callback]);
	```
	* **`url`**：服务器请求地址
	* **可选项 `callback`**:请求成功后，执行的回调函数

* 代码演示
	* 前台JS代码
	```js
		$("#getScript").on('click', function(){
		console.log("调用了方法");
		var $this = $(this);
		$.getScript("/springmvctest/static_resource/script.js", function(data){
			console.log(data);
			$this.attr("disabled", true);
		});
	});
	```
	* 后台数据
	```js
	var data = [{ 
	  "name": "足球"
	},{ 
	  "name": "散步"
	},{ 
	  "name": "篮球"
	},{ 
	  "name": "乒乓球"
	},{ 
	  "name": "骑自行车"
	}];
	
	$.each(data, function(index, sport){
		if(index === 1){
			$("ul").append("<li>" + sport["name"] + "</li>");
		}
	});
	```
	* 最终效果
	![](https://i.imgur.com/4R44aYp.png)