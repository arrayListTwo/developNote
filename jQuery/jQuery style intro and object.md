# jQuery Style 样式篇 - intro and object

> 2.x 不再兼容IE6、7、8浏览器，主要目的是为了兼容移动端开发

> 如果比较在意老版本 IE 用户，只能使用 jQuery1.9及之前的版本

> jQuery每个系列版本分为：压缩版(compressed)与开发版(development).在项目开发过程中使用开发版（开发版本便于代码修改及调试），项目上线发布使用压缩版（因为压缩版本体积更小，效率更快）

## jQurey对象与DOM对象是不一样的

* 通过**原生的DOM模型**提供的方法，获取的DOM元素是一个**DOM对象**
* 通过**jQuery的selector**得到的是一个**jQuery对象（类数组对象）**
	* 通过jQuery处理DOM操作，可以让开发者更专注于业务逻辑的开发

### `$`符号

* `$`是著名的`jQuery`符号。实际上，`jQuery`把所有功能都封装在一个全局变量`jQuery`中，而`$`也是一个合法的变量名，它是变量`jQuery`的别名：

```JavaScript
window.jQuery; // jQuery(selector, context)
window.$; // jQuery(selector, context)
$ === jQuery; // true
typeof($); // 'function'
```

* `$`本质上就是一个函数，但是函数也是对象，于是`$`除了可以直接调用外，也可以有很多其他属性

* `jQuery`交出`$`的使用权

```JavaScript
$; // jQuery(selector, context)
// 释放jQuery的$符号使用权
jQuery.noConflict();
$; // undefined
jQuery; // jQuery(selector, context)
```

### jQuery对象转换成DOM对象

> jQuery是一个**类数组对象**，它的每个元素都是一个引用了DOM节点的对象；而DOM对象就是一个单独的DOM元素

> jQuery库本质上还是JavaScript代码，它只是对JavaScript语言进行包装处理，为的是提供更好更方便快捷的DOM处理与开发中经常使用的功能

> 使用jQuery的同时也能混合JavaScript原生代码一起使用

* 利用**数组下标的方式**读取到jQuery中的DOM对象

	```js
	// 得到的dom就是一个DOM对象
	// $jquery 是一个jQuery对象
	var dom = $jquery[0];
	```
* 利用**jQuery自带的get()方法**

	jQuery对象自身提供了一个get()方法，允许我们直接访问jQuery对象中共的相关DOM节点，get方法中需提供一个元素的索引

	```js
	// 得到的dom就是一个DOM对象
	// $jquery 是一个jQuery对象
	var dom = $jquery.get(3);
	```

### DOM对象转换成jQuery对象

> **`$(参数)`**是一个**多功能的方法**，通过传递不同的参数而产生不同的作用

* 如果传递给`$(参数)`函数的参数是一个`DOM`对象，`jQuery`方法会把这个`DOM`对象给包装成一个新的`jQuery`对象

	```js
	// 得到的$jQuery就是一个jQuery对象
	// dom 参数是一个DOM对象
	var $jQuery = $(dom);
	```