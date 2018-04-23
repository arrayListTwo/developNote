# Bootstrap 网格系统 （Grid System）

> Bootstrap包含了一个**响应式的，移动设备优先的、流式栅格系统**，可以随着设备或视口大小的增加而适当地扩展到12列

## Bootstrap网格系统工作原理

> 网格系统通过一系列包含内容的行和列来创建页面布局

* **行（row）**必须包含在 `.container` （固定宽度）或 `.container-fluid` （100% 宽度）中，以便为其赋予合适的排列（`aligment`）和内补（`padding`）

* 通过**行（row）**在水平方向创建一组**列（column）**

* 你的内容应当放置于**列（column）**内，并且，只有**列（column）**可以作为**行（row）**的直接子元素

* 预定义的网格类，比如`.row` 和 `.col-xs-4`，可用于快速创建网格布局

* 通过为**列（column）**设置 `padding` 属性，从而创建列与列之间的间隔（gutter）。通过为 `.row` 元素设置**负值 margin** 从而**抵消掉为 `.container` 元素设置的 `padding`**，也就间接为**行（row）**所包含的**列（column）**抵消掉了padding

* 如果一**行（row）**中包含了的**列（column）**大于 12，多余的**列（column）**所在的元素将被作为一个整体另起一行排列。

## 栅格系统参数

![](https://i.imgur.com/SV7Xj2x.png)

## 清除浮动

```html
<!--可选：多用于存在xs布局-->
<div class="clearfix visible-xs-block"></div>
```

## 列偏移

* 使用 `.col-md-offset-*` 类可以将列向右侧偏移。
* 这些类实际是通过使用 * 选择器为当前元素**增加了左侧的边距（`margin`）**。例
	* `.col-md-offset-4` 类将 `.col-md-4` 元素**向右侧偏移**了4个列（column）的宽度。
* **相对于左侧**

**CSS：**
![](https://i.imgur.com/IcqFXiM.png)

## 列排序

* 通过使用 `.col-md-push-*` 和 `.col-md-pull-*` 类就可以很容易的改变列（column）的顺序。

##### 原理

* 所有的列默认情况下都是左浮动，在统一左浮动的基础上，通过设置left和right的值来实现定位显示

**CSS：**
![](https://i.imgur.com/nz2lXR7.png)

