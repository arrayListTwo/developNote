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
 
 ## API
 
 * `dayjs().isValid()`: 是否是合法的Day.js对象实例
 
