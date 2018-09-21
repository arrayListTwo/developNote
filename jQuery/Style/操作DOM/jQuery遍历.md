# jQuery遍历

## 子元素`children()`

* 无参数`children()`，允许我们通过在DOM树种对这些元素的直接子元素进行搜索，并且构造一个新的匹配元素的jQuery对象。

* `children(selector)`，对直接子元素进行筛选

## 后代元素`find(selector)`

* `find()`是遍历当前元素集合中每个元素的后代，参数是必须的，若选择全部后代元素，可以传递参数`selector`为通配选择器`*`

## 直接父元素`parent()`

* `parent()`方法允许我们能够在DOM树种搜索到这些元素的父级元素，从有序的向上匹配元素，并根据匹配的元素创建一个新的jQuery对象

* `parent(selector)`传递一个选择器的表达式，对直接父元素进行一定的筛选

##  祖辈元素`parents()`

* `parents()`方法允许我们能够在DOM树种搜索到这些元素的祖先元素，从有序的向上匹配元素，并根据匹配的元素创建一个新的jQuery对象

* `parents(selector)`对祖辈元素进行一定的筛选

* 一直查找到**根元素**，并将匹配的元素加入集合

## 最近符合`selector`的自己或者祖辈元素`closest(selector)`

* 从**元素本身**开始，在DOM树上逐级向上元素匹配，并返回最先匹配的元素

## 紧邻在后面同辈元素`next()`

* `next()`：同辈相邻的后面的兄弟元素

* `next(selector)`：根据`selector`进行一定的筛选

## 紧邻在前面同辈元素`prev()`

* `prev()`元素的前一个同辈元素

* `prev(selector)`对元素进行筛选

## 同辈兄弟元素`siblings()`

* `siblings()`元素的同辈元素集合

* `siblings()`对同辈元素进行一定的筛选

## 添加到已选定的元素集合`add()`

* `.add()`的参数几乎可以接受任何的`$()`，包括一个jQuery选择器表达式、DOM元素或HTML片段引用

## 遍历jQuery对象`each()`

```JavaScript
$("li").each(function(index, element) {
     index 索引 0,1
     element是对应的li节点 li,li
     this 指向的是li
})
```

**注意：**在`each()`函数内，调用`return false；`即可终止循环