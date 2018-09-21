# data方式实现数据存储

* html5 dataset是新的HTML5标准，允许在普通的元素标签里嵌入类似`data-*`的属性，实现一些简单数据的存取。并且数量不受限制，能由`JavaScript`动态修改，也支持`CSS`选择器进行样式修改

* 不支持HTML5标准的浏览器，`jQuery`提供了一个`data()`方法来处理这个问题

## jQuery提供的存储接口

* 存储数据
	* 静态接口：`jQuery.data(element, key, value);`
	* 实例接口：`.data(key, value);`

* 取数据
	* 静态接口：`jQuery.data(element, key);`
	* 实例接口：`.data(key, value);`

* 删除数据
	* 实例接口：`jQuery.removeData(element [, key]);`
	* 实例接口：`.removeData([key]);`