# JSON对象

> `JSON`是`JavaScript Object Notation`的缩写，它是一种数据交换格式

> `JSON`实际上是`JavaScript`的一个子集

> `JSON`定死了字符集必须是`UTF-8`

> `JSON`的字符串规定必须用双引号`""`，`Object`的键也必须用双引号`""`

## `JSON`中数据类型

* `number` : 和`JavaScript`中的`number`完全一致
* `boolean` : `JavaScript`的`true` 或 `false`
* `string` : `JavaScript`的 `string`
* `null` ： `JavaScript` 的 `null`
* `array` ： `JavaScript` 的 `Array` ，表示方式 - `[]`
* `object` : `JavaScript` 的 `{...}` 的表示方式

## `JavaScript`中的序列化和反序列化

### 序列化

> 将`JavaScript`对象序列化成一个`JSON`格式的字符串，便可以通过网络传输

```JavaScript
// object对象序列化成json字符串
JSON.stringify(jsonObj);
/*
 * 美化输出json，
 * jsonObj：json对象
 * obj：用于控制如何筛选对象的键值，下面做详细解释
 * format就是输入的格式，可以为制表符(`\t`)
 * /
JSON.stringify(jsonObj, obj, 'format');
```

#### 第二个参数：obj

```JavaScript
var xiaoming = {
    name: '小明',
    age: 14,
    gender: true,
    height: 1.65,
    grade: null,
    'middle-school': '\"W3C\" Middle School',
    skills: ['JavaScript', 'Java', 'Python', 'Lisp']
};
```

* 只输出指定的属性，可以传入`Array`，`Array`中的值是`json`对象的键，如： `['name', 'skills']`

* 传入一个函数，这样对象的每个键值对都会被函数先处理，如：

```JavaScript
function convert(key, value) {
    if (typeof value === 'string') { // 如果对象对应的值是string类型，则将值转化为大写
        return value.toUpperCase(); 
    }
    return value;
}

JSON.stringify(xiaoming, convert, '  ');
/*结果*/
{
  "name": "小明",
  "age": 14,
  "gender": true,
  "height": 1.65,
  "grade": null,
  "middle-school": "\"W3C\" MIDDLE SCHOOL",
  "skills": [
    "JAVASCRIPT",
    "JAVA",
    "PYTHON",
    "LISP"
  ]
}
```

#### 重写`toJSON()`方法

* 精确的控制如何序列化对象，可以给对象定义`toJSON`方法，则序列化时会直接返回应该序列化的数据

```JavaScript
var xiaoming = {
    name: '小明',
    age: 14,
    gender: true,
    height: 1.65,
    grade: null,
    'middle-school': '\"W3C\" Middle School',
    skills: ['JavaScript', 'Java', 'Python', 'Lisp'],
    toJSON: function () {
        return { // 只输出name和age，并且改变了key：
            'Name': this.name,
            'Age': this.age
        };
    }
};
JSON.stringify(xiaoming); // '{"Name":"小明","Age":14}'
```

### 反序列化

> 将`JSON`格式的字符串反序列化成一个`JavaScript`对象，可以在`JavaScript`中直接解析使用这个对象

* 获取到一个`JSON`格式的字符串，直接使用`JSON.parse()`方法把它变成一个`JavaScript`对象

```JavaScript
JSON.parse('[1,2,3,true]'); // [1, 2, 3, true]
JSON.parse('{"name":"小明","age":14}'); // Object {name: '小明', age: 14}
JSON.parse('true'); // true
JSON.parse('123.45'); // 123.45
```
* `JSON.parse()`还可以接收一个函数，用它转换解析出来的属性

```JavaScript
var obj = JSON.parse('{"name":"小明","age":14}', function (key, value) {
    if (key === 'name') {
        return value + '同学';
    }
    return value;
});
console.log(JSON.stringify(obj)); // {name: '小明同学', age: 14}
```