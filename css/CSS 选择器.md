# CSS选择器

## 层叠样式表

* 0 0 0
	* 0: 这个选择器包含ID？每个ID加 1 分
	* 0：这个选择器包含类或伪类？每个类或伪类加 1 分
	* 0：这个选择器包含元素名？一个元素名加 1 分

## 常用选择器

### 元素选择器

* 指定需要应用样式的元素的名称

```css
p{color: black;}
```

### 后代选择器

* 所有后代

```css
blockquote p{padding-left: 2em}
```

### ID选择器

* ID在页面上是唯一存在的

```css
#intro{font-weight: bold}
```

### 类选择器

```css
.date-posted{color: #ccc}
```

### 伪类

> 根据**文档结构之外的其他条件**对元素应用样式，例如：表单元素或链接的状态

```css
/*makes all unvisited links blue*/
a:link{color: blue;}
```
```css
/*make all visited links green*/
a:visited{color:green;}
```
```css
/*makes links red when hovered or activated*/
a:hover, a:focus, a:active{color: red;}
```

**注意：** 
* `:link`和`:visited`称为*链接伪类*，只能应用于锚元素
* `:active`、`:hover`和`:focus`称为*动态伪类*，理论上可以应用于任何元素

**兼容性：**
* **IE6** 只注意应用于锚链接的`:active`和`:hover` 选择器，完全忽略`:focus`
* **IE7** 在任何元素上都支持`:hover`，但是忽略`:active`和`focus`

## 通用选择器

> 通用选择器由一个 ** * ** 表示

```css
<!--对页面上的所有元素应用样式，删除每个元素上默认的浏览器内边距和外边距-->
* {
	padding: 0; 
	margin: 0;
  }
```

## 高级选择器

### 子选择器

> 选择元素的直接后代：子元素

```css
#nav > li{padding-left: 20px}
```
**兼容性：**
* **IE7** 和更高版本都支持子选择器，但是在 **IE7** 中，当父元素和子元素之间有HTMl注释时，就会出现问题
* 在 **IE6** 和更低版本中，可以使用 **通用选择器模拟子选择器的效果**
	* 先在所有后代上应用你希望子元素具有的样式
	```css
	#nav li{padding-left: 20px;}
	```
	* 接着，使用通用选择器覆盖子元素的后代上的样式
	```css
	#nav li *{padding-left: 0;}
	```

### 相邻同胞选择器

> 相邻同胞选择器可用于定位同一个父元素下某个元素之后的元素(与其相邻)

```css
<!--顶级标题后面的第一个段落显示为：灰色-->
h2 + p{color: #777;}
```
**兼容性：**
* 与子选择器一样，如果在目标元素之间有注释，在 **IE7** 中也会出问题

### 属性选择器

> 属性选择器可以 **根据某个属性是否存在或属性的值** 来寻找元素，属性用 **[ ]** 括住表示

#### 属性是否存在

##### 单个属性
```css
<!--为含有title属性的acronym元素应用样式：字体显示为红色-->
acronym[title] {color:red;}
```
##### 多个属性

> 让属性选择器连接在一起即可

```css
<!--有 href 和 title 属性的 HTML 超链接的文本设置为红色-->
a[href][title] {color:red;}
```

#### 属性值

##### 单个属性值

```css
<!--超链接的title属性值为：test，设置样式为：字体红色-->
a[title="test"] {color: red;}
```

##### 多个属性值

> 将多个属性值连接在一起

```css
<!--超链接的title属性值为：test，并且 href属性值为：http://www.w3school.com.cn/，设置样式为：字体红色-->
a[href="http://www.w3school.com.cn/"][title="W3School"] {color: red;}
```

##### 一个属性的部分属性值

> 需要使用 **波浪号 ~**

```css
<!--title值为"important small"，可应用此样式； 值为"important"，也可应用此样式-->
<!--title值为"importants small", 不可应用此样式-->
p[title~="important"] {color: red;}
```

##### 子串匹配属性选择器

```css
<!--以"imp"开头的title属性的p元素-->
p [title^="imp"]{color: red;}
```
```css
<!--以"imp"结尾的title属性的p元素-->
p [title$="imp"]{color: red;}
```
```css
<!--包含"imp"字符串的title属性的p元素-->
p [title*="imp"]{color: red;}
```
```css
<!--title属性值等于"imp"或者以"imp-"开头的p元素-->
p [title|="imp"]{color: red;}
```
