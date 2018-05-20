# jQuery style 样式篇 - 选择器 selector (ID Class Element *)

> jQuery提供了一系列的选择器帮助开发者达到这一目的，让开发者可以更少的处理复杂选择过程与性能优化，更多专注于业务逻辑的编写

## ID选择器 

> 元素的`ID`属性

> ID是唯一的，每个ID值在一个页面中只能使用一次

```js
$("#ID"); // jQuery对象
```
**id选择器**是最基本的选择器，`jQuery`内部使用`JavaScript`函数`document.getElementById()`来处理ID的获取

## 类选择器 Class

> 通过`class`样式类名获取节点

> 类选择器，相对id选择器来说，效率相对会低一些，但**优势就是可以多选**

```js
$( ".class" )
```

* JS原生方法`document.getElementsByClassName('class');`

	使用JS原生获取的是一个**相同类的集合**，如果你对这些元素进行操作（例如：修改样式），你必须**将这些元素一个一个取出来，分别赋值**，你**不能对集合divs直接赋值**

* 使用jQuery对象的类选择器

	使用jQuery对象的类选择器，取得一个集合，但是你**可以直接对该集合进行赋值**。这样就省略了一个元素一个元素赋值的过程

## 元素选择器 Element

> 根据给定（html)标签名称选择所有的元素

> 搜索指定元素标签名称的所有节点，这是一个**合集的操作**

```js
$("element");
```

* JS原生方法`getElementsByTagName("tagName")`

## 全选择器（* 选择器）

> 全选择器代表文档页面中的所有元素

```js
$("*");
```

* JS 原生方法，获取文档中所有的元素，通过`document.getElementByTagName("*")`

## 使用JS原生方法获取对象局限：

> `id`、`class`、`tag`、`*`，都可以通过原生的方法获取到对应的节点，但存在兼容性问题

* IE 会将注释节点实现为元素，所以在 IE 中调用`getElementByTagName`里面会包含注释节点

* `getElementById`的参数在 IE8 及较低的版本不区分大小写

* `getElementsByClassName`，IE8 及较低的版本不支持

* IE7 及较低的版本，表单元素中，如果表单 A 的 name的属性名用了另一个元素 B 的 ID 名并且 A 在 B 之前，那么 `getElementById` 会选中 A
