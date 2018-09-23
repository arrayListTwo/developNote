# 操作DOM

## 修改和获取`Text`、`HTML`

* `jQuery`对象无参数的`text()`和`html()`分别获取节点的文本和原始HTML文本

```JavaScript
<!-- HTML结构 -->
<ul id="test-ul">
    <li class="js">JavaScript</li>
    <li name="book">Java &amp; JavaScript</li>
</ul>
// jQuery获取文本和HTML
$('#test-ul li[name=book]').text(); // 'Java & JavaScript'
$('#test-ul li[name=book]').html(); // 'Java &amp; JavaScript'
```

* 有参数的`text('str')`和`html('<span>...</span>')`，设置文本和HTML

```JavaScript
'use strict';
var j1 = $('#test-ul li.js');
var j2 = $('#test-ul li[name=book]');
// 设置文本和HTML
j1.html('<span style="color: red">JavaScript</span>');
j2.text('JavaScript & ECMAScript');
// 查看
console.log(j1.text()); // JavaScript
console.log(j2.html()); // JavaScript &amp; ECMAScript
```
* `jQuery`对象可以包含0个或者任意个DOM对象，它的方法实际上会作用在对应的每个DOM节点上

```JavaScript
$('#test-ul li').text('JS'); // 符合选择器的DOM节点文本都将设置JS
```
**注意：**即使`jQuery`对象是空`[]`，也不会报错

## 修改CSS

> `jQuery`对象是集合操作也支持链式操作

> `css()`方法将作用于DOM节点的`style`属性，具有最高优先级

* 修改css，调用`jQuery`对象的`css('name', 'value')`方法

```JavaScript
$('#test-css li.dy>span').css('background-color', '#ffd351').css('color', 'red');
```

* `jQuery`对象的`css()`方法

```JavaScript
var div = $('#test-div');
div.css('color'); // '#000033', 获取CSS属性
div.css('color', '#336699'); // 设置CSS属性
div.css('color', ''); // 清除CSS属性
```

* 修改`class`属性

```JavaScript
var div = $('#test-div');
div.hasClass('highlight'); // false， class是否包含highlight
div.addClass('highlight'); // 添加highlight这个class
div.removeClass('highlight'); // 删除highlight这个class
```

## 显示和隐藏DOM

> 隐藏`DOM`节点并未改变`DOM`树的结构，它只影响`DOM`节点的显示，和删除`DOM`节点是不同的

* `hide()`：隐藏

* `show()`:显示

## 获取DOM信息

* 利用`jQuery`对象的若干方法，我们直接可以获取DOM的高宽等信息

```JavaScript
// 浏览器可视窗口大小:
$(window).width(); // 800
$(window).height(); // 600

// HTML文档大小:
$(document).width(); // 800
$(document).height(); // 3500

// 某个div的大小:
var div = $('#test-div');
div.width(); // 600
div.height(); // 300
div.width(400); // 设置CSS属性 width: 400px，是否生效要看CSS是否有效
div.height('200px'); // 设置CSS属性 height: 200px，是否生效要看CSS是否有效
```

* `attr()`和`removeAttr()`方法用于操作DOM节点的属性

```JavaScript
// <div id="test-div" name="Test" start="1">...</div>
var div = $('#test-div');
div.attr('data'); // undefined, 属性不存在
div.attr('name'); // 'Test'
div.attr('name', 'Hello'); // div的name属性变为'Hello'
div.removeAttr('name'); // 删除name属性
div.attr('name'); // undefined
```

## 操作表单

* 对于表单元素，`jQuery`对象统一提供`val()`方法获取和设置对应的value属性

* `.trim()`去除字符串两端的空白字符

```JavaScript
/*
    <input id="test-input" name="email" value="">
    <select id="test-select" name="city">
        <option value="BJ" selected>Beijing</option>
        <option value="SH">Shanghai</option>
        <option value="SZ">Shenzhen</option>
    </select>
    <textarea id="test-textarea">Hello</textarea>
*/
var
    input = $('#test-input'),
    select = $('#test-select'),
    textarea = $('#test-textarea');

input.val(); // 'test'
input.val('abc@example.com'); // 文本框的内容已变为abc@example.com

select.val(); // 'BJ'
select.val('SH'); // 选择框已变为Shanghai

textarea.val(); // 'Hello'
textarea.val('Hi'); // 文本区域已更新为'Hi'
```

