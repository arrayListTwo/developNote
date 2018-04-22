# Bootstrap 进度条

> Bootstrap进度条使用CSS3过渡和动画来获得效果

> Internet Explorer 9 及之前的版本和旧版的Firefox不支持该特性，Opera 12 不支持动画

## 默认的进度条

#### 步骤

1、 添加一个带有`.progress`的`<div>`
2、 在上面的`<div>`里，添加一个带有`.progress-bar`的空子元素`<div>`
3、 添加一个带有百分比表示的宽度的`style`属性，表示进度条的位置

##### 示例
```html
<h2>默认的进度条</h2>
<div class="progress">
    <div class="progress-bar" role="progressbar" aria-valuenow="60"
         aria-valuemin="0" aria-valuemax="100" style="width: 40%"></div>
</div>
```
##### 效果
<img src="example_image/progress-default.png" alt="默认的进度条">

## 交替的进度条（创建不同样式的进度条）

#### 步骤

1、 添加一个带有`.progress`的`<div>`
2、 在上面的`<div>`内，添加一个带有`.progress-bar`和`.progress-bar-*`的空子元素`<div>`。其中：** * ** 可以是：`success`、`info`、`warning`、`danger`
3、 添加一个带有百分比表示的宽度的`style`属性，表示进度条的位置

##### 示例
```html
<h2>交替的进度条</h2>
<div class="progress">
    <div class="progress-bar progress-bar-success" role="progressbar"
         aria-valuenow="60" aria-valuemin="0" aria-valuemax="100"
         style="width: 90%;">
    </div>
</div>
<div class="progress">
    <div class="progress-bar progress-bar-info" role="progressbar"
         aria-valuenow="60" aria-valuemin="0" aria-valuemax="100"
         style="width: 30%;">
    </div>
</div>
<div class="progress">
    <div class="progress-bar progress-bar-warning" role="progressbar"
         aria-valuenow="60" aria-valuemin="0" aria-valuemax="100"
         style="width: 20%;">
    </div>
</div>
```
##### 效果
![](https://i.imgur.com/8WJQqti.png)
<!--<img src="example_image/progress-type.png" alt="进度条的显示效果">-->

## 条纹的进度条

##### 步骤
1、 添加一个带有`.progress`和`.progress-striped`的`<div>`
2、 在上面的`<div>`内，添加一个带有`.progress-bar`和`.progress-bar-*`的空子元素`<div>`。其中：** * ** 可以是：`success`、`info`、`warning`、`danger`
3、 添加一个带有百分比表示的宽度的`style`属性，表示进度条的位置

#### 示例
```html
<h2>条纹的进度条</h2>
<div class="progress progress-striped">
    <div class="progress-bar progress-bar-success" aria-valuenow="60"
         aria-valuemin="0" aria-valuemax="100" style="width: 90%">
    </div>
</div>
```
#### 效果
![](https://i.imgur.com/BoPnHYH.png)
<!--<img src="example_image/progress-striped.png" alt="条纹的进度条">-->

## 动画的进度条
#### 步骤
1、 添加一个带有`.progress`和`.progress-striped`的`<div>`，同时添加`.active`
2、 在上面的`<div>`内，添加一个带有`.progress-bar`的空子元素
3、 添加一个带有百分比表示的宽度的`style`属性，表示进度条的位置

#### 示例
```html
<h2>动画的进度条</h2>
<div class="progress progress-striped active">
    <div class="progress-bar progress-bar-success" role="progressbar"
         aria-valuenow="60" aria-valuemin="0" aria-valuemax="100"
         style="width: 40%;"></div>
</div>
```
#### 效果(左侧的条纹在运动...)
![](https://i.imgur.com/2Zk2jcY.png)
<!--<img src="example_image/progress-anim.png" alt="动画的进度条">-->

## 堆叠的进度条

> 把多个进度条放在相同的`.progress`中即实现堆叠

##### 示例
```html
<h2>堆叠的进度条</h2>
<div class="progress">
    <div class="progress-bar progress-bar-success" aria-valuenow="60"
         aria-valuemin="0" aria-valuemax="100" style="width: 40%;"></div>
    <div class="progress-bar progress-bar-info" aria-valuenow="60"
         aria-valuemin="0" aria-valuemax="100" style="width: 30%;"></div>
    <div class="progress-bar progress-bar-warning" aria-valuenow="60"
         aria-valuemin="0" aria-valuemax="100" style="width: 20%;"></div>
</div>
```
##### 效果
![](https://i.imgur.com/G210FvW.png)
<!--<img src="example_image/progress-push.png" alt="堆叠的进度条">-->