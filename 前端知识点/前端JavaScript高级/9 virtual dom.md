# virtual dom

* `vdom`是什么？ 为何会存在`vdom`？

	* `virtual dom` ， 虚拟化 `DOM`

	* **用 `JS` 模拟 `DOM` 结构 ！！！！！！** （`DOM` 操作非常'昂贵'）

		* html结构语言
	
		```html
		<ul>
			<li class='item'>Item 1</li>
			<li class='item'>Item 2</li>
		</ul>
		```
		* `JS` 模拟 `DOM` 结构
		
		```JavaScript
		{
			tag: 'ul',
			attrs: {
				id: 'list'
			},
			children: [
				{
					tag: 'li',
					attrs: { className: 'item' },
					children: ['Item 1']
				},
				{
					tag: 'li',
					attrs: { className: 'item' },
					children: ['Item 2']
				}
			]
		}
		```

	* **`DOM` 变化的对比，放在 `JS` 层来做 （图灵完备语言），提高效率 ！！！！！！**

	* 提高重绘技能

* `vdom`如何应用，核心 `API` 是什么？

	* 介绍 `snabbdom`，其中一个`vdom`实现库

	```JavaScript
	var snabbdom = require('snabbdom');
	var patch = snabbdom.init([ // Init patch function with chosen modules
	  require('snabbdom/modules/class').default, // makes it easy to toggle classes
	  require('snabbdom/modules/props').default, // for setting properties on DOM elements
	  require('snabbdom/modules/style').default, // handles styling on elements with support for animations
	  require('snabbdom/modules/eventlisteners').default, // attaches event listeners
	]);
	var h = require('snabbdom/h').default; // helper function for creating vnodes
	
	var container = document.getElementById('container');
	
	var vnode = h('div#container.two.classes', {on: {click: someFn}}, [
	  h('span', {style: {fontWeight: 'bold'}}, 'This is bold'),
	  ' and this is just normal text',
	  h('a', {props: {href: '/foo'}}, 'I\'ll take you places!')
	]);
	// Patch into empty DOM element – this modifies the DOM as a side effect
	patch(container, vnode);
	
	var newVnode = h('div#container.two.classes', {on: {click: anotherEventHandler}}, [
	  h('span', {style: {fontWeight: 'normal', fontStyle: 'italic'}}, 'This is now italic type'),
	  ' and this is still just normal text',
	  h('a', {props: {href: '/bar'}}, 'I\'ll take you places!')
	]);
	// Second `patch` invocation
	patch(vnode, newVnode); // Snabbdom efficiently updates the old view to the new state
	
	// to unmount from the DOM and clean up, simply pass null
	patch(newVnode, null)
	```
	* 核心 API
		
		* `h('<标签名>', {...属性...}, [...子元素...])` // 生成 vnode 节点

		* `h('<标签名>',{...属性...}, '...')`

		* `patch(container, vnode)`

		* `patch(vnode, newVnode)` // 比对vnode节点，只渲染变化，减少 DOM 操作

* 介绍一下 `diff` 算法

	* 什么是 `diff` 算法

		* `linux` 的基础命令

		* `git diff` 命令

		* `diff` 算法不是 `vdom` 专有

	* `vdom` 为何使用 `diff` 算法

		* `DOM` 操作是 '昂贵' 的，因此尽量减少 `DOM` 操作

		* 找出本次 `DOM` 必须更新的节点来更新，其他的不更新

		* 这个 **找出** 的过程，就需要 `diff` 算法

	* `diff` 算法的实现流程

		* `patch(container, vnode)` 

			* 将 `JS` 模拟的 `DOM` 结构，转化成真实的 DOM 元素

			```JavaScript
			// 伪代码，简单实现
			function createElement (vnode) {
			  var tag = vnode.tag
			  var attrs = vnode.attrs || {}
			  var children = vnode.children || []
			  if (!tag) {
			    return null
			  }
			  // 创建真实的 DOM 元素
			  var elem = document.createElement(tag)
			  // 属性
			  var attrName
			  for (attrName in attrs) {
			    if (attrs.hasOwnProperty(attrName)) {
			      // 给 elem 添加属性
			      elem.setAttribute(attrName, attrs[attrName])
			    }
			  }
			  // 子元素
			  children.forEach(function (childVnode) {
			    // 给 elem 添加子元素
			    elem.appendChild(createElement(childVnode)) // 递归
			  })
			  // 返回真实的 DOM 元素
			  return elem
			}
			```

			* 将真实的 `DOM` 元素添加到 `container` 容器
	
		* `patch(vnode, newVnode)` 比对

		```JavaScript
		// 伪代码，不能运行
		function updateChildren (vnode, newVnode) {
		  var children = vnode.children || []
		  var newChildren = newVnode.children || []
		
		  children.forEach(function (childVnode, index) {
		    var newChildVnode = newChildren[index]
		    if (childVnode.tag === newChildVnode.tag) {
		      // 深层次对比，递归
		      updateChildren(childVnode, newChildVnode)
		    } else {
		      // 替换
		      replaceNode(childVnode, newChildVnode)
		    }
		  })
		}
		
		function replaceNode (vnode, newVnode) {
		  // 真实的 DOM 节点
		  var elem = vnode.elem
		  var newElem = createElement(newVnode)
		  // 替换
		...
		}
		```