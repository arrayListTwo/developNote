# 操作DOM

> HTML文档被浏览器解析后就是一棵DOM树，要改变HTML结构，就需要通过JavaScript来操作DOM

> 根节点Document已经自动绑定为全局变量document

## 常见操作

* 更新：更新该DOM节点的内容，相当于更新了该DOM节点表示的HTML内容

* 遍历：遍历该DOM节点下的子节点，以便进行进一步操作

* 添加：在该DOM节点下新增一个子节点，相当于动态增加了一个HTML节点

* 删除：将该节点从HTML中删除，相当于删掉了该DOM节点的内容以及它包含的所有子节点

## 获取DOM节点

* 通过ID属性，直接定义一个唯一的DOM节点：`document.getElementById()`

* 通过HTML标签名称，获取一组DOM节点：`document.getElementsByTagName()`

* 通过CSS的class选择器，一组DOM节点：`document.getElementsByClassName()`

**注意：**通过HTML标签名和class选择器获取到一组DOM节点，以此作为父节点，再从父节点中开始选择，以缩小范围

```JavaScript
// 返回ID为'test'的节点：
var test = document.getElementById('test');

// 先定位ID为'test-table'的节点，再返回其内部所有tr节点：
var trs = document.getElementById('test-table').getElementsByTagName('tr');

// 先定位ID为'test-div'的节点，再返回其内部所有class包含red的节点：
var reds = document.getElementById('test-div').getElementsByClassName('red');

// 获取节点test下的所有直属子节点:
var cs = test.children;

// 获取节点test下第一个、最后一个子节点：
var first = test.firstElementChild;
var last = test.lastElementChild;
```

* 使用`querySelector()`和`querySelectorAll()`方法，`IE<8`不支持，`IE8`仅有限支持

```JavaScript
// 通过querySelector获取ID为q1的节点：
var q1 = document.querySelector('#q1');

// 通过querySelectorAll获取q1节点内的符合条件的所有节点：
var ps = q1.querySelectorAll('div.highlighted > p');
```