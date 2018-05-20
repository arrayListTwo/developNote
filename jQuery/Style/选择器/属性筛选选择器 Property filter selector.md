# jQuery选择器之属性筛选选择器 - Property filter selector

> 属性选择器可以基于属性来定位一个元素，可以只指定该元素的某个属性，这样所有使用该属性而不管它的值，这个元素都将被定位，也可以更加明确并定位在这些属性上使用特定值的元素，这就是属性选择器展示它们的威力的地方

## 属性筛选选择器

* **`$("[attribute|='value']")`：**选择指定属性值等于给定字符串 或 以该文字串为前缀（该字符串后跟一个连字符**"-"**）的元素

* **`$("[attribute*='value']")`：**选择指定属性具有包含一个给定的子字符串的元素（选择给定的属性是以包含某些值的元素）

* **`$("[attribute~='value']")`：**选择指定属性用空格分割的值中包含一个给定值的元素

* **`$("[attribute='value']")`：**选择指定属性是给定值的元素

* **`$("[attribute!='value']")`：**选择不存在指定属性 或者 指定的属性值不等于给定值的元素

* **`$("[attribute^='value']")`：**选择指定属性是以给定字符串开始的元素

* **`$("[attribute$='value']")`：**选择指定属性是以给定值结尾的元素，这个比较是区分大小写的

* **`$("[attribute]")`：**选择所有具有指定属性的元素，该属性可以是任何值

* **`$("[attributeFilter1][attributeFilterN]")`：**选择匹配所有指定的属性筛选器的元素

* **备注**：

	* **`[attr="value"]`** 和 **`[attr*="value"]`**是最实用的
	* **`[attr="value"]`**：能帮我们定位不同类型的元素，特别是表单form元素的操作，如`input[type='text']` ， `input[type='checkbox']`
	* **`[attr*="value"]`**：能在网站中帮助我们匹配不同类型的文件

## 实战

#### 前台

```html
<!DOCTYPE html>
<html>

<head>
    <meta http-equiv="Content-type" content="text/html; charset=utf-8"/>
    <title></title>
    <script src="https://www.imooc.com/static/lib/jquery/1.9.1/jquery.js"></script>
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

        .bottom {
            width: 800px;
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

        .bottom .small {
            width: 60px;
            height: 25px;
            font-size: 12px;
            background: #fab;
        }
    </style>
</head>

<body>
<h2>属性筛选选择器</h2>
<h3>[att=val]、[att]、[att|=val]、[att~=val]</h3>
<div class="left" testattr="true">
    <div class="div" testattr="true" name='p1'>
        <a>[att=val]</a>
    </div>
    <div class="div" testattr="true" p2>
        <a>[att]</a>
    </div>
    <div class="div" testattr="true" name="start-end">
        <a>[att|=val]</a>
    </div>
    <div class="div" testattr="true" name="a b">
        <a>[att~=val]</a>
    </div>
</div>

<script type="text/javascript">
    //查找所有div中，属性name=p1的div元素
    $('div[name=p1]').css("border", "3px groove red");
</script>

<script type="text/javascript">
    //查找所有div中，有属性p2的div元素
    $('div[p2]').css("border", "3px groove blue");
</script>

<script type="text/javascript">
    //查找所有div中，有属性name中的值只包含一个连字符“-”的div元素
    $('div[name|="start"]').css("border", "3px groove #00FF00");
</script>

<script type="text/javascript">
    //查找所有div中，有属性name中的值包含一个连字符“空”和“a”的div元素
    $('div[name~="a"]').css("border", "3px groove #668B8B");
</script>


<h3>[att^=val]、[att*=val]、[att$=val]、[att!=val]</h3>
<div class="left" testattr="true">
    <div class="div" testattr="true" name='imooc-aaorn'>
        <a>[att^=val]</a>
    </div>
    <div class="div" testattr="true" name='aaorn-imooc'>
        <a>[att$=val]</a>
    </div>
    <div class="div" testattr="true" name="attr-test-selector">
        <a>[att*=val]</a>
    </div>
    <div class="div" name="a b">
        <a>[att!=val]</a>
    </div>
    <div class="div" testattr="false">
        <a>[att*=val]</a>
    </div>

</div>


<script type="text/javascript">
    //查找所有div中，属性name的值是用imooc开头的
    $('div[name^=imooc]').css("border", "3px groove red");
</script>

<script type="text/javascript">
    //查找所有div中，属性name的值是用imooc结尾的
    $('div[name$=imooc]').css("border", "3px groove blue");
</script>

<script type="text/javascript">
    //查找所有div中，有属性name中的值包含一个test字符串的div元素
    $('div[name*="test"]').css("border", "3px groove #00FF00");
</script>

<script type="text/javascript">
    //查找所有div中，有属性testattr中的值没有包含"true"的div
    $('div[testattr!="true"]').css("border", "3px groove #668B8B");
</script>

</body>

</html>
```

#### 效果

![](https://i.imgur.com/OEPUsOx.png)