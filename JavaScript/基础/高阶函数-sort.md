# 高阶函数 `sort`

* **问题：** `Array.sort()`函数排序算法是默认把所有元素转换为`String`再排序，根据ASCII码进行比较，升序

## `Array`的`sort()`函数是一个高阶函数

* 接收一个函数参数，函数需要接收两个参数`(x, y)`
	* 如果`x < y`，则返回`-1`，两个元素位置不变
	* 如果`x > y`，则返回`1`，两个元素位置置换
	* 如果`x = y`，则返回`0`，两个元素位置不变

```JavaScript
// 升序
ar arr = [10, 20, 1, 2];
arr.sort(function (x, y) {
    if (x < y) {
        return 1;
    }
    if (x > y) {
        return -1;
    }
    return 0;
});
console.log(arr); // [1, 2, 10, 20]
```