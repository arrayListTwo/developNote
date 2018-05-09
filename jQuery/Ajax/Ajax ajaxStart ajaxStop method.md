# Ajax应用

## 使用`ajaxStart()`和`ajaxStop()`方法

* `ajaxStart()`和`ajaxStop()`方法时绑定`Ajax`事件

* 使用`ajaxStart()`方法，用于在`Ajax`请求发出前触发函数
* 使用`ajaxStop()`方法用于在`Ajax`请求完成后触发函数


* 调用格式如下：
	```html
	$(selector).ajaxStart(function())
			或
	$(selector).ajaxStop(function())
	```
	* **`function()`**：绑定的函数，当发送`Ajax`请求前执行`ajaxStart()`方法绑定的函数，请求成功后，执行`ajaxStop()`方法绑定的函数

* 代码演示
	* 前台JS代码
	```js
	<script type="text/javascript">
		$(function() {
			$(document).ajaxStart(function() {
				console.log("开始请求");
				$(this).html("正在请求数据...");
			});
			$(document).ajaxStop(function() {
				console.log("结束请求");
				$(this).html("数据请求完成！");
			});
			$("#btnShow").bind("click", function() {
				var $this = $(this);
				$.ajax({
					url : "/springmvctest/static_resource/new_json.json",
					dataType : "json",
					success : function(data) {
						$this.attr("disabled", "true");
						$.each(data, function(index, sport){
							$("ul").append("<li>我的名字叫：" + sport.name + "</li>");
						})
					}
				});
			})
		});
	</script>
	```

	* 最终效果
	![](https://i.imgur.com/WWiFWTu.png)