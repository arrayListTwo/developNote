# JQuery选择器之基本筛选选择器 - Basic filter selector

> 筛选器很多不是css的规范，而是jQuery自己为了开发者的便利延展出来的选择器

> 基本筛选选择器针对的是**元素DOM节点**

## 基本筛选选择器

* **`$(":first")`：**匹配第一个元素

* **`$(":last")`：**匹配最后一个元素

* **`$(":not(selector)")`:**一个用来过滤的选择器，选择所有元素去除不匹配给定的选择器元素

* **`$(":eq(index)")`:**在匹配的集合中选择索引值为index的元素

* **`$(":gt(index)")`:**选择匹配集合中所有大于给定index（索引值）的元素

* **`$(":even")`:**选择索引值为偶数的元素，从 0 开始计数

* **`$(":odd")`:**选择索引值为奇数的元素，从 0 开始计数

* **`$(":lt(index)")`:**选择匹配集合中所有索引值小于给定index参数的元素

## 总结

* **`:eq()`**、**`:lt()`**、**`:gt()`**、**`:odd`**，用来筛选他们前面的匹配表达式的集合元素，**根据之前匹配的元素再进一步筛选**

* jQuery合集都是从 0 开始的索引

## 实践

#### 前台

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        .left {
            width: auto;
            height: 120px;
        }

        .left div {
            width: 70px;
            height: 70px;
            padding: 5px;
            margin: 5px;
            float: left;
            background: #bbffaa;
            border: 1px solid #ccc;
        }

    </style>
    <script src="https://cdn.bootcss.com/jquery/1.9.1/jquery.js"></script>
</head>
<body>
<h2>基本筛选器</h2>
<h3>:first/:last/:even/:odd</h3>
<div class="left">
    <div class="div">
        <p>div:first</p>
        <p>:even</p>
    </div>
    <div class="div">
        <p>:odd</p>
    </div>
    <div class="div">
        <p>:even</p>
    </div>
    <div class="div">
        <p>:odd</p>
    </div>
    <div class="div">
        <p>:even</p>
    </div>
    <div class="div">
        <p>div:last</p>
        <p>:odd</p>
    </div>
</div>
<script type="text/javascript">
    //找到第一个div
    $(".div:first").css("color", "#CD00CD");
</script>

<script type="text/javascript">
    //找到最后一个div
    $(".div:last").css("color", "#CD00CD");
</script>

<script type="text/javascript">
    //:even 选择所引值为偶数的元素，从 0 开始计数
    $(".div:even").css("border", "3px groove red");
</script>

<script type="text/javascript">
    //:odd 选择所引值为奇数的元素，从 0 开始计数
    $(".div:odd").css("border", "3px groove blue");
</script>


<h3>:eq/:gt/:lt</h3>
<div class="left">
    <div class="aaron">
        <p>:lt(3)</p>
    </div>
    <div class="aaron">
        <p>:lt(3)</p>
    </div>
    <div class="aaron">
        <p>:eq(2)</p>
    </div>
    <div class="aaron">
    </div>
    <div class="aaron">
        <p>:gt(3)</p>
    </div>
    <div class="aaron">
        <p>:gt(3)</p>
    </div>
</div>
<script type="text/javascript">
    //:eq
    //选择单个
    $(".aaron:eq(2)").css("border", "3px groove blue");
</script>

<script type="text/javascript">
    //:gt 选择匹配集合中所有索引值大于给定index参数的元素
    $(".aaron:gt(3)").css("border", "3px groove blue");
</script>

<script type="text/javascript">
    //:lt 选择匹配集合中所有索引值小于给定index参数的元素
    //与:gt相反
    $(".aaron:lt(2)").css("color", "#CD00CD");
</script>

<h3>:not</h3>
<div class="left">
    <div>
        <input type="checkbox" name="a"/>
        <p>Aaron</p>
    </div>
    <div>
        <input type="checkbox" name="b"/>
        <p>慕课</p>
    </div>
    <div>
        <input type="checkbox" name="c" checked="checked"/>
        <p>其他</p>
    </div>
</div>
<script type="text/javascript">
    //:not 选择所有元素去除不匹配给定的选择器的元素
    //选中所有紧接着没有checked属性的input元素后的p元素，赋予颜色
    $("input:not(:checked) + p").css("background-color", "#CD00CD");
</script>
</body>
</html>
```

#### 效果

![](https://i.imgur.com/3ph58aX.png)