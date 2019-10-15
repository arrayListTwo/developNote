# Class 和 普通构造函数

* JS 构造函数
	
	```JavaScript
	function MathHandle(x, y){
		this.x = x;
		this.y = y
	}
	MathHandle.prototype.add = function(){
		return this.x + this.y
	}
	var m = new MathHandle(1, 2)
	console.log(m.add())
	```

* Class 基本语法

	```JavaScript
	class MathHandle{
		constructor(x, y){
			this.x = x;
			this.y = y
		}
		add(){
			return this.x + this.y
		}
	}
	var m = new MathHandle(1, 2)
	console.log(m.add())
	```

* 语法糖

	```JavaScript
	class MathHandle{}
	var m = new MathHandle()	

	typeof MathHandle // "function"
	MathHandle === MathHandle.prototype.constructor // true
	m.__proto__ === MathHandle.prototype // true
	```

* 继承

	```JavaScript
	/* ES5实现方式 */
	// 动物
	function Animal(){
		this.eat = function(){
			console.log('animal')
		}
	}
	// 狗
	function Dog(){
		this.bark = function(){
			console.log('dog')
		}
	}
	// 绑定原型，实现继承
	Dog.prototype = new Animal()
	// 哈士奇
	let hashiqi = new Dog()
	
	/* ES6实现方式 */
	class Animal{
		constructor(name){
			this.name = name
		}
		eat(){
			console.log(`${this.name} eat`)
		}
	}
	class Dog extends Animal{
		constructor(name){
			super(name)
			this.name = name
		}
		say(){
			console.log(`${this.name} say`)
		}
	}
	let dog = new Dog('哈士奇')
	dog.say()
	dog.eat()

	// 原型链
	hashiqi --> Dog.prototype --> Animal.prototype --> Object.prototype
	```