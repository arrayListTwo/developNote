# Date/Math/Array/Object

# 理论

* Date

	```JavaScript
	Date.now() // 获取当前时间毫秒数
	let dt = new Date()
	dt.getTime() // 获取毫秒数
	dt.getFullYear() // 年
	dt.getMonth() // 月 （0 - 11）
	dt.getDate() // 日（0 - 31）
	dt.getHours() // 小时 （0 - 23）
	dt.getMinutes() // 分钟 （0 - 59）
	dt.getSeconds() // 秒 （0 - 59）
	```

* Math

	```JavaScript
	Math.random() // 获取随机数，附加在请求后面，随时清空缓存效果
	```

* 数组API

	```JavaScript
	var arr = [1, 2, 3]
	---------方法-----------
		forEach // 遍历所有元素
	arr.forEach(function(item, index){
		// 遍历数组的所有元素
	})

		every // 判断所有元素是否都符合条件
	let res = arr.every(function(item, index){
		// 用来判断所有的数组元素，都满足一个条件，遇到不满足的，立即停止判断
		if(item < 4){
			return true
		}
	})
	console.log(res) // true

		some // 判断是否有至少一个元素符合条件
	let res = arr.some(function(item, index){
		// 用来判断所有的数组元素，只要有一个满足条件即可，遇到一个满足条件的，立即停止判断
		if(item < 2){
			return true
		}
	})
	console.log(res) // true

		sort // 排序，改变原数组
	let arr2 = arr.sort(function(a, b){
		// 从小到大排序
		return a - b
		// 从大到小排序
		// return b - a
	})
	console.log(arr2) // [1, 2, 3]

		map // 对元素重新组装，生成新数组
	let arr2 = arr.map(function(item, index){
		// 将元素重新组装，并返回
		return '<b>' + item + '</b>'
	})
	console.log(arr2) // ["<b>1</b>", "<b>2</b>", "<b>3</b>"]

		filter // 过滤符合条件的元素
	let arr2 = arr.filter(function(item, index){
		// 通过某一个条件过滤数组
		if(item >= 2){
			return true
		}
	})
	console.log(arr2) // [2, 3]
	```

* 对象API

	```JavaScript
	let obj = {x:100, y:200, z:300}
	for(let key in obj){
		if(obj.hasOwnProperty(key)){
			console.log(key, obj[key])
		}
	}
	```

## 题目

* 获取 2017-06-10 格式的日期

	```JavaScript
	function formatDate(dt){
		if(!dt){
			dt = new Date()
		}
		let year = dt.getFullYear()
		let month = dt.getMonth() + 1
		let date = dt.getDate()
		if(month < 10){
			// 强制类型转换
			month = '0' + month
		}
		if(date < 10){
			// 强制类型转换
			date = '0' + date
		}
		// 强制类型转换
		return year + '-' + month + '-' + date
	}
	```

* 获取随机数，要求是长度一致的字符串格式

	```JavaScript
	let random = Math.random()
	random = random + '0000000000' // 强制类型转换，后面加10个零（保证不会报错）
	random = random.slice(0, 10)
	```

* 下一个能遍历对象和数组的通用forEach函数

	```JavaScript
	function forEach(obj, fn){
		var key 
		if(obj instanceof Array){
			obj.forEach(function(item, index){
				fn(index, item)
			})
		}else{
			for(key in obj){
				fn(key, obj[key])
			}
		}
	}
	```
