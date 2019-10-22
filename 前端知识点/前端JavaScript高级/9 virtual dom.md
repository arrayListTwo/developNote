# virtual dom

* 使用 `JS` 模拟 `DOM` 结构

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

* `vdom`是什么？ 为何会存在`vdom`？

	* `virtual dom` ， 虚拟化 `DOM`

	* 用 `JS` 模拟 `DOM` 结构

	* `DOM` 变化的对比，放在 `JS` 层来做 （图灵完备语言）

	* 提高重绘技能

* `vdom`如何应用，核心 `API` 是什么？

* 介绍一下 `diff` 算法