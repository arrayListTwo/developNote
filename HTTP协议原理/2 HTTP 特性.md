# HTTP

## CORS跨域请求的限制和解决

## CORS预请求

## 缓存 Cache-Control

### 可缓存性

* `public`

* `private`

* `no-cache`

### 到期

* `max-age=<seconds>`

* `s-maxage=<seconds>`

* `max-stale=<seconds>`

### 重新验证

* `must-revalidate`

* `proxy-revalidate`

### 其他

* `no-store`

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

## Cookie

* 服务器端，通过 `Set-Cookie` 设置

* 下次请求会自动带上

* 键值对，可以设置多个

* 属性

	* `max-age` 和 `expires` 设置过期时间
	
	* `Secure` 只在 `https` 的时候发送

	* `HttpOnly` 无法通过 `document.cookie` 访问
