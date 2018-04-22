# Bootstrap 按钮下拉菜单

<small>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;--- 可参见《Bootstrap下拉菜单（dropdown）》</small>

> 向按钮添加下拉菜单，只需要简单地在在一个 `class="btn-group"` 中放置按钮和下拉菜单即可

> `Bootstrap`下拉菜单需要引入`Bootstrap.js`，则需要首先引入`Bootstrap.js`

> 可以使用 <span class="caret"></span> 来指示按钮作为下拉菜单。

> 添加`data-toggle="dropdown"`下拉事件

> 按钮下拉菜单的大小，类`.btn-large`、`.btn-sm` 或 `.btn-xs`

> 上拉菜单，添加类`dropup`，即`class="btn-group dropup"`

#### 简单示例
```html
<div class="btn-group">
    <button type="button" class="btn btn-priwmary dropdown-toggle"
            data-toggle="dropdown">原始
        <span class="caret"></span>
    </button>
    <ul class="dropdown-menu" role="menu">
        <li><a href="#">功能</a></li>
        <li><a href="#">另一个功能</a></li>
        <li><a href="#">其他</a></li>
        <li class="divider"></li>
        <li><a href="#">分离的链接</a></li>
    </ul>
</div>
```
#### 效果
![](https://i.imgur.com/EiDhbpT.png)
<!--<img src="example_image/btn-dropdown.png" alt="按钮下拉菜单简单效果">-->

## 分割的按钮下拉菜单

> 分割按钮的左边是原始的功能，右边是显示下拉菜单的切换

#### 示例
```html
<div class="btn-group">
    <button type="button" class="btn btn-default">默认</button>
    <button type="button" class="btn btn-default dropdown-toggle"
            data-toggle="dropdown">
        <span class="caret"></span>
        <span class="sr-only">切换下拉菜单</span>
    </button>
    <ul class="dropdown-menu" role="menu">
        <li><a href="#">功能</a></li>
        <li><a href="#">另一个功能</a></li>
        <li><a href="#">其他</a></li>
        <li class="divider"></li>
        <li><a href="#">分离的链接</a></li>
    </ul>
</div>
```
#### 效果
![](https://i.imgur.com/tHHta7V.png)
<!--<img src="example_image/btn-dropdown-splid.png" alt="分割按钮的下拉菜单效果">-->