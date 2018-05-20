# JQuery选择器之特殊选择器this - this selector

> **`this`**是`JavaScript`中的关键字，指的是当前的上下文对象，简单的说就是方法/属性的所有者

> **`JavaScript`**中的**`this`**是动态的，也就是说这个上下文对象都是可以被动态改变的，可以通过`call`和`apply`方法

## this转换成jQuery中的对象

```js
var $this = $(this);
```

* **`this`：**表示当前的上下文对象是一个html对象，可以调用html对象所拥有的属性和方法

* **`$this`：**代表的上下文对象是一个jQuery的上下文对象，可以调用jQuery的方法和属性值

## 实战

#### 前台

```html
<!DOCTYPE html>
<html>

<head>
    <meta http-equiv="Content-type" content="text/html; charset=utf-8"/>
    <title></title>
    <script src="https://www.imooc.com/static/lib/jquery/1.9.1/jquery.js"></script>
</head>

<body>
<h2>特殊选择器this</h2>

<p id="test1">点击测试：通过原生DOM处理</p>

<p id="test2">点击测试：通过原生jQuery处理</p>

<script type="text/javascript">
    var p1 = document.getElementById('test1');
    p1.addEventListener('click', function () {
        //直接通过dom的方法改变颜色
        this.style.color = "red";
    }, false);
</script>

<script type="text/javascript">
    $('#test2').click(function () {
        //通过包装成jQuery对象改变颜色
        $(this).css('color', 'blue');
    })
</script>

</body>

</html>
```
#### 效果

![](https://i.imgur.com/co3zhDz.png)