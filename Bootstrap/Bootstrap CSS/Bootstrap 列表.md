# Bootstrap 列表

* `ul`：无序列表
* `ol`：有序列表

## 无样式列表

##### `class="list-unstyled"`
* **移除了默认的 list-style 样式和左侧外边距的一组元素**（只针对直接子元素）。
* **这是针对直接子元素的**，也就是说，你需要对所有嵌套的列表都添加这个类才能具有同样的样式。

![](https://i.imgur.com/Eld1q6J.png)

## 内联列表

* 通过设置 `display: inline-block`; 并**添加少量的内补（`padding`）**，将所有元素放置于同一行。

![](https://i.imgur.com/ngLsGC4.png)

## 描述

> 带有描述的短语列表

![](https://i.imgur.com/Y7nv0UJ.png)

## 水平排列的描述

* `.dl-horizontal` 可以让 `<dl>` 内的短语及其描述排在一行。**开始是像 <dl> 的默认样式堆叠在一起，随着导航条逐渐展开而排列在一行。**
	* 在较窄的视口（`viewport`）内，**列表将变为默认堆叠排列的布局方式**。