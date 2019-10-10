# 存储

## 理论

* cookie

	* 本身用于客户端和服务器端通信
	
	* 但是它有本地存储的功能，于是就被 '借用'

	* 使用`document.cookie = ...` 获取和修改即可

	* 存储量太小，只有 4kB 

	* 所有的http请求都带着，会影响获取资源的效率

	* API简单不易用，需要封装才能用 `document.cookie=...`

* sessionStorage、localStorage

	* HTML5专门为存储设计，最大容量为 5M
	 
	* API简单易用
		
		* localStorage.setItem(key, value)

		* localStorage.getItem(key)

## 题目

* 请描述一下 cookie，sessionStorage和localStorage的区别

	* 容量

	* 是否会携带到 ajax 中

	* API易用性