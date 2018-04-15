# Bootstrap 表单

## 表单布局

* 垂直表单（默认）
* 内联表单
* 水平表单

## 垂直或基本表单

1、 向`父<form>`元素添加 `role="form"`
2、 把标签和控件放在一个带有`class="form-group"`的`<div>`中。这是获取最佳间距所必需的
3、 向所有的文本元素添加`class="form-control"`

## 内联表单

* 内联表单，表单元素向左对齐，标签是并排的。向`<form>`标签添加`class="form-inline"`

**注：**
* 默认情况下，`Bootstrap`中的`input`、`select`和`textarea`有**100%**的宽度，在使用内联表单时，需要设置表单控件宽度
* 在`<label>`标签上使用`class="sr-only"`，可以隐藏内联表单的标签

## 水平表单

1、 向父`<form>`元素添加`class="form-horizontal"`
2、 把**标签和控件**放在一个带有`class="form-group"`的`<div>`中
3、 向**标签**添加`class="control-label"`