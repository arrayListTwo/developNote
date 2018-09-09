# 修改DOM结构

## 添加DOM

* 要添加新的DOM节点，除了通过JQuery的`html()`暴力方法以外，还可以使用`append()`方法：

* `append()`方法可以传入**字符串**、**`DOM`对象**、**`jQuery`对象**、**函数对象**

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

* `after()`方法：新的节点插入到指定元素后面

* `before()`方法：新的节点插入到指定元素前面

## 删除节点

* 拿到jQuery对象后直接调用`remove()`方法，即可删除DOM节点。如果jQuery对象包含若干DOM节点，实际上可以一次删除多个DOM节点

```JavaScript
var li = $('#test-div>ul>li');
li.remove(); // 所有<li>全被删除
```