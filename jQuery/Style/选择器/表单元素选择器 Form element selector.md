# JQuery选择器之表单元素选择器 - Form element selector

## 表单元素选择器

* **`$(":input")`：**选择所有`input`、`textarea`、`select`、和`button`元素

* **`$(":text")`：**匹配所有文本框

* **`$(":password")`：**匹配所有密码

* **`$(":radio")`：**匹配所有单选按钮

* **`$(":checkbox")`：**匹配多有复选框

* **`$(":submit")`：**匹配所有提交按钮

* **`$(":image")`：**匹配所有提交按钮

* **`$(":reset")`：**匹配所有重置按钮

* **`$(":button")`：**匹配所有按钮

* **`$(":file")`：**匹配所有文件域

* **备注：**
	* 除了`input`筛选选择器，几乎每个表单类别筛选器都对应一个`input`元素的`type`值，大部分表单类别筛选器可以使用**属性筛选器**替换。比如：`$(":password") == $("[type=password]")`

## 实战

#### 前台

```html
<!DOCTYPE html>
<html>
<head>
    <meta http-equiv="Content-type" content="text/html; charset=utf-8"/>
    <title></title>
    <style>
        input {
            display: block;
            margin: 10px;
            padding: 10px;
        }
    </style>
    <script src="http://libs.baidu.com/jquery/1.9.1/jquery.js"></script>
</head>

<body>
<h2>子元素筛选选择器</h2>
<h3>input、text、password、radio、checkbox</h3>
<h3>submit、image、reset、button、file</h3>
<div class="left first-div">
    <form>
        <input type="text" value="text类型"/>
        <input type="password" value="password"/>
        <input type="radio"/>
        <input type="checkbox"/>
        <input type="submit"/>
        <input type="image" src="../../res/img/wei.png"/>
        <input type="reset"/>
        <input type="button" value="Button"/>
        <input type="file"/>
    </form>
</div>

<script type="text/javascript">
    //查找所有 input, textarea, select 和 button 元素
    //:input 选择器基本上选择所有表单控件
    $(':input').css("border", "1px groove red");
</script>

<script type="text/javascript">
    //匹配所有input元素中类型为text的input元素
    $('input:text').css("background", "#A2CD5A");
</script>

<script type="text/javascript">
    //匹配所有input元素中类型为password的input元素
    $('input:password').css("background", "yellow");
</script>

<script type="text/javascript">
    //匹配所有input元素中的单选按钮,并选中
    $('input:radio').attr('checked', 'true');
</script>

<script type="text/javascript">
    //匹配所有input元素中的复选按钮,并选中
    $('input:checkbox').attr('checked', 'true');
</script>

<script type="text/javascript">
    //匹配所有input元素中的提交的按钮,修改背景颜色
    $('input:submit').css("background", "#C6E2FF");
</script>

<script type="text/javascript">
    //匹配所有input元素中的图像类型的元素,修改背景颜色
    $('input:image').css("background", "#F4A460");
</script>

<script type="text/javascript">
    //匹配所有input元素中类型为按钮的元素
    $('input:button').css("background", "red");
</script>

<script type="text/javascript">
    //匹配所有input元素中类型为file的元素
    $('input:file').css("background", "#CD1076");
</script>

</body>

</html>
```

#### 效果

![](https://i.imgur.com/MsniSR1.png)