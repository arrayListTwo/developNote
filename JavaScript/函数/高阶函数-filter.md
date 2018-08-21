# 高阶函数 `filter`

> `filter()`方法用于把`Array`的某些元素过滤掉，然后返回剩下的元素，返回新的数据

#### `filter()`和`map()`区别

* `filter()`和`map()`函数，参数都是一个函数
* `filter()`作用是把传入的函数依次作用于每个元素，然后根据返回值是`true`还是`false`，决定保留还是丢弃该元素

```JavaScript
var arr = ['A', '', 'B', null, undefined, 'C', '  '];
var r = arr.filter(function (s) {
    return s && s.trim(); // 注意：IE9以下的版本没有trim()方法
});
console.log(r);
```

#### 回调函数

* `filter()`接收的回调函数，回调函数可以存在多个参数。回调函数共计可以接收三个参数

```JavaScript
var arr = ['A', 'B', 'C'];
var r = arr.filter(function (element, index, self) {
    console.log(element); //Array的某个元素，依次打印'A', 'B', 'C'
    console.log(index); // Array元素的索引，依次打印0, 1, 2
    console.log(self); // Array元素本身，self就是变量arr
    return true;
});
```