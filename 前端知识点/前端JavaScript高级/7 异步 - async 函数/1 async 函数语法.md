# async 函数

> `async` 表示函数里有异步操作

> `await`表示紧跟在后面的表达式需要 **等待** 结果

> `async` 函数完全可以看做是多个异步操作，包装成的一个 `Promise` 对象，而 `await` 命令就是内部 `then` 命令的语法糖

## 基本用法

* `async` 函数返回一个 `Promise` 对象，可以使用`then`方法添加回调函数

* 当函数执行的时候，一旦遇到`await`就会先返回，等到异步操作完成，再接着执行函数体内后面的语句

* `async`函数有多种使用形式

```JavaScript
// 函数声明
async function foo(){...}

//函数表达式
const foo = async function(){...}

// 对象的方法
let obj = { async foo(){...} }

// Class 的方法
class Storage{
	constructor(){
		this.cachePromise = caches.open('avatars')
	}
	async getAvatar(name){
		const cache = await this.cachePromise;
		return cache.match(`/avatars/${name}.jpg`)
	}
}
const storage = new Storage()
storage.getAvatar('jake').then( () => {...} )

// 箭头函数
const foo = async () => {...}
```

## 语法

### `async` 函数返回一个 `Promise` 对象

* `async` 函数内部 `return` 语句返回的值，会成为 `then` 方法回调函数的参数

	```JavaScript
	async function(){
		return 'hello world';
	}
	f().then( v => console.log(v) )
	// 结果：'hello'
	```

* `async` 函数内部抛出错误，会导致返回的 `Promise` 对象变为 `reject` 状态。抛出的错误对象会被 `catch` 方法回调函数接收到

	```JavaScript
	async function foo(){
		throw new Error('出错了...')
	}
	foo().then( (res) => {console.log(res)} )
		.catch( err => {console.log(err)} )
	// 结果：Error：出错了
	```

### `Promise`对象的状态变化

* `async` 函数返回的 `Promise` 对象，必须等到内部所有 `await` 命令后面的 `Promise` 对象执行完，才会发生状态改变，除非遇到 `return` 语句或者抛出错误。也就是说，只有 `async` 函数内部的异步操作执行完，才会执行 `then` 方法指定的回调函数

### `await` 命令

* `await`命令后面是一个`Promise`对象，返回该对象的结果。如果不是`Promise`对象，就直接返回对应的值

* `await`命令后面的`Promise`对象如果变为`reject`状态，则`reject`的参数会被`catch`方法的回调函数接收到

* 任何一个 `await` 语句后面的 `Promise` 对象变为 `reject` 状态，那么整个 `async` 函数都会中断执行

	```JavaScript
	async function f(){
		await Promise.reject('出错了');
		await Promise.resolve('hello world') // 不会执行
	}
	```

	* 希望即使前一个异步操作失败，也不要中断后面的异步操作

		* 将第一个 `await` 放在 `try...catch`结构里面，这样不管这个异步操作是否成功，第二个`await`都会执行

		```JavaScript
		async function f(){
			try{
				await Promise.reject('出错了')
			} catch(e) {}
			return await Promise.resolve('hello world')
		}
		f()
			.then( v => console.log(v) )
		// 运行结果： hello world
		```

		* `await` 后面的 `Promise` 对象再跟一个`catch`方法，处理前面可能出现的错误

		```JavaScript
		async function f(){
			await Promise.reject('出错了')
				.catch( e => console.log(e) );
			return await Promise.resolve('hello world')
		}
		f()
			.then( v => console.log(v) )
		// 运行结果：出错了
		//          hello world
		```