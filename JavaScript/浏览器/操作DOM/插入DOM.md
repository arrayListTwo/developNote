# 插入DOM

> 获取某个DOM节点，就可以在此DOM节点内插入新的DOM

* 直接使用`innerHTML`属性插入`HTML`代码

* 使用方法`appendChild()`，实现把一个子节点添加到父节点的最后一个子节点
	* 如果欲插入的节点是在页面中获取的，会首先在页面原先的位置中删除此DOM节点，然后再实现在新的位置插入DOM节点的操作
	* 常用情况，插入一个新的节点
		* 插入一个新的节点：
		```JavaScript
		var
	    list = document.getElementById('list'),
		// 创建一个element对象
	    haskell = document.createElement('p');
		// 设置属性以及内容
		haskell.id = 'haskell';
		haskell.innerText = 'Haskell';
		// 插入到父节点list的最后一个子节点
		list.appendChild(haskell);
		```
		* 动态创建一个`style`节点，然后把它添加到`<head>`节点的末尾，实现动态给文档添加新的CSS定义
		```JavaScript
		var d = document.createElement('style');
		d.setAttribute('type', 'text/css');
		d.innerHTML = 'p { color: red }';
		document.getElementsByTagName('head')[0].appendChild(d);
		```
* `parentElement.insertBefore(newElement, referenceElement);`实现在子节点`referenceElement`之前插入元素`newElement`
```JavaScript
var
    list = document.getElementById('list'),
    ref = document.getElementById('python'),
    haskell = document.createElement('p');
haskell.id = 'haskell';
haskell.innerText = 'Haskell';
// 实现在父元素`list`中插入一个元素，并且此元素在`ref`之前
list.insertBefore(haskell, ref);
```
	* 使用`insertBefore`重点是要拿到一个**“参考子节点”**的引用。很多时候，需要循环一个父节点的所有子节点，可以通过**迭代`children`属性**实现：
	```JavaScript
	var
	i, c,
	list = document.getElementById('list');
	for (i = 0; i < list.children.length; i++) {
	    c = list.children[i]; // 拿到第i个子节点
	}
```