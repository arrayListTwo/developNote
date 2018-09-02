# 更新DOM

> 拿到一个DOM节点后，我们可以对它进行更新

* 修改`innerHTML`属性，这个方式非常强大，不但可以修改一个DOM节点的文本内容，还可以直接**通过HTML片段修改DOM节点内部的子树**
```JavaScript
// 获取<p id="p-id">...</p>
var p = document.getElementById('p-id');
// 设置文本为abc:
p.innerHTML = 'ABC'; // <p id="p-id">ABC</p>
// 设置HTML:
p.innerHTML = 'ABC <span style="color:red">RED</span> XYZ';
// <p>...</p>的内部结构已修改
```

**注意：**如果写入的字符串是通过网络拿到了，可能会插入一段js代码，要注意**对字符编码来避免XSS攻击**

* 修改`innerText`或`textContent`属性，此种方式会自动对字符串进行HTML编码，保证无法设置任何HTML标签(包括引入js代码)
```JavaScript
// 获取<p id="p-id">...</p>
var p = document.getElementById('p-id');
// 设置文本:
p.innerText = '<script>alert("Hi")</script>';
// HTML被自动编码，无法设置一个<script>节点:
// <p id="p-id">&lt;script&gt;alert("Hi")&lt;/script&gt;</p>
```

**区别：**读取属性时，`innerText`不返回隐藏元素的文本，而`textContent`返回所有文本。另外注意**`IE<9`不支持`textContent`**

* 修改CSS属性
	* DOM节点的`style`属性对应所有的CSS，可以直接获取或者设置
	* 使用`style`属性修改CSS时，css属性统一改为**驼峰式命名**
```JavaScript
// 获取<p id="p-id">...</p>
var p = document.getElementById('p-id');
// 设置CSS:
p.style.color = '#ff0000';
p.style.fontSize = '20px';
p.style.paddingTop = '2em';
```