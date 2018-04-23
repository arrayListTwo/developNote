# Bootstrap 表单

## 表单布局

* 垂直表单（默认）
* 内联表单
* 水平表单

**注意：**不要将表单组直接和输入框组混合使用。**建议将输入框组嵌套到表单组中使用**。

## 垂直或基本表单

1、 向`父<form>`元素添加 `role="form"`
2、 把标签和控件放在一个带有`class="form-group"`的`<div>`中。这是获取最佳间距所必需的
3、 向所有的文本元素添加`class="form-control"`

* 所有设置了 `.form-control` 类的 `<input>`、`<textarea>` 和 `<select>` 元素都将被默认设置宽度属性为 width: 100%

## 内联表单

* 内联表单，表单元素向左对齐，标签是并排的。向`<form>`标签添加`class="form-inline"`

**注意：** **只适用于视口（viewport）至少在 768px 宽度时（视口宽度再小的话就会使表单折叠）**

**注：**
* 默认情况下，`Bootstrap`中的`input`、`select`和`textarea`有**100%**的宽度，在使用内联表单时，需要设置表单控件宽度（**在内联表单，我们将这些元素的宽度设置为 width: auto;**）
* 在`<label>`标签上使用`class="sr-only"`，可以隐藏内联表单的标签

## 水平表单

1、 向父`<form>`元素添加`class="form-horizontal"`
2、 把**标签和控件**放在一个带有`class="form-group"`的`<div>`中
3、 向**标签**添加`class="control-label"`

## 静态控件

* 当您需要在一个水平表单内的表单标签后放置纯文本时，请在 <p> 上使用 `class="form-control-static"`

![](https://i.imgur.com/tFIJXFv.png)

## 表单控件状态

* `disabled`属性：禁用输入框
* `<fieldset disabled>`：禁用的字段集`fieldset`
	* 在 `Opera 18` 及更低版本的浏览器或 `Internet Explorer 11` 总没有得到全面支持，并且不会阻止键盘用户能够获取焦点或激活这些链接，`<a>` 标签的链接功能不受影响，建议使用JavaScript禁止
	* `Internet Explorer 11 `及以下浏览器中的 `<fieldset>` 元素并不完全支持 `disabled` 属性。因此建议在这些浏览器上通过 JavaScript 代码来禁用 `<fieldset>`
* `class="has-warning"，class="has-error"，class="has-success"`：**父元素添加相应的class**，警告、错误、成功的验证样式。
* **只读状态**，为输入框设置 **readonly 属性**可以禁止用户修改输入框中的内容。处于只读状态的输入框颜色更浅（就像被禁用的输入框一样），但是仍然保留标准的鼠标状态。

## 表单控件大小

* `class="input-lg"`：表单的高度增高
* `class="input-sm"`：表单的高度减小

## 控件

* 文本域

> 支持多行文本的表单控件。可根据需要改变 `rows` 属性。
```html
<textarea class="form-control" rows="3"></textarea>
```

* 内联单选和多选框
 > 通过将 `.checkbox-inline` 或 `.radio-inline` 类应用到一系列的多选框（`checkbox`）或单选框（`radio`）控件上，可以使这些**控件排列在一行**

