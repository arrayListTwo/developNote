# BootStrap CSS （一）

> Bootstrap 3 的设计目标是移动设备优先，然后才是桌面设备。这实际上是一个非常及时的转变，因为现在越来越多的用户使用移动设备。

### 设置视图宽度等于屏幕宽度并且不能进行缩放

* 在网页的 `head` 之中添加 `viewport` `meta` 标签
```css
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no">
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