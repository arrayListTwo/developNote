# jQuery选择器之可见性筛选选择器 - Visibility filter selector

> 元素有显示状态与隐藏状态，jQuery根据元素的状态扩展了可见性筛选选择器:**`:visible`**与**`:hidden`**

## css隐藏元素的方式

* CSS中`display`的值为`none`

* `type="hidden"`的表单元素

* 宽度和高度都显示设置为 **0**

* 一个祖先元素是隐藏的，该元素是不会在页面上显示

* CSS中`visibility`的值是`hidden`；（页面中占据空间）

* CSS中`opacity`的值是**0**；（页面中占据空间）

* #### 备注：

	* 如果元素占据文档中一定的空间，元素被认为是可见的，可见元素的宽度或高度，是大于零的

	* 元素的`visibility: hidden` 或 `opacity: 0` ，被认为是可见的，因为他们仍然占用空间布局

## `$(":visible")`

* 选择所有显示的元素

## `$(":hidden")`

* 选择所有隐藏的元素

## 实战

#### 前台

```html
<!DOCTYPE html>
<html>

<head>
    <meta http-equiv="Content-type" content="text/html; charset=utf-8"/>
    <title></title>
    <script src="http://libs.baidu.com/jquery/1.9.1/jquery.js"></script>
    <style>
        .left {
            width: auto;
            height: 120px;
        }

        .left div {
            width: 100px;
            height: 70px;
            padding: 5px;
            margin: 5px;
            float: left;
            background: #bbffaa;
            border: 1px solid #ccc;
        }

        .bottom div,
        .bottom span {
            display: block;
            width: 80px;
            height: 80px;
            margin: 5px;
            background: #bbffaa;
            float: left;
            font-size: 14px;
        }
    </style>
</head>

<body>
<h2>可见性筛选选择器</h2>
<h3>:visible/:hidden</h3>
<div class="left">
    <div class="div">
        <a>display</a>
        <p id="div1" style="display:none;">display</p>
    </div>
    <div class="div">
        <a>width</a>
        <a>height</a>
        <p id="div2" style="width:0;height:0">width/height</p>
    </div>
    <div class="div">
        <a>visibility</a>
        <a>opacity</a>
        <p id="div3" style="visibility:hidden;opacity:0">visibility</p>
    </div>
</div>

<p id="show"></p>
<script type="text/javascript">
    function show(ele) {
        if (ele instanceof jQuery) {
            $("#show").html($("#show").html() + '元素的长度的 = ' + ele.length + " <br>");
        } else {
            alert(ele + ' 不是jQuery对象')
        }
    }
</script>


<script type="text/javascript">
    //查找id = div1的DOM元素,是否可见
    show($('#div1:visible'));
</script>

<script type="text/javascript">
    //查找id = div2的DOM元素,是否可见
    show($('#div2:visible'));
</script>

<script type="text/javascript">
    //查找id = div3的DOM元素,是否可见
    show($('#div3:visible'));
</script>

<script type="text/javascript">
    //查找id = div1的DOM元素,是否隐藏
    show($('#div1:hidden'));
</script>

<script type="text/javascript">
    //查找id = div2的DOM元素,是否隐藏
    show($('#div2:hidden'));
</script>

<script type="text/javascript">
    //查找id = div3的DOM元素,是否隐藏
    show($('#div3:hidden'));
</script>

</body>

</html>
```

#### 效果

![](https://i.imgur.com/Cyww7aK.png)