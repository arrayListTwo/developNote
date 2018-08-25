# 高级函数之generator

> `generator`生成器是`ES6`标准引入的新的数据类型。一个`generator`看上去像一个函数，但**可以返回多次**

## 定义

> `generator`由`function*`定义
> 除了`return`语句外，还可以`yield`返回多次

```JavaScript
function* foo(x){
	yield x + 1;
	yield x + 2;
	return x + 3;
}
```

## 编写斐波那契数列 和 取出`generator`生成器数据

#### 斐波那契数列

> 0 1 1 2 3 5 8 13 21 34 ...

```JavaScript
function* fib(max) {
    var
        t,
        a = 0,
        b = 1,
        arr = [0, 1];
    while (arr.length < max) {
        [a, b] = [b, a + b];
        arr.push(b);
    }
    return arr;
}
// 测试:
fib(5); 	// [0, 1, 1, 2, 3]
fib(10);	// [0, 1, 1, 2, 3, 5, 8, 13, 21, 34]
```

* `console.log(fib(5))`

```JavaScript
// 直接调用`generator`，会创建一个`generator`对象，并没有执行它
fib {[[GeneratorStatus]]: "suspended", [[GeneratorReceiver]]: Window}
```

#### 第一种：`next()`方法：

`next()`方法会执行`generator`的代码，然后，每次遇到`yield`关键字就会返回一个对象`{value: x, done: true/false}`，然后**暂停**

* 返回的`value`就是`yield`的返回值
* `done`表示这个`generator`是否已经执行结束。如果`done`为`true`，则`value`就是`return`的返回值

```JavaScript
var f = fib(5);
f.next(); // {value: 0, done: false}
f.next(); // {value: 1, done: false}
f.next(); // {value: 1, done: false}
f.next(); // {value: 2, done: false}
f.next(); // {value: 3, done: false}
f.next(); // {value: undefined, done: true}
```

#### 第二种：`for ... of`循环

```JavaScript
for (var x of fib(5)) {
    console.log(x); // 依次输出0, 1, 1, 2, 3
}
```