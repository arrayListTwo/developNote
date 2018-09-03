# Promise对象

> 异步执行，需要使用回调函数

> 承诺将来会执行的对象在JavaScript中称为`Promise`对象,`ES6`引入

> `Promise`对象在创建时，立即得到执行

#### 简单示例

```JavaScript
function test(resolve, reject) {
    var timeOut = Math.random() * 2;
    log('set timeout to: ' + timeOut + ' seconds.');
    setTimeout(function () {
        if (timeOut < 1) {
            log('call resolve()...');
            resolve('200 OK');
        }
        else {
            log('call reject()...');
            reject('timeout in ' + timeOut + ' seconds.');
        }
    }, timeOut * 1000);
}
/* 创建Promise对象，参数是一个函数，并且此函数的形参是两个函数，第一个函数是代表异步任务成功时，运行的函数；第二个函数是代表异步任务失败时，运行的函数
*/
var p1 = new Promise(test);
var p2 = p1.then(function (result) {
    console.log('成功：' + result);
});
var p3 = p2.catch(function (reason) {
    console.log('失败：' + reason);
});
```

* `Promise`对象支持链式操作

```JavaScript
// 如果异步任务执行成功，执行这个函数，即形参resolve：
p1.then(function (result) {
    console.log('成功：' + result);
});
// 如果异步任务执行失败，执行这个函数，即形参reject：
p2.catch(function (reason) {
    console.log('失败：' + reason);
});
/*链式写法*/
new Promise(test).then(function (result) {
    console.log('成功：' + result);
}).catch(function (reason) {
    console.log('失败：' + reason);
});
```

* `Promise`最大的好处是在异步执行的流程中，把执行代码和处理结果的代码清晰地分离

<center>![](https://i.imgur.com/LL6Wnkb.png)</center>

#### 执行若干异步任务

* 需要先做任务1，如果成功后再做任务2，任何任务失败则不再继续并执行错误处理函数

```JavaScript
// job1、job2和job3都是Promise对象
job1.then(job2).then(job3).catch(handleError);
```

```JavaScript
// 0.5秒后返回input*input的计算结果:
function multiply(input) {
    return new Promise(function (resolve, reject) {
        log('calculating ' + input + ' x ' + input + '...');
        setTimeout(resolve, 500, input * input);
    });
}

// 0.5秒后返回input+input的计算结果:
function add(input) {
    return new Promise(function (resolve, reject) {
        log('calculating ' + input + ' + ' + input + '...');
        setTimeout(resolve, 500, input + input);
    });
}

var p = new Promise(function (resolve, reject) {
    log('start new Promise...');
    resolve(123);
});

p.then(multiply)
 .then(add)
 .then(multiply)
 .then(add)
 .then(function (result) {
    log('Got value: ' + result);
});
```

* `AJAX`异步执行函数转换为`Promise`对象

```JavaScript
'use strict';

// ajax函数将返回Promise对象:
function ajax(method, url, data) {
    var request = new XMLHttpRequest();
    return new Promise(function (resolve, reject) {
        request.onreadystatechange = function () {
            if (request.readyState === 4) {
                if (request.status === 200) {
                    resolve(request.responseText);
                } else {
                    reject(request.status);
                }
            }
        };
        request.open(method, url);
        request.send(data);
    });
}
var log = document.getElementById('test-promise-ajax-result');
var p = ajax('GET', '/api/categories');
p.then(function (text) { // 如果AJAX成功，获得响应内容
    log.innerText = text;
}).catch(function (status) { // 如果AJAX失败，获得响应代码
    log.innerText = 'ERROR: ' + status;
});

```

#### 使用`Promise`对象实现并行执行两个异步函数

```JavaScript
var p1 = new Promise(function (resolve, reject) {
    setTimeout(resolve, 500, 'P1');
});
var p2 = new Promise(function (resolve, reject) {
    setTimeout(resolve, 600, 'P2');
});
// 同时执行p1和p2，并在它们都完成后执行then:
Promise.all([p1, p2]).then(function (results) {
    console.log(results); // 获得一个Array: ['P1', 'P2']
});
```

#### 并行执行两个异步函数，先成功者即执行resolve，后成功者放弃

```JavaScript
var p1 = new Promise(function (resolve, reject) {
    setTimeout(resolve, 500, 'P1');
});
var p2 = new Promise(function (resolve, reject) {
    setTimeout(resolve, 600, 'P2');
});
Promise.race([p1, p2]).then(function (result) {
    console.log(result); // 'P1'
});
```