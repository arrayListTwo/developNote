# dayjs 文档

> 所有的 API 操作都将返回一个新的 **Dayjs** 对象

## 解析

### 当前时间

* 直接调用 `dayjs()` 将返回一个包含当前日期和时间的 **Day.js** 对象，等同于调用 `dayjs(new Date())` 的调用
* 当没有传入参数时，参数默认值是 `undefined` ，所以调用 `dayjs(undefined)` 就相当于调用 `dayjs()`
* **Day.js** 将 `dayjs(null)` 视为无效的输入

### 字符串

* 解析传入的 **ISO 8601** 格式的字符串并返回一个 **Day.js** 对象实例

  ```JavaScript
  new Date().toISOString() // '2020-10-28T02:09:44.889Z'
  dayjs('2020-10-28T02:09:44.889Z') // Day.js 对象实例
  ```
 **注：** 为了保证结果一致，当解析除了 **ISO 8601** 格式以外的字符串时，应该使用 **String + Format (字符串 + 格式)**
 
 ### 字符串 + 格式
 
 > 如果知道输入字符串的格式，可以用此方式来解析日期
 
 #### 使用本功能，需要先配置 **CustomParseFormat** 插件
 
 ```JavaScript
 let customParseFormat = require('dayjs/plugin/customParseFormat')
 dayjs.extend(customParseFormat)
 dayjs('12-25-1995', 'MM-DD-YYYY')
 ```
 
 * 最后一个参数可传入布尔值来启用严格解析模式。严格解析要求格式和输入内容完全匹配，包括分隔符
 
 ```JavaScript
 dayjs('2020-10/28', 'YYYY-MM-DD').isValid() // true
 dayjs('2020-10/28', 'YYYY-MM-DD', true).isValid() // false
 dayjs('2020-10-28', 'YYYY-MM-DD', true).isValid() // true
 ```
 
 #### 支持的解析占位符列表
 | 输入 | 例子 | 详情 |
| :-----| :----: | :---- |
| YY | 18 | 两位数的年份 |
| YYYY | 2020 | 四位数的年份 |
| M | 1-12 | 月份，从1开始 |
| MM | 01-12 | 月份，两位数 |
| MMM | Jan-Des | 缩写的月份名称 |
| MMMM | January-December | 完整的月份名称 |
| D | 1-31 | 月份里的一天 |
| DD | 01-31 | 月份里的一天，两位数 |
| H | 0-23 | 小时 |
| HH | 00-23 | 小时，两位数 |
| h | 1-12 | 小时，12小时制 |
| hh | 01-12 | 小时，12小时制，两位数 |
| m | 0-59 | 分钟 |
| mm | 00-59 | 分钟，两位数 |
| s | 0-59 | 秒 |
| ss | 00-59 | 秒，两位数 |
| S | 0-9 | 毫秒，一位数 |
| SS | 00-99 | 毫秒，两位数 |
| SSS | 000-999 | 毫秒，三位数 |

### Unix 时间戳（毫秒）

* 解析传入的一个Unix时间戳（13位数字，从1970年1月1日UTC午夜开始所经过的毫秒数）创建一个 **Day.js** 对象

```JavaScript
dayjs(1318781876406)
```

**注：** 传入的参数必须是 **number**

### Unix 时间戳 （秒）

* 解析传入的一个Unix时间戳（10位数字，从1970年1月1日Utc午夜开始所经过的秒数）创建一个 **Day.js** 对象

```JavaScript
dayjs.unix(1318781876)
```

* 这个方法是用 `dayjs(timestamp * 1000)` 实现的，所有传入时间戳里的小数点后面的秒也会被解析

```JavaScript
dayjs.unix(1318781876.721)
```

### Date 对象

* 使用原生 JavaScript `Date` 对象创建一个 **Day.js** 对象

```JavaScript
let day = dayjs(new Date(2020, 10, 18))
```

* 这将克隆 `Date` 对象。对传入的 `Date` 对象做进一步更改不会影响 `Day.js` 对象，反之亦然

### UTC

* 默认情况下，**Day.js** 会把时间解析成本地时间

* 如果想使用 **UTC** 时间，先配置 **UTC** 插件

```JavaScript
import dayjs from 'dayjs'
var utc = require('dayjs/plugin/utc')
dayjs.extend(utc)
```

* 调用 `dayjs.utc()`，在 **UTC** 模式下，所有显示方法将会显示 **UTC** 时间而非本地时间

```JavaScript
dayjs().format('YYYY-MM-DD HH:mm:ss') // 2020-10-28 17:55:46  东八区时间
dayjs.utc().format('YYYY-MM-DD HH:mm:ss') // 2020-10-28 09:55:46  零时区时间
```

### Dayjs 复制

* 所有的 **Day.js** 对象都是 不可变的。但如果有必要，要使用 `dayjs#clone` 可以复制出一个当前对象

```JavaScript
let a = dayjs()
let b = a.clone()
// a 和 b 是两个独立的 Day.js 对象
```

* 在 `dayjs()` 里传入一个 `Day.js` 对象也会返回一个复制的对象

```JavaScript
let a = dayjs()
let b = dayjs(b)
```

 ### 验证
 
 * 检测当前 `Day.js` 对象是否是一个有效的时间，返回 `boolean`
 
 ```JavaScript
 dayjs().isValid()
 ```
 
 ## 取值 / 赋值
 
