# Bootstrap 代码区域

> 使用Bootstrap框架直接在网页中显示代码

* 第一种是 `<code>` 标签。如果您想要**内联显示代码**，那么您应该使用 `<code>` 标签。
* 第二种是 `<pre>` 标签。如果代码需要被显示为一个**独立的块元素或者代码有多行**，那么您应该使用 `<pre>` 标签。

**注：**请确保当您使用 `<pre>` 和 `<code>` 标签时，开始和结束标签使用了 **unicode** 变体：` &lt;` 和 `&gt;`

#### 示例：

	```html
	<p><code>&lt;header&gt;</code> 作为内联元素被包围。</p>
	<p>如果需要把代码显示为一个独立的块元素，请使用 &lt;pre&gt; 标签：</p>
	<pre>
		&lt;article&gt;
		&lt;h1&gt;Article Heading&lt;/h1&gt;
		&lt;/article&gt;
	</pre>
	```

#### 效果：

![](https://i.imgur.com/2zxdpO6.jpg)
<!--<img src='example_image/code_design.jpg' alt="code显示效果">-->

## 变量

> 通过 `<var>` 标签标记变量

![](https://i.imgur.com/DeCQduy.png)

## 程序输出

> 通过 `<samp>` 标签来标记程序输出的内容

![](https://i.imgur.com/JRHh8O7.png)