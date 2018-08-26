# Date对象

> 在`JavaScript`中，`Date`对象用来表示日期和时间

## 获取系统当前时间，系统时间可以手动更改，不一定准确

> `new Date()`，在创建`Date`对象时，会将系统当前时间封装成`Date`对象，对象内封装的时间不会随着时间的推进发生改变，除非重新创建

```JavaScript
var now = new Date();
now; // Sun Aug 26 2018 20:44:33 GMT+0800 (中国标准时间)
now.getFullYear(); // 2018，年份
now.getMonth(); // 7，月份，月份的范围是0~11
now.getDate(); // 26，表示26号
now.getDay(); // 0，表示周天
now.getHours(); // 20，24小时制
now.getMinutes(); // 47，分钟 
now.getSeconds(); // 19，秒
now.getMilliseconds(); // 166，毫秒
now.getTime(); // 1535287771220，以number形式表示的时间戳
Date.now(); // 时间戳，老版本IE中不存在此方法
```

## 创建指定时间的`Date`对象

* 直接传入`年`、`月`等信息，返回`Date`对象

```JavaScript
var d = new Date(2015, 5, 19, 20, 15, 30, 123); // 月份范围是0~11
d; // Fri Jun 19 2015 20:15:30 GMT+0800 (CST)
```

* 传入`ISO 8601`格式的字符串，返回**时间戳**

```JavaScript
var d = Date.parse('2015-06-24T19:49:22.875+08:00');
d; // 时间戳，1435146562875
```

* 传入**时间戳**，返回`Date`对象

```JavaScript
var d = new Date(1435146562875);
d; // Wed Jun 24 2015 19:49:22 GMT+0800 (CST)
d.getMonth(); // 5
```

## 时间戳

> 时间戳是一个自增的整数，它表示从1970年1月1日零时整的`GMT`时区开始的那一刻，到现在的毫秒数，**任何时区，在此时此刻的时间戳数字都是一样的**，时间戳可以精确的表示一个时刻，与时区无关

> 我们只需要传递时间戳，或者把时间戳从数据库里读出来，再让`JavaScript`自动转换为当地时间就可以了

* 显示本地时间

```JavaScript
var now = new Date(1535288480471);
now.toLocaleString(); // "2018/8/26 下午9:01:20"
```

* 显示`UTC`时间

```JavaScript
var now = new Date(1535288480471);
now.toUTCString(); // "Sun, 26 Aug 2018 13:01:20 GMT"
```