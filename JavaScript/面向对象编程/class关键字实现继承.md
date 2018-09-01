## class关键字实现继承关系

> 以往实现继承关系，需要正确实现原型链，则需要编写大量的代码

> `ES6`引入了`class`关键字，`class`的目的就是让定义类更简单

* 定义`Student`类

```JavaScript
class Student {
    constructor(name) {
        this.name = name;
    }

    hello() {
        alert('Hello, ' + this.name + '!');
    }
}
```

**注意：**
* `class`的定义包含了构造函数`constructor`
* 定义在原型上的函数，等同于`Student.prototype.hello = function () {...}`，不使用关键字`function`

* `class`继承

```JavaScript
class PrimaryStudent extends Student {
    constructor(name, grade) {
        super(name); // 记得用super调用父类的构造方法!
        this.grade = grade;
    }

    myGrade() {
        alert('I am at grade ' + this.grdddade);
    }
}
```

**注意：**
* 子类的定义也是`class`关键字实现的
* `extends`关键字则表示原型链对象来自`Student`