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

* 拿到jQuery对象后直接调用`remove()`方法，即可删除DOM节点。如果jQuery对象包含若干DOM节点，实际上可以一次删除多个DOM节点，包括绑定的事件及与该元素相关的jQuery数据(包括内部所有节点)
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

#### 保留数据的删除

* `detach()`方法，让一个web元素托管。即从当前页面中移除该元素，但保留这个元素的内存模型对象（包括内部所有节点）。

* `$("div").detach()`，调用此方法会移除对象，但仅仅是显示效果的删除，对象依然存在内存中，对象所有绑定的事件、附加的数据都会保存下来
	* `detach()`是jQuery特有的，它只能处理通过jQuery的方法绑定的事件或者数据

## `clone()`实现拷贝

* `.clone()`方法复制所有匹配的元素集合，包括所有匹配元素、匹配元素的下级元素、文字节点

* `.clone(true)`方法不仅实现复制节点结构，还会把附带的事件和数据一并克隆
	* `clone()`方法是jQuery扩展的，只能处理通过jQuery绑定的事件和数据
	* 元素数据`data`内对象和数组不会被复制，将继续被克隆元素和原始元素共享

## 替换

* `.replaceWith(newContent)`：用提供的内容替换集合中所有匹配的元素并且**返回被删除元素的集合**

* `.replaceAll(target)`:功能相似，目标和源相反

* `.replaceAll()`和`.replaceWith()`功能类似，主要是目标和源的位置区别

* `.replaceWith()`与`.replaceAll()` 方法会删除与节点相关联的所有数据和事件处理程序

## 包裹`wrap()`方法，相当于生成父结构

> 将元素用其他元素包裹起来，也就是给它增加一个父元素，集合中的每个元素都增加父结构

* `.wrap(wrappingElement)`:在集合中匹配的每个元素周围包裹一个HTML结构

```JavaScript
$('p').wrap('<div></div>');
```

* `.wrap(function)`：一个回调函数，返回用于包裹匹配元素的HTML内容或者jQuery对象

```JavaScript
$('p').wrap(function(){
	return '<div></div>';
});
```

* 方法返回原始的元素集，以便使用链式方法

* `.wrap()`函数可以接受任何字符串或对象，可以传递给`$()`工厂函数来指定一个DOM结构

## 删除父结构`.unwrap()`方法

* 将匹配元素集合的父级元素删除，保留自身（和兄弟元素，如果存在）在原来的位置

## `wrapAll()`方法，集合元素只添加一个父元素

* `.wrapAll(content)`将集合中的所有元素增加一个父元素

```JavaScript
<!--HTML结构-->
<p>p元素</p>
<span>span元素</span>
<p>p元素</p>
<!--jQuery代码-->
$('p').wrapAll('<div></div>');
<!--形成的HTML结构-->
<div>
	<p>p元素</p>
	<p>元素</p>
</div>
<span>span元素</span>
```

**注意：**`.wrapAll(content)`方法，所有符合的集合元素只会生成一个父元素，集合中后面的元素自动移动到后面

* `.wrapAll(function)`方法，类似于`wrap()`方法，一个元素一个元素的增加父元素

## `wrapInner()`方法，给集合中所有子元素添加父元素

* `.wrapInner(wrappingElement)`

```JavaScript
<div><a>a元素</a><span>span元素</span></div>
$("div").wrapInner("<p></p>");
// 结果
<div>
	<p>
		<a>a元素</a><span>span元素</span>
	</p>
</div>
```

* `.wrapInner( function )` ：允许我们用一个callback函数做参数，每次遇到匹配元素时，该函数被执行，返回一个DOM元素，jQuery对象，或者HTML片段，用来包住匹配元素的内容
