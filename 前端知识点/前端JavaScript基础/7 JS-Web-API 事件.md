# 事件

## 理论

* 通用事件绑定

	```JavaScript
	// js原生方法  IE低版本使用 attachEvent 绑定事件（和W3C标准不一样）
	elem.addEventListener(type, function(event){})
	// 阻止默认行为
	event.preventDefault()
	// 绑定事件封装（简单）
	function bindEvent(elem, type, fn){
		elem.addEventListener(type, fn)
	}
	```

* 事件冒泡

	```JavaScript
	// 阻止事件冒泡
	event.stopPropagation()
	```

* 代理

	> 代码简洁
	> 减少浏览器内存占用
	
	```JavaScript
	// 利用冒泡机制，父元素绑定事件机制
	event.target // 得到点击的目标元素对象
	// 绑定事件封装（结合代理机制）
	function bindEvent(elem, type, selector, fn){
		if(fn == null){
			fn = selector;
			selector = null
		}
		elem.addEventListener(type, function(e){
			var target
			if(selector){
				target = e.targer
				if(targer.matches(selector)){
					fn.call(target, e)
				}
			}else{
				fn(e)
			}
		})
	}
	// 使用代理（a标签需要事件处理，div是a的父元素）
	var div1 = document.getElementById('div1')
	bindEvent(div1, 'click', 'a', function(e){...})
	// 不使用代理(div标签需要事件处理)
	bindEvent(div1, 'click', function(e){...})
	```

## 题目

* 编写一个通用的事件监听函数
	
* 描述事件冒泡过程

	* DOM树型机构
	* 事件冒泡
	* 阻止冒泡
	* 冒泡的应用（代理）

* 对于一个无限下拉下载图片的页面，如何给每个图片绑定事件
	
	* 通过代理来完成