# 高阶函数`map/reduce`

> 让函数的参数能够接收别的函数，也就是形参包含其他函数

## map

> `map()`方法定义在`JavaScript`的`Array`中，调用`Array`的`map()`方法，传入我们自己的函数，就得到了一个新的`Array`

```JavaScript
function pow(x) {
    return x * x;
}
var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9];
var results = arr.map(pow); // [1, 4, 9, 16, 25, 36, 49, 64, 81]
```

* 传入实参`pow`函数，`Array`数组的每个值作为实参传入`pow`函数中，得到一个新的`Array`

## reduce

> `reduce()`方法定义在`JavaScript`的`Array`中，参数的函数必须接收两个参数，`reduce()`方法把结果继续和序列的下一个元素做累积计算

```JavaScript
[x1, x2, x3, x4].reduce(f) = f(f(f(x1, x2), x3), x4)
```

#### 实练

* 把`[1, 3, 5, 7, 9]`变换成整数`13579`

```JavaScript
var arr = [1, 3, 5, 7, 9];
arr.reduce(function (x, y) {
    return x * 10 + y;
}); // 13579
```