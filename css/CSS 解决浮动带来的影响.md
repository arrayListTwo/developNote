# CSS 解决浮动带来的影响

## 方法一：clear:both

* 在容器的末端添加一个块状元素，设置样式为：`clear:both`

## 方法二 voerflow

* 使用`overflow`属性，属性值设置为：`hidden`或`auto`，会自动的清理包含的任何浮动元素
* **注意：**这种方法在某些情况下会产生滚动条或截断内容

## 方法三 :after

* 结合使用`:after`伪类和内容声明在指定的现有内容的末尾添加新的内容

```css
.clear:after{
	content: ".";
	height: 0;
	visibility: hidden;
	display: block;
	clear: both;
}
```

* **注意：** **IE6** 或 更低的浏览器不支持

## 方法四：zoom和:after结合

```css
.clearfix {
	*zoom: 1;
}
.clearfix:after {
	content: '';
	display: table;
	clear: both;
}
```
