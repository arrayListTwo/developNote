# iterable

> 遍历`Array`可以采用下标循环，遍历`Map`和`Set`就无法使用下标
> `ES6`标准引入了新的`iterable`类型
> `Array`、`Map`和`Set`都属于`iterable`类型

## `for...of`循环遍历

> 具有`iterable`类型的集合，可以通过新的`for...of`循环来遍历

#### 用法

```JavaScript
var a = ['A', 'B', 'C'];
var s = new Set(['A', 'B', 'C']);
var m = new Map([[1, 'x'], [2, 'y'], [3, 'z']]);
for (var x of a) { // 遍历Array
    console.log(x); // A  B  C
}
for (var x of s) { // 遍历Set
    console.log(x);  // A   B   C
}
for (var x of m) { // 遍历Map
    console.log(x[0] + '=' + x[1]); // 1=x  2=y  3=z
}
```

#### `for...of`和`for...in`区别

* `for...in`，遍历的实际上是对象的属性名称
	* 一个`Array`数组实际上也是一个对象，它的每个元素索引都被视为一个属性
	```JavaScript
	var a = ['A', 'B', 'C'];
	a.name = 'Hello';
	for (var x in a) {
	    console.log(x); // '0', '1', '2', 'name'
	}
	```
	* `for...in`循环将把`name`包括在内，但`Array`的`length属性`却不包括在内
* `for...of`循环则修复了这些问题，它只循环集合本身的元素
	```JavaScript
	var a = ['A', 'B', 'C'];
	a.name = 'Hello';
	for (var x of a) {
	    console.log(x); // 'A', 'B', 'C'
	}
	```

## `iterable`内置的`forEach`方法，`ES5.1`引入，建议使用

> `forEach`方法接收一个函数，每次迭代到自动回调该函数

#### `Array`对象存在索引

```JavaScript
'use strict';
var arr = ['A', 'B', 'C'];
arr.forEach(function (element, index, array) {
    // element: 指向当前元素的值
    // index: 指向当前索引
    // array: 指向Array对象本身
    console.log(element + ', index = ' + index);
	/*	
		A, index = 0
	 	B, index = 1
		C, index = 2 
	 */
});
```

#### `Set`对象没有索引

* 回调函数的前两个参数都是元素本身

	```JavaScript
	var s = new Set(['A', 'B', 'C']);
	s.forEach(function (element, sameElement, set) {
	    console.log(element + " : " + sameElement);
	});
		/*
			A : A
			B : B
			C : C
		*/
	```

#### `Map`的回调函数参数依次为`value`、`key`和`map`本身：

```JavaScript
var m = new Map([[1, 'x'], [2, 'y'], [3, 'z']]);
m.forEach(function (value, key, map) {
    console.log(value + " : " + key);
});
	/*
		x : 1
		y : 2
		z : 3
	*/
```