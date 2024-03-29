# jQuery选择器之表单对象属性筛选选择器 - The form object property filters the selector

> 除了表单元素选择器外，表单对象属性筛选选择器也是专门针对表单元素的选择器，可以附加在其他选择器的后面，主要功能是对所选择的的表单元素进行筛选

## 表单对象属性筛选选择器

* **`$(":enabled")`:**选取可用的表单元素

* **`$(":disabled")`:**选取不可用的表单元素

* **`$(":checked")`:**选取被选中的`<input>`元素

* **`$(":selected")`:**选取被选中的`<option>`元素

* * **备注：**
	
	* 在某些浏览器中，选择器**`:checked`**可能会引起错误的选取到**`<option>`**元素，所以保险起见换用选择器**`input:checked`**，确保只会选取**`<input>`**元素

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
    <script src="https://www.imooc.com/static/lib/jquery/1.9.1/jquery.js"></script>
</head>

<body>
<h2>子元素筛选选择器</h2>
<h3>enabled、disabled</h3>
<form>
    <input type="text" value="未设置disabled"/>
    <input type="text" value="设置disabled" disabled="disabled"/>
    <input type="text" value="未设置disabled"/>
</form>

<script type="text/javascript">
    //查找所有input所有可用的（未被禁用的元素）input元素。
    $('input:enabled').css("border", "2px groove red");
</script>

<script type="text/javascript">
    //查找所有input所有不可用的（被禁用的元素）input元素。
    $('input:disabled').css("border", "2px groove blue");
</script>

<h3>checked、selected</h3>
<form>
    <input type="checkbox" checked="checked">
    <input type="checkbox">
    <input type="radio" checked>
    <input type="radio">

    <select name="garden" multiple="multiple">
        <option>imooc</option>
        <option selected="selected">慕课网</option>
        <option>aaron</option>
        <option selected="selected">博客园</option>
    </select>

</form>

<script type="text/javascript">
    //查找所有input所有勾选的元素(单选框,复选框)
    //移除input的checked属性
    $('input:checked').removeAttr('checked')
</script>

<script type="text/javascript">
    //查找所有option元素中,有selected属性被选中的选项
    //移除option的selected属性
    $('option:selected').removeAttr('selected')
</script>

</body>

</html>
```

#### 效果

![](https://i.imgur.com/oN65bY6.png)