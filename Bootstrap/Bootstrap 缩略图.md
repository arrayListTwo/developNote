# Bootstrap 缩略图

## 普通缩略图

#### 创建缩略图步骤：

* 在图像周围添加带有`.thumbnail`的`<a>`标签，
* 这样做会添加四个像素的内边距（padding）和一个灰色的边框
* 当鼠标悬停在图像上时，会动画显示出图像的轮廓

##### 示例
```html
<div class="container">
    <div class="row">
        <div class="col-xs-6">
            <a href="#" class="thumbnail">
                <img src="../source/zhou.jpg" alt="通用的缩略图占位符">
            </a>
        </div>
        ...
    </div>
    <div class="row">
        <div class="col-xs-6">
            <a href="#" class="thumbnail">
                <img src="../source/zhou.jpg" alt="通用的缩略图占位符">
            </a>
        </div>
        ...
    </div>
</div>
```
##### 效果
![](https://i.imgur.com/rtqrN50.png)

## 添加自定义内容

1、 把带有`.thumbnail`的`<a>`标签改为`<div>`
2、 在该`<div>`内，可以添加任何想添加的东西，可以使用默认的基于`span`的命名规则来调整大小
3、 若给多个图像进行分组，将图像放置在一个无序列表中，且每个列表项向左浮动

##### 示例
```html
<div class="container">
    <div class="row">
        <div class="col-xs-6">
            <div class="thumbnail">
                <img src="../source/zhou.jpg"
                     alt="通用的占位符缩略图">
                <div class="caption">
                    <h3>缩略图标签</h3>
                    <p>一些示例文本。一些示例文本。</p>
                    <p>
                        <a href="#" class="btn btn-primary" role="button">
                            按钮
                        </a>
                        <a href="#" class="btn btn-default" role="button">
                            按钮
                        </a>
                    </p>
                </div>
            </div>
        </div>
        <div class="col-xs-6">
            <div class="thumbnail">
                ...
            </div>
        </div>
    </div>
    <div class="row">
        <div class="col-xs-6">
            <div class="thumbnail">
                ...
            </div>
        </div>
        <div class="col-xs-6">
            <div class="thumbnail">
                ...
            </div>
        </div>
    </div>
</div>
```
##### 效果
![](https://i.imgur.com/1QgD8pk.jpg)