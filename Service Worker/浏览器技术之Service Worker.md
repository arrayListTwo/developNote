# 浏览器技术之 Service Worker

## 渐进式网络应用 PWA

Web应用 和 Native 应用有着各自不同的优势和使用场景

PWA 结合了二者的优势

PWA 会越来越流行

​	Web 应用的资源存储在服务器，Native 的资源存储在本地。 所以 Native 会比 Web 应用的加载速度和流畅性方面获得更好的表现；

​	PWA 旨在创造拥有更加流畅的用户体验的 Web 应用，和创建类 Native App 的沉浸式效果，而非浏览器端那样的外观和体验；

​	在各种网络和数据加载的条件下仍然可用 - 它可以在网络不稳定或者没有网络的情况下使用。

​	Service Worker 是 PWA 的关键技术，可以支持一些原生应用的功能

​		友好的弱网和离线体验

​		定期的后台同步

​		推送通知

## Service Worker

>  Service Worker 本质上充当 Web 应用程序、浏览器与网络（可用时）之间的代理服务器

这个 API 旨在创建有效的离线体验，它会拦截网络请求并根据网络是否可用来采取适当的动作、更新来自服务器的资源。它还提供入口以推送通知和访问后台同步 API。

### Web Worker

- JavaScript 是一个单线程的语言
- 异步编程通过调度一部分代码在 event loop 中执行，从而让程序流畅地运行
- Web Worker 是真正的多线程
- Service Worker 是 Web Worker 的一个子类

### Service Worker 的特性

- 它是一种 Web Worker，不能直接访问 DOM
- 有自己独立的生命周期，不和特定网页相关联
- 是一个由事件驱动的 worker，它由源和路径组成
- 可以使用一些离线存储 API --- CacheStorage 和 IndexedDB，不能访问 localStorage
- 大量使用了 Promise
- 只能使用 HTTPS，localhost 也被允许

### Service Worker 的生命周期

- Service Worker 的生命周期和网页是相互独立的
- 在网页的 JS 代码中调用 Service Worker 的注册方法开始安装。在安装阶段可以进行一些缓存工作，缓存失败安装就会失败。如果安装成功，代表了缓存也成功完成了
- 安装成功后触发 activate 事件，Service Worker处于激活状态
- 激活后的 Service Worker 线程可以控制页面、监听事件了，它可以根据情况被终止或者唤起

### Service Worker 支持的事件

- install 事件会在注册完成之后触发。install 事件一般是被用来填充你的浏览器的离线缓存能力
- activate 事件在脚本激活后触发，一般在这里处理旧版本的缓存
- fetch 事件监听客户端的请求，包括任何被 Service Worker 控制的文档和文档内引用的资源。配合 respondWith() 方法，可以劫持 HTTP 响应

### 使用 Cache API 缓存资源

install 事件会在注册完成之后触发。install 事件一般是被用来填充你的浏览器的离线缓存能力。

为了达成这个目的，我们使用了 Service Worker 的新的标志性的存储 API -- cache -- 一个 Service Worker 上的全局对象，它使我们可以存储网络响应发来的资源，并且根据它们的请求来生成 key。

在安装事件的回调里我们需要完成一些缓存工作，所以需要 waitUntil() 方法来暂时挂起代码， waitUntil 方法接受一个 promise 参数。

Cache 接口为缓存的 Request / Response 对象对提供存储机制。

一个域可以有多个命名 Cache 对象。

你需要在你的脚本（例如：在 ServiceWorker 中）中处理缓存更新方式。除非明确地更新缓存，否则缓存将不会被更新；除非删除，否则缓存数据不会过期。

CacheStorage 接口表示 Cache 对象存储。

使用通过全局 caches 属性来访问 CacheStorage ，可以在 window、Service Worker 中访问。

使用 CacheStorage.open(cacheName) 打开一个 Cache 对象，再使用 Cache 对象的方法去处理缓存。

```
// CacheStorage
CacheStorage.open()
CacheStorage.keys()
CacheStorage.match()

// Cache
Cache.addAll(requests)
Cache.add(request)
Cache.put(request, response)
Cache.match(request)
Cache.delete(request)
```

### 在 install 阶段缓存资源

1、打开缓存

2、缓存文件

3、确认是否所有的静态资源已缓存

### 缓存运行时请求

- event.respondWith() 会决定如何响应 fetch 事件。caches.match() 查询请求及查找之前创建的缓存中是否有任意缓存结果并返回 promise
- 如果有，则返回该缓存资源
- 否则，执行fetch
- 检查返回的状态码是否是 200 。同时检查响应类型是否为 basic ，即检查请求是否同域。当前场景不缓存第三方资源的请求。
- 把返回数据添加到缓存中。

### 更新 Service Worker

当用户访问网络应用的时候，浏览器会在后台重新下载包含 Service Worker 代码的 .js 文件。

如果下载下来的文件和当前的 Service Worker 代码文件不同，浏览器会认为文件发生了改变并且会创建一个新的 Service Worker。

创建新的 Serivice Worker 的过程将会启动，然后触发 install 事件。然而，这时候，旧的 Service Worker 仍然控制着网络应用的页面，意味着新的 Service Worker 将会处于 waiting 状态。

一旦关闭网络应用当前打开的页面，旧的 Service Worker 将会被浏览器杀死而新安装的 Service Worker 就可以上位了。这时候将会触发 activate 事件。

这是为了避免在不同选项卡中同时运行不同版本的网络应用所造成的问题 -- 一些在网页中实际存在的问题且有可能会产生新的bug（比如当前浏览器中本地存储数据的时候却拥有不同的数据库结构）

### 在 activate 阶段清理旧版本的缓存

出现在 activate 回调中的一个常见任务是缓存管理。

这么做的原因是，如果在安装步骤中清除了任何旧缓存，则继续控制所有当前页面的任何旧 Service Worker 将突然无法从缓存中提供文件。
