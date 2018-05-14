# Ajax应用

## 使用`serialize()`方法序列化表单元素值

* 使用`serialize()`方法可以**将表单中有`name`属性的元素值进行序列化**，生成标准的`URL`编码文本字符串，直接可用于`ajax`请求，调用格式如下：
	```html
	$(selector).serialize();
	```
	* **`selector`**：一个或多个表单中的元素或表单元素本身

* 代码演示
	* 前台JS代码
	```html
	<form>
		<div class="form-group">
			<input class="form-control" type="text" name="name">
			<input class="form-control" type="text" name="age">
		</div>
	</form>
	<button id="form" class="btn btn-default">Ajax
	serialize()方法</button>
	/*js代码部分*/
	$("#form").on('click', function(){
		var seria = $("form").serialize();
		$("span").html(seria);
	});
	```

	* 最终效果
	![](https://i.imgur.com/ocQ0x1Y.png)