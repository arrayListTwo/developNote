# Ajax应用

## 使用`post()`方法以`POST`方式从服务器发送数据

* 使用`post()`方法多用于以`POST`方式向服务器发送数据，服务器接收到数据之后，进行处理，并将处理结果返回页面，调用格式如下：
	```html
	$.post(url, [data], [callback]);
	```
	* **`url`**：服务器请求地址
	* **可选项 `data`**：向服务器请求时发送的数据，参数格式为`key/value`方式
	* **可选项 `callback`**:请求成功后，执行的回调函数

* 代码演示
	* 前台JS代码
	```js
	$("#post").on('click', function() {
	var $this = $(this);
	$.post("dopost.htm", {num: "3中文"}, function(data){
		$this.attr("disabled", true);
		console.log(data);
		console.log(JSON.parse(data).nature);
		$("ul").append("<li>" + JSON.parse(data).nature + "</li>");
		});
	});
	```
	* 后台代码
	```java
	@RequestMapping(value = "dopost", method = RequestMethod.POST)
	@ResponseBody
	public String doAjaxPost() {
		// 获取post方式提交过来的数据
		String num = request.getParameter("num");
		System.out.println(num);
		Gson gson = new Gson();
		Person person = new Person("5中文");
		System.out.println(gson.toJson(person));
		// 返回json格式数据(含有中文)
		return gson.toJson(person);
	}

	class Person {
		String nature;

		public Person(String nature) {
			super();
			this.nature = nature;
		}

		public String getNature() {
			return nature;
		}

		public void setNature(String nature) {
			this.nature = nature;
		}

	}
	```
	* 解决后台返回中文乱码，springmvc配置文件添加配置
	```xml
	<!-- 解决返回前台时，含有中文出现乱码问题 -->
	<mvc:annotation-driven>
		<mvc:message-converters>
			<bean class="org.springframework.http.converter.StringHttpMessageConverter">
				<property name="supportedMediaTypes" value="text/html;charset=utf-8"></property>
			</bean>
		</mvc:message-converters>
	</mvc:annotation-driven>
	```	

	* 最终效果
	![](https://i.imgur.com/XrkUBsw.png)