# 修改DOM结构

## 创建元素节点

* 直接把这个节点的结构通过HTML标记字符串描述出来，通过`$()`函数处理，`$("html结构")`

	```JavaScript
	// 创建一个div标签元素
	var $div = $("<div></div>");
	// 直接创建一个文本节点
	var $text = $("<div>我是文本节点</div>");
	// 创建时指定属性
	var $att = $("<div id='text' class='array'>我含有属性</div>");
	```

## 添加DOM

#### 形成父子关系

* 要添加新的DOM节点，除了通过JQuery的`html()`暴力方法以外，还可以使用`append()`方法：

* `$(A).append(B)`方法可以传入**字符串**、**`DOM`对象**、**`jQuery`对象**、**函数对象**，添加至最后一个元素位置
* `$(B).appendTo(A)`：颠倒了常规的`$(A).append(B)`，实现的依然是`A`对象添加到`B`对象中，添加至最后一个元素位置
```JavaScript
/* 传入HTML字符串 */
$ul.append('<li><span>Haskell</span></li>');
/* 传入DOM对象 */
// 创建DOM对象:
var ps = document.createElement('li');
ps.innerHTML = '<span>Pascal</span>';
// 添加DOM对象:
$ul.append(ps);
/* 传入jQuery对象 */
// 添加jQuery对象:
$ul.append($('#scheme'));
/* 传入函数，函数的返回值可以是：HTML字符串、DOM对象、jQuery对象
因为jQuery的append()可能作用于一组DOM节点，只有传入函数才能针对每个DOM生成不同的子节点。 */
// 添加函数对象:
$ul.append(function (index, html) {
    return '<li><span>Language - ' + index + '</span></li>';
});
```
**注意：**如果要添加的DOM节点已经存在于HTML文档中，它会首先从文档移除，然后再添加，也就是说，用`append()`，你可以移动一个DOM节点

* `parent.prepend(content)`：添加至第一个元素

* `content.prependTo(parent)`：功能等同，添加至第一个元素

#### 形成相邻兄弟关系

###### 新的节点插入到指定元素后面

* `$ele.after(content)`方法：新的节点插入到指定元素后面

* `content.insertAfter($ele)`方法：等同于上面方法，参数不同

###### 新节点插入到指定元素前面

* `$ele.before(content)`方法：新的节点插入到指定元素前面

* `content.insertBefore($ele)`方法：等同于上面方法，参数不同

## 删除节点

#### remove 删除节点

* 拿到jQuery对象后直接调用`remove()`方法，即可删除DOM节点。如果jQuery对象包含若干DOM节点，实际上可以一次删除多个DOM节点，包括绑定的事件及与该元素相关的jQuery数据
```JavaScript
var li = $('#test-div>ul>li');
li.remove(); // 所有<li>全被删除
```

* `remove()`可以传递一个选择器表达式用来过滤将被移除的匹配元素集合，可以实现选择性的删除指定的节点

```JavaScript
$("p").filter(":contains('3')").remove();
 // 等同于
$("p").remove(":contains('3')");
```

#### empty 清空节点

* `empty()`方法不同于删除，它只移除指定元素中的所有子节点（包括其他后代元素、元素里的文本），即元素本身存在（属性依旧存在，但内容全部删除了）