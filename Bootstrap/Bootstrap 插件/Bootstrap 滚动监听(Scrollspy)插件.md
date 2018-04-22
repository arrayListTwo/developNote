# Bootstrap 滚动监听(Scrollspy)插件

> 滚动监听（Scrollspy）插件，即自动更新导航插件，会根据滚动条的位置自动更新对应的导航目标
> 其基本的实现是随着您的滚动，基于滚动条的位置向导航栏添加 `.active` class。

## 用法

### 通过 `data` 属性

* 向您想要监听的元素（通常是 body）添加 `data-spy="scroll"`。
* 然后添加带有 Bootstrap .nav 组件的父元素的 **`ID` 或 `class` 的属性 `data-target`**。为了它能正常工作，您必须确保页面主体中有匹配您所要监听链接的 ID 的元素存在。
```html
<body data-spy="scroll" data-target=".navbar-example">
...
<div class="navbar-example">
    <ul class="nav nav-tabs">
        ...
    </ul>
</div>
...
</body>
```
### 通过`js`

* 通过 JavaScript 调用滚动监听，选取要监听的元素，然后调用 .scrollspy() 函数：
```js
$('body').scrollspy({ target: '.navbar-example' })
```