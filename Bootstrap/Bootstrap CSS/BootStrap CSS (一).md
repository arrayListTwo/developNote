# Bootstrap CSS （一）

> **Bootstrap 3 的设计目标是移动设备优先**，然后才是桌面设备。这实际上是一个非常及时的转变，因为现在越来越多的用户使用移动设备。

### 设置视图宽度等于屏幕宽度并且不能进行缩放（zooming）

* 在网页的 `head` 之中添加 `viewport` `meta` 标签
```css
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no">
```
## 布局容器

> `Bootstrap` 需要为页面内容和栅格系统包裹一个 `.container` 容器。我们提供了两个作此用处的类。注意，**由于 padding 等属性的原因，这两种容器类不能互相嵌套**

* `.container` 类用于固定宽度并`支持响应式布局`的容器。
```html
<div class="container">
  ...
</div>
```
* `.container-fluid` 类用于 100% 宽度，占据全部视口（viewport）的容器。
```html
<div class="container-fluid">
  ...
</div>
```


## 响应式图像

> 通过添加 `img-responsive` 类可以让BootStrap3中的图像对响应式支持的布局更友好
> 如果需要让使用了 `img-responsive` 类的图片水平居中，请使用 `center-block` 类，**不要用 .text-center**

```css
.img-responsive {
  display: block;
  height: auto;
  max-width: 100%;
}
```