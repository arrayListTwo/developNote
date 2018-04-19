# Bootstrap 警告（Alerts）

> 警告（Alerts）向用户提供了一种定义消息样式的方式。它们为典型的用户操作提供了上下文信息反馈

## 基本的警告框

#### 步骤

* 创建一个 `<div>`，并向其添加一个 `.alert` 和四个上下文 class（即 `.alert-success`、`.alert-info`、`.alert-warning`、`.alert-danger`）之一，来添加一个基本的警告框。

##### 示例
```html
<div class="alert alert-success">成功！很好地完成了提交。</div>
<div class="alert alert-info">信息！请注意这个信息。</div>
<div class="alert alert-warning">警告！请不要提交。</div>
<div class="alert alert-danger">错误！请进行一些更改。</div>
```
##### 效果
![](https://i.imgur.com/QWutHXO.png)

## 可取消的警告（Dismissal Alerts）

#### 步骤
1、 通过创建一个 `<div>`，并向其添加一个 `.alert` 和四个上下文 class（即 `.alert-success`、`.alert-info`、`.alert-warning`、`.alert-danger`）之一，来添加一个基本的警告框
2、同时向上面的 `<div>` class 添加可选的 .alert-dismissable
3、添加一个关闭按钮。**务必使用带有 `data-dismiss="alert"` data 属性的 `<button>` 元素**

##### 示例
```html
<div class="alert alert-success alert-dismissable">
    <button type="button" class="close" data-dismiss="alert"
            aria-hidden="true">
        &times;
    </button>
    成功！很好地完成了提交。
</div>
<div class="alert alert-info alert-dismissable">
	...
</div>
<div class="alert alert-warning alert-dismissable">
	...
</div>
<div class="alert alert-danger alert-dismissable">
	...
</div>
```
##### 效果
![](https://i.imgur.com/AevffHz.png)

## 警告中的链接

#### 步骤

1、 通过创建一个 `<div>`，并向其添加一个 `.alert` 和四个上下文 class（即 `.alert-success`、`.alert-info`、`.alert-warning`、`.alert-danger`）之一，来添加一个基本的警告框
2、 使用 `.alert-link` 实体类来快速提供带有匹配颜色的链接

##### 示例
```html
<div class="alert alert-success">
    <a href="#" class="alert-link">成功！很好地完成了提交。</a>
</div>
<div class="alert alert-info">
    <a href="#" class="alert-link">信息！请注意这个信息。</a>
</div>
<div class="alert alert-warning">
    <a href="#" class="alert-link">警告！请不要提交。</a>
</div>
<div class="alert alert-danger">
    <a href="#" class="alert-link">错误！请进行一些更改。</a>
</div>
```
##### 效果
![](https://i.imgur.com/Zw4mfYO.png)