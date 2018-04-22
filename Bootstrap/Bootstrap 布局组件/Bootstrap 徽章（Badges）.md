# Bootstrap 徽章（Badges）

> Bootstrap徽章（Badges）与标签（Label）相似，主要区别在于徽章的边角更加圆滑

> 徽章（Badegs）主要用于突出显示新的或未读的项

> 使用徽章，只需将`<span class="badge">`添加到链接、Bootstrap导航等这些元素上

> `<span>`标签中内容为空，则会通过`CSS`的`:empty`选择器，徽章会折叠起来

##### 导航元素中含有徽章

```html
<h2>胶囊式导航中的激活状态</h2>
<ul class="nav nav-pills">
	<li class="active"><a href="#">首页 <span class="badge">42</span></a></li>
	<li><a href="#">简介</a></li>
	<li><a href="#">消息 <span class="badge">3</span></a></li>
</ul>
<br>
<h2>列表导航中的激活状态</h2>
<ul class="nav nav-pills nav-stacked" style="max-width: 260px;">
	<li class="active">
		<a href="#">
			<span class="badge pull-right">42</span>
			首页
		</a>
	</li>
	<li><a href="#">简介</a></li>
	<li>
		<a href="#">
			<span class="badge pull-right">3</span>
			消息
		</a>
	</li>
</ul>
```
##### 效果
![](https://i.imgur.com/dWO6ERK.png)
