# JS-Web-API DOM BOM

## DOM 操作 (Document Object Model) 文档对象模型

### 理论

* DOM本质

	* 树型结构：浏览器将HTML代码（字符串）结构化成树型结构模型（浏览器可识别，js可识别）

* DOM节点操作
	
	* 获取DOM节点
		
	```JavaScript
	document.getElementById('id') // 元素 js对象
	document.getElementsByTagName('div') // 集合 js数组对象
	document.getElementByClassName('.name') // 集合 js数组对象
	document.querySelectorAll('p') // 集合 js数组对象
	```

	* property

		* js对象的标准属性（ `{style:{width:100px}}` ）

	* Attribute

		* html代码中标签的属性（`<img class='' src='' />`）

* DOM结构操作

	* 新增节点
		
	```JavaScript
	let div1 = document.getElementById('div1')

	let p1 = document.createElement('p') // 创建新节点
	div1.appendChild(p1) // 添加新创建的元素
	
	let p2 = document.getElementById('p2')
	div1.appendChild(p2) // 移动p2元素
	```

	* 获取父元素
		
	```JavaScript
	parentElement // 获取父元素
	```

	* 获取子元素

	```JavaScript
	childNodes // 获取子元素
	```

	* 删除节点

	```JavaScript
	removeChild() // 删除子元素
	```

### 题目

* DOM是哪种基本的数据结构

	树

* DOM操作的常用的API有哪些

	* 获取DOM节点，以及节点的property和Attribute
	* 获取父节点，获取子节点
	* 新增节点，删除节点

* DOM节点的 `attr` 和 `property` 有何区别

	* property只是一个JS对象的属性的修改
	* Attribute是对HTML标签属性的修改

## BOM Browser Object Model 浏览器对象模型

### 理论

* navigator 浏览器对象 `navigator.userAgent`
	
* screen 屏幕对象

* location 地址栏对象

* history 前进后退

### 题目

* 如何检测浏览器的类型

	`navigator` 判断

* 拆解url的各部分

	`location` 对象