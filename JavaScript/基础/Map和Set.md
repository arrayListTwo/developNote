# Map和Set ES6新增数据类型

## Map

> `Map`是一组键值对的结构，具有极快的查找速度
> `map`中一个`key`只能对应一个`value`，多次对一个`key`放入`value`，后面的值会把前面的值冲掉

#### 初始化

* 初始化`map`对象需要一个二维数组，或者直接初始化一个空`map`

```JavaScript
/* 初始化二维数组 */
var map = new Map([['Michael', 95],['Bob', 75],['Tracy', 85]]);
/* 初始化空map */
var map = new Map();
```

## 集合操作

```JavaScript
// 添加一个新的key-value，或者更改key的值
map.set('Bob', 67);
// 判断是否存在key
map.has("Bob");
// 获取key对应的value，若没有此key，则返回undefined
map.get("Bob");
// 删除指定的key
map.delete("Bob");
````

## Set

> 是一组`key`的集合，并且`key`不能重复

#### 初始化

* 创建一个`Set`，需要提供一个`Array`作为输入，或者直接创建一个空`Set`

```JavaScript
// Array作为输入
var set = new Set([1,2,3]);
// 空的Set
var set = new Set();
```

* Set操作

```JavaScript
// 添加元素到`Set`中
set.add(key);
// 判断是否含有key
set.has(key);
// 删除元素
set.delete(key);
```
