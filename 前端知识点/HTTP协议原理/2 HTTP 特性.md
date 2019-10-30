# HTTP

## CORS跨域请求的限制和解决

## CORS预请求

## 缓存 Cache-Control

### 可缓存性

* `public`

* `private`

* `no-cache`：强制确认缓存

### 到期

* `max-age=<seconds>`

* `s-maxage=<seconds>`

* `max-stale=<seconds>`

### 重新验证

* `must-revalidate`

* `proxy-revalidate`

### 其他

* `no-store` ：缓存中不得存储任何关于客户端请求和服务端响应的内容

* `no-transform`

## 资源验证

* `Last-Modified` 

	* 上次修改时间

	* 配合 `If-Modified-Since` 使用

	* 对比上次修改时间，验证资源是否更新

* `Etag` 
 
	* 数据签名

	* 配合 `If-Match` 或者 `If-Non-Match` 使用

	* 对比资源的签名判断是否使用缓存

* [HTTP 缓存](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Caching_FAQ "HTTP 缓存")

* [彻底弄懂HTTP缓存机制及原理](https://www.cnblogs.com/chenqf/p/6386163.html "彻底弄懂HTTP缓存机制及原理")

## Cookie

* 服务器端，通过 `Set-Cookie` 设置

* 下次请求会自动带上

* 键值对，可以设置多个

* 属性

	* `max-age` 和 `expires` 设置过期时间
	
	* `Secure` 只在 `https` 的时候发送

	* `HttpOnly` 无法通过 `document.cookie` 访问

	* `domain`：设置为 **.一级域名**，则一级域名和所有的二级域名共享此 `Cookie`

## HTTP 长连接

* `Connection` 设置为 `keep-alive`

## 数据协商

### 分类

* 请求

	* `Accept`

	* `Accept-Encoding`

	* `Accept-Language`

	* `User-Agent`

* 返回

	* `Content-Type`

	* `Content-Encoding`

	* `Content-Language`

## Redirect

* `302`：暂时移动资源地址

* `301`：永久移动资源地址（**慎重操作**）

## 内容安全策略（`Content-Security-Policy`）

* 限制资源获取

* 报告资源获取越权

### 限制方式

* 响应头 `Content-Security-Policy` 和 `Content-Security-Policy-Report-Only`

* `default-src` 限制全局

* 指定资源类型来实现限制

