# jQuery的属性与样式-attr()、removeAttr()和prop、removeProp()

## 获取 / 设置属性值 attr（）

> 如果是集合操作获取属性值，获取的是第一个元素的属性值，可以通过`each()`或`map()`方法遍历获取值
 
* **`attr(attrName)`：**

* **`attr(attrName)`：**获取属性的值

* **`attr(attrName, attrValue)`：**设置属性的值

* **`attr(attrName, functionName)`：**设置属性的函数值

* **`attr(attrs)`：**给指定元素设置多个属性值，即：`{attrName1:"attrValue1", attrName2:"attrValue2"，...}`

## 删除属性 removeAttr()

* **`removeAttr(attrName)`：**匹配的元素集合中的每个元素移除一个属性

## prop() / removeProp()

* 添加属性名称，该属性就会生效，应该使用**`prop()`**来获取 / 设置属性

* **`true`**和**`false`**属性使用**`prop()`**

## 官方推荐使用attr和prop的情况

![](https://i.imgur.com/zqiXDv7.png)