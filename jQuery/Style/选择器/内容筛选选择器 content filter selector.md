# JQuery选择器之内容筛选选择器 - content filter selector

> jQuery提供了一组内容筛选选择器，其规则也会体现在它所包含的子元素或者文本内容上

## 内容筛选选择器

* **`$(":contains(text)")`：**选择所有包含指定文本的元素

* **`$(":parent")`：**选择所有含有子元素或者文本的元素

* **`$(":empty")`：**选择所有没有子元素的元素，文本节点属于元素

* **`$(":has(selector)")`:**选择元素中至少包含指定选择器的元素

## 总结：

* **`:contains`** 与 **`:has`** 都有查找的意思，但是contains查找包含"指定文本"的元素；has查找包含"指定元素"的元素

* 如果**`:contains`**匹配的文本包含在元素的子元素中，同样认为是符合条件的

* **`:parent`** 与 **`:empty`** 是相反的，两者所涉及的子元素，包括文本节点

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
    <script src="https://cdn.bootcss.com/jquery/1.9.1/jquery.js"></script>
</head>
<body>
<h2>内容筛选器</h2>
<h3>:contains/:has</h3>
<div class="left">
    <div class="div">
        <p>:contains</p>
    </div>
    <div class="div">
        <p>:contains</p>
    </div>
    <div class="div">
        <p>
            <span>:has</span>
        </p>
    </div>
    <div class="div">
        <p>:contains</p>
    </div>
</div>

<script type="text/javascript">
    //查找所有class='div'中DOM元素中包含"contains"的元素节点
    //并且设置颜色
    $(".div:contains(':contains')").css("background-color", "#CD00CD");
</script>

<script type="text/javascript">
    //查找所有class='div'中DOM元素中包含"span"的元素节点
    //并且设置颜色
    $(".div:has(span)").css("background-color", "#fff");
</script>


<h3>:parent/:empty</h3>
<div class="left">
    <div class="aaron">
        <a>:parent</a>
    </div>
    <div class="aaron">
        <a>:parent</a>
    </div>
    <div class="aaron">
        <a>:parent</a>
    </div>
    <div class="aaron">
        <a></a>
    </div>
</div>
<script type="text/javascript">
    //选择所有包含子元素或者文本的a元素
    //增加一个蓝色的边框
    $("a:parent").css("border", "3px groove blue");
</script>

<script type="text/javascript">
    //找到a元素下面的所有空节点(没有子元素)
    //增加一段文本与边框
    $("a:empty").text(":empty").css("border", "3px groove red");
</script>
</body>
</html>
```

#### 效果

![](https://i.imgur.com/hBJ8r71.png)