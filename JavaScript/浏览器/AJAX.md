# AJAX

> `ajax`即为`Asynchronous JavaScript and XML`，意思就是**用JavaScript执行异步网络请求**

> `AJAX`请求是异步执行的，也就是说，要通过回调函数获得响应

## `XMLHttpRequest`对象

#### 现代浏览器编写方式

```JavaScript
function success(text) {
    var textarea = document.getElementById('test-response-text');
    textarea.value = text;
}

function fail(code) {
    var textarea = document.getElementById('test-response-text');
    textarea.value = 'Error code: ' + code;
}

// 新建XMLHttpRequest对象
var request = new XMLHttpRequest(); 

// 设置回调函数，状态发生变化时，函数被回调
request.onreadystatechange = function () { 
    if (request.readyState === 4) { // 成功完成
        // 判断响应结果:
        if (request.status === 200) {
            // 成功，通过responseText拿到响应的文本:
            return success(request.responseText);
        } else {
            // 失败，根据响应码判断失败原因:
            return fail(request.status);
        }
    } else {
        // HTTP请求还在继续...
    }
}

// 发送请求:
request.open('GET', '/api/categories');
request.send();

alert('请求已发送，请等待响应...');
```

#### 低版本`IE`，需要换一个`ActiveXObject`对象

```JavaScript
function success(text) {
    var textarea = document.getElementById('test-ie-response-text');
    textarea.value = text;
}

function fail(code) {
    var textarea = document.getElementById('test-ie-response-text');
    textarea.value = 'Error code: ' + code;
}

var request = new ActiveXObject('Microsoft.XMLHTTP'); // 新建Microsoft.XMLHTTP对象

request.onreadystatechange = function () { // 状态发生变化时，函数被回调
    if (request.readyState === 4) { // 成功完成
        // 判断响应结果:
        if (request.status === 200) {
            // 成功，通过responseText拿到响应的文本:
            return success(request.responseText);
        } else {
            // 失败，根据响应码判断失败原因:
            return fail(request.status);
        }
    } else {
        // HTTP请求还在继续...
    }
}

// 发送请求:
request.open('GET', '/api/categories');
request.send();

alert('请求已发送，请等待响应...');
```

#### 兼容性写法

* 通过检测`window`对象是否有`XMLHttpRequest`属性来确定浏览器是否支持标准的`XMLHttpRequest`

```JavaScript
var request;
if (window.XMLHttpRequest) {
    request = new XMLHttpRequest();
} else {
    request = new ActiveXObject('Microsoft.XMLHTTP');
}
```

* 当创建了`XMLHttpRequest`对象后，要先设置`onreadystatechange`的回调函数。在回调函数中，通常我们只需通过`readyState === 4`判断请求是否完成，如果已完成，再根据`status === 200`判断是否是一个成功的响应

* `XMLHttpRequest`对象的`open()`方法有`3`个参数，第一个参数指定是`GET`还是`POST`，第二个参数指定`URL`地址，第三个参数指定是否使用异步，默认是`true`
	* **注意：**千万不要把第三个参数指定为`false`，否则浏览器将停止响应，直到`AJAX`请求完成。如果这个请求耗时10秒，那么10秒内你会发现浏览器处于“假死”状态

## 安全限制/同源策略

> 完全一致的意思是，域名要相同（www.example.com和example.com不同），协议要相同（http和https不同），端口号要相同（默认是:80端口，它和:8080就不同）

* 通过`Flash`插件发送HTTP请求，此种方式可以绕过浏览器的安全限制，但必须安装`Flash`，并且跟`Flash交互`，不建议使用

* 在同源域名下架设一个代理服务器来转发，`JavaScript`负责把请求发送到代理服务器上，代理服务器再把结果返回，这样就遵守了浏览器的同源策略。服务器需要额外开发。

#### JSONP方式

* `JSONP`方式，此种方式只能使用`GET`请求，并且要求返回`JavaScript`，这种方式跨域实际上是利用了浏览器允许跨域引用`JavaScript`资源

* `JSONP`方式通常以函数调用的方式返回，预先定义好回调函数名称，动态读取外域的JavaScript资源，等待回调即可

```JavaScript
/* 动态引入js标签，并从外域引入js资源，定义回调函数 */
function getPrice() {
    var
        js = document.createElement('script'),
        head = document.getElementsByTagName('head')[0];
    js.src = 'http://api.money.126.net/data/feed/0000001,1399001?callback=refreshPrice';
    head.appendChild(js);
}
```

## CORS跨域 -- HTML5跨域规范

* CORS需要浏览器和服务器同时支持。目前，所有浏览器都支持该功能，IE浏览器不能低于IE10。

* 整个CORS通信过程，都是浏览器自动完成，不需要用户参与。对于开发者来说，CORS通信与同源的AJAX通信没有差别，代码完全一样。浏览器一旦发现AJAX请求跨源，就会自动添加一些附加的头信息，有时还会多出一次附加的请求，但用户不会有感觉。

* 因此，实现CORS通信的关键是服务器。只要服务器实现了CORS接口，就可以跨源通信。