# Bootstrap下拉菜单（dropdown）

> 下拉菜单是可切换的，是以列表格式显示链接的上下文菜单
    
> `Bootstrap`下拉菜单需要引入`Bootstrap.js`，则需要首先引入`Bootstrap.js`

> `class="dropdown"` 菜单用于指定下拉菜单，下拉菜单都包裹在 `class="dropdown"` 里。

> `class="dropdown-menu"` 类用于实际下拉菜单的创建。

> `data-toggle`属性用于监听事件，此处下拉菜单应监听的事件为`dropdown`，故应写成`data-toggle="dropdown"`

#### 简单示例

```html
<div class="dropdown">
    <button class="btn btn-default" data-toggle="dropdown">
        周星驰电影<span class="caret"></span>
    </button>
    <ul class="dropdown-menu">
        <li>唐伯虎点秋香</li>
        <li>大话西游</li>
        <li>国产凌凌漆</li>
        <li>美人鱼</li>
    </ul>
</div>
```

#### 效果

![](https://i.imgur.com/URtQ8S2.jpg)
<!--<img src="example_image/dropdown-simple.jpg" alt="简单的下拉菜单示例">-->

## 选项

### 对齐

* 通过向 `class="dropdown-menu"` 添加 `class="pull-right"` 或者`class="dropdown-menu-right"`来向右对齐下拉菜单`<ul class="dropdown-menu pull-right">`

##### 效果

![](https://i.imgur.com/yl2OeTT.jpg)
<!--<img src="example_image/dropdown-right.jpg" alt="菜单项向右对齐">-->

### 标题和分割线

* 使用 `class="dropdown-header"` 向下拉菜单的标签区域添加标题
* 使用`class="divider"` 向下拉菜单的标签区域添加分割线
##### 示例
```html
<div class="dropdown">
    <button class="btn dropdown-toggle"
            data-toggle="dropdown">
        周星驰电影
        <span class="caret"></span>
    </button>
    <ul class="dropdown-menu">
        <li class="dropdown-header">港式老电影</li>
        <li>
            <a href="#">
                唐伯虎点秋香
            </a>
        </li>
		...
        <li class="divider"></li>
        <li class="dropdown-header">新印象电影</li>
        <li>
            <a href="#">美人鱼</a>
        </li>
    </ul>
</div>
```
##### 效果

![](https://i.imgur.com/JknEcPb.jpg)
<!--<img src="example_image/dropdown-header.jpg" alt="菜单项向右对齐">-->