* 在设计上 `Day.js` 的 `getter` 和 `setter` 使用了相同的 API，也就是说，不传参数调用方法即为 `getter` ，调用并传入参数为 `setter`
 
* 这些 API 调用了对应原生的 `Date` 对象的方法

```JavaScript
dayjs().second(30).valueOf() // => new Date().setSeconds(30)
dayjs().second() // => new Date().getSeconds()
```

* 如果处于 **UTC模式** ，将会调用对应的 `UTC` 方法

```JavaScript
dayjs.utc().second(30).valueOf() // => new Date().setUTCSeconds(30)
dayjs.utc().second() // => new Date().getUTCSeconds()
```

### Millisecond

> 获取或设置毫秒

* 传入 0 - 999 的数字。如果超出这个范围，它会进位到秒

```JavaScript
dayjs().millisecond() // 58 => getter
dayjs().millisecond(1) // => setter
```

### Second

> 获取或设置秒

* 传入 0 - 59 的数字。如果超出这个范围，它会进位到分钟

```JavaScript
dayjs().second()
dayjs().second(1)
```

### Minute

> 获取或设置分钟

* 传入 0 - 59 的数字。如果超出这个范围，它会进位到小时

```JavaScript
dayjs().minute()
dayjs().minute(59)
```

### Hour

> 获取或设置小时

* 传入 0 - 23 的数字。如果超出这个范围，它会进位到天数

```JavaScript
dayjs().hour()
dayjs().hour(12)
```

### Date of Month

> 获取或设置月份里的日期

* 接受 1 - 31 的数字。如果超出这个范围，它会进位到月份

```JavaScript
dayjs().date()
dayjs().date(1)
```

### Date of Week

> 获取或设置星期几

* 传入 number 从 0(星期天) 到 6(星期天)。如果超出这个范围，它会进位到其他周

```JavaScript
dayjs().day()
dayjs().day(0)
```

**注：** `dayjs#date`: 是该月的日期；`dayjs#day`: 是星期几

### Day of Year

> 获取或设置年份里的第几天

* 传入 1 - 366 的数字。如果超出这个范围，它会进位到下一年

* 使用功能需先配置 `DayOfYear` 插件

```JavaScript
const dayOfYear = require('dayjs/plugin/dayOfYear')
dayjs.extend(dayOfYear)
dayjs('2010-01-01').dayOfYear() // 1
dayjs('2010-01-01').dayOfYear(365) // 2010-12-31
```

### Week of Year

> 获取或设置该年的第几周

* 使用前需先配置 `WeekOfYear` 插件

```JavaScript
const weekOfYear = require('dayjs/plugin/weekOfYear')
dayjs.extend(weekOfYear)
dayjs('2018-06-27').week() // 26
dayjs('2018-06-27').week(5) // 设置周 
```

### Month

> 获取或设置月份

* 传入 0 - 1 的number。如果超出这个范围，它会进位到年份

```JavaScript
dayjs().month()
dayjs().month(0)
```

**注：**月份是从 0 开始计算的，即 1 月是 0

### Quarter

> 获取或设置季度

* 使用前需先配置 `QuarterOfYear` 插件

```JavaScript
const quarterOfYear = require('dayjs/plugin/quarterOfYear')
dayjs.extend(quarterOfYear)
dayjs('2010-04-01').quarter() // 2
dayjs('2010-04-01').quarter(2)
```

### Year

> 获取或设置年份

```JavaScript
dayjs().year()
dayjs().year(2000)
```

### Get

> 从 `Day.js` 对象中获取相应信息的 `getter`

* 相当于 `dayjs().get(unit) === dayjs()[unit]()`

* 各个传入的单位对大小写不敏感，支持缩写和复数

```JavaScript
dayjs().get('year')
dayjs().get('month') // 从 0 开始
dayjs().get('date')
dayjs().get('hour')
dayjs().get('minute')
dayjs().get('second')
dayjs().get('millisecond')
```

* 支持的单位列表

| 单位 | 缩写 | 详情 |
| :--- | :---: | :-- |
| date | D | 月份里的日期 |
| day | d | 星期几 (星期天为0；星期六为6) |
| month | M | 月份 (一月 0， 十二月 11) |
| year | y | 年份 |
| hour | h | 小时 |
| minute | m | 分钟 |
| second | s | 秒 |
| millisecond | ms | 毫秒 |

### Set

> 通用的 `setter`，两个参数分别是要更新的单位和数值，调用后会返回一个修改后的新实例

* 相当于 `dayjs().set(unit, value) === dayjs()[unit](value)`

```JavaScript
dayjs().set('date', 1)
dayjs().set('month', 3) // 四月
dayjs().set('second', 30)
```

### Maximum Minimum

> 返回传入的 `Day.js` 实例中最大或最小实例对象

* 使用前，需先配置 `MinMax` 插件

```JavaScript
const minMax = require('dayjs/plugin/minMax')
dayjs.extend(minMax)
dayjs.max(dayjs('2020-10-23'), dayjs('2018-01-01'), dayjs('2019-01-01')).format('YYYY-MM-DD') // 2020-10-23
dayjs.min(dayjs('2020-10-23'), dayjs('2018-01-01'), dayjs('2019-01-01')).format('YYYY-MM-DD') // 2018-01-01
dayjs.min([dayjs('2020-10-23'), dayjs('2018-01-01'), dayjs('2019-01-01')]).format('YYYY-MM-DD') // 2018-01-01 => 数组参数
```


