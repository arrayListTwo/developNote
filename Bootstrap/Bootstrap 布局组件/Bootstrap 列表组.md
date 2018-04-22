# Bootstrap 列表组

> 列表组件用以列表形式呈现复杂的和自定义的内容

## 步骤

1、 向元素`<ul>`添加`.list-group`
2、 向`<li>`添加`.list-group-item`

## 默认的列表组

##### 示例
```html
<ul class="list-group">
    <li class="list-group-item">周星驰的电影</li>
    <li class="list-group-item">大话西游</li>
    <li class="list-group-item">国产凌凌漆</li>
</ul>
```
##### 效果
![](https://i.imgur.com/0vx51Cj.png)
<!--<img src="example_image/list-group.png" alt="默认的列表组">-->

## 向列表组添加徽章

> 可以向任意的列表项添加徽章组件，它会自动定位到右边
> 在`<li>`元素中添加`<span class="badge">`即可

##### 示例
```html
<h2>带有徽章的列表组</h2>
<ul class="list-group">
    <li class="list-group-item">
        <span class="badge">2</span>大话西游</li>
    <li class="list-group-item">还魂夜</li>
    <li class="list-group-item">功夫</li>
</ul>
```
##### 效果
![](https://i.imgur.com/medutFf.png)
<!--<img src="example_image/list-group-badge.png" alt="带有徽章的列表组">-->

## 向列表组添加链接

> 使用`<div>`代替`<ul>`元素
> 通过使用**锚标签代替列表项**

##### 示例
```html
<h2>向列表组添加链接</h2>
<div class="list-group">
    <a class="list-group-item" href="#">大话西游</a>
    <a class="list-group-item" href="#">还魂夜</a>
    <a class="list-group-item" href="#">功夫</a>
</div>
```
##### 效果
![](https://i.imgur.com/SOkbppw.png)
<!--<img src="example_image/list-group-href.png" alt="向列表组添加链接">-->

## 向列表组添加自定义内容

* `.active`：列表颜色加重
* `.list-group-item-heading`：列表组名称，字体稍大
* `.list-group-item-text`：列表组内容字体，字体适中

##### 示例
```html
<h2>列表组自定义内容</h2>
<div class="list-group">
    <a href="#" class="list-group-item active">
        <h4 class="list-group-item-heading">
            周星驰
        </h4>
    </a>
    <a href="#" class="list-group-item">
        <h4 class="list-group-item-heading">周星驰电影</h4>
        <p class="list-group-item-text">
            大喜中透着大悲
        </p>
    </a>
    <a href="#" class="list-group-item">
        <h4 class="list-group-item-heading">周星驰粉丝</h4>
        <p class="list-group-item-text">低调的影迷</p>
    </a>
</div>
```
##### 效果
![](https://i.imgur.com/EhF25Uq.png)
<!--<img src="example_image/list-group-custom.png" alt="向列表组添加自定义内容">-->