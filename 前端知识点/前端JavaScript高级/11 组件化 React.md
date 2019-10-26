# 组件化 React

* 说一下对组件化的理解

	* 组件的封装

		* 视图
		
		* 数据

		* 变化逻辑（数据驱动视图变化）
		
	* 组件的复用

		* `props` 传递数据


* `JSX` 本质是什么

	* `JSX` 语法

		* `JSX` 语法根本无法被浏览器所解析

		* `html` 形式

		* 引入 `JS` 变量和表达式: 使用 `{...}` 形式

			* `if...else...`
	
			* `for` 循环

		* `style` 和 `className`

		* 事件

	* `JSX` 其实是语法糖

	* 开发环境下，会将 `JSX` 解析成 `JS`
		
	```JavaScript

	// React.createElement 参数说明
	React.createElement("div", {id: 'div1'}, child1, child2, child3)
	Reate.createElement("div", {id: 'div1'}, [...])

	/* JSX 代码 */
	var profile = 
		<div>
			<img src="avatar.png" className="profile" />
			<h3>{[user.firstName, user.lastName].join(' ')}</h3>
		</div>

	/* 解析结果 返回vnode */
	var profile = React.createElement("div", null, 
		React.createElement("img", {src: "avatar.png", className: "profile"}),
		React.createElement("h3", null, [user.firstName, user.lastName].join(" "))
	)
	```

	```JavaScript
	/* JSX 写法 */
	render(){
		const list = this.props.data
		return (
			<ul>
				{
					list.map((item, index) => {
						return <li key={index}>{item}</li>
					})
				}
			</ul>
		)
	}

	/* 解析结果 返回vnode */
	function render(){
		const list = this.props.data
		return React.createElement(
			"ul",
			null,
			list.map((item, index) => {
				return React.createElement(
					"li",
					{key: index},
					item
				)
			})
		)
	}
	```

	* 独立的标准

		* `JSX` 是 `React` 引入的，但不是 `React` 独有的

		* `React` 已经将它作为一个独立标准开发，其他项目也可用

		* `React.createElement` 是可以自定义修改的

* `JSX` 和 `vdom` 的关系

	* 分析：为何需要 `vdom`

		* `vdom` 是 `React` 初次推广开来的，结合 `JSX`

		* `JSX` 就是模板，最终要渲染成 `HTML`，数据驱动视图

		* 初次渲染 + 修改 `state` 后的 `re-render`

			* 初次渲染 - `ReactDom.render(<App />, container)`

			* 会触发 `patch(container, vnode)`

			* `re-render` - `setState`

			* 会触发 `patch(vnode, newVnode)`

		* 正好符合 `vdom` 的应用场景

	* `React.createElement` 和 `h` 基本一致，都生成 `vnode`

	* 自定义组件的解析
	
		* `div` - 直接渲染 `<div>` 即可，`vdom` 可以做到

		* 自定义组件（`class`），`vdom` 默认不认识

		* 因此自定义组件定义的时候必须声明 `render` 函数

		* 根据 `props` 初始化实例（组件使用`class`定义，构造函数），然后执行实例的 `render` 函数

		* `render` 函数返回的还是 `vnode` 对象

* 说一下 `setState` 的过程

	* `setState` 的异步

		* 可能会一次执行多次 `setState`

		* 没必要每次 `setState` 都重新渲染，考虑性能

	* 每个组件实例，都有 `renderComponent` 方法（源自继承）

	* 执行 `renderComponent` 会重新执行实例的 `render` 函数

	* `render` 函数返回 `newVnode`， 然后拿到 `preVnode`

	* 执行 `patch(preVnode, newVnode)`

* 阐述自己对 `React` 和 `Vue` 的认识

	* 两者的本质区别

		* `vue` - 本质是 `MVVM` 框架，由 `MVC` 发展而来

		* `React` - 本质是前端组件化框架，由后端组件化发展而来

	* 看模板和组件化的区别

		* 模板

			* `vue` - 使用模板 （最初由 `angular` 提出）
	
			* `React` - 使用 `JSX` 
	
			* 模板语法上，倾向于 `JSX`
	
			* 模板分离上，倾向于 `Vue` 

		* 组件化

			* `React` 本身就是组件化，没有组件化就不是 `React`

			* `vue` 也支持组件化，不过是在 `MVVM` 上的扩展

	* 两者共同点

		* 都支持组件化

		* 数据驱动视图

	* 总结问题答案

		* 国内使用，首推 `Vue` 。文档更易读、易学、社区够大

		* 如果团队水平够高，推荐使用 `React`。组件化和 `JSX` 