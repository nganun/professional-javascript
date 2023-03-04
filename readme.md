# 前言

## 1 什么是 JavaScript +

*   Book name:
    *   Professional JavaScript for Web Developer, 4th Edition
    *   每个版本的作者
        *   1st Brendan Eich
        *   3rd Nicholas Zakas
        *   4th Matt Frisbie / 马特-弗里斯比 / 4th

### 1.1 简短的历史回顾

### 1.2 JavaScript 实现

*   核心 ECMAScript
*   DOM
*   BOM

## 2 HTML 中的 JavaScript +

### 2.1 script 属性

*   async
    *   表示立即开始下载脚本，但不能阻止其它页面动作
    *   与 defer 的不同时，并不能保证按照它们出现的顺序执行
    *   异步脚本不应该在加载期间修改 DOM，异步脚本会在页面的 load 事件前执行
    *   只对外部脚本文件有效
*   defer
    *   表示在文档解析和显示完成后再执行脚本是没有问题的。
    *   只对外部脚本有效
*   crossorigin
    *   配置相关请求的 CORS （跨域资源共享）设置，默认不使用 CORS。
    *   crossorigin="anonymous" 配置谁的请求不必设置凭据标志
    *   crossorigin="use-credentials" 设置凭据标志，意味着出站请求会包含凭据
*   integrity
    *   允许比对接收到的资源和指定的加密签名以验证子资源完整性（SRI， Subresource Intergrity）
    *   如果接收到的资源的签名与这个属性指定的签名不匹配，则页面会报错，脚本不会执行。
    *   这个属性可以用于确保内容分发网络（CDN, Content Delivery Network）不会提供恶意内容。
*   type
    *   代替 language，表示代码块中脚本语言的内容类型（出称 MIME 类型）
    *   按照惯例，这个值始终都是 "text/javascript"
*   language
    *   废弃
*   charset
    *   使用 src 属性指定的代码字符集；很少使用

### 一些规范

*   script 标签要前后对应
*   JavaScript 放在 body 元素页面内容的后面

### noscript 元素

noscript 元素的出现，被用于给不支持 JavaScript 的浏览器提供替代内容。

## 3 语言基础

### 3.1 语法

#### 3.1.1 区分大小写

#### 3.1.2 标识符

> 定义：变量、属性、函数或函数参数的名称

1.  第一个字符必需是字母、下划线或美元符号；剩下的其他字符可以是字母、下划线、美元符号或数字
2.  标识符中的字母可以是 Extended ASCII 中的字母，也可以是 Unicode 的字母；但不推荐使用。
3.  按照惯例，ECMAScript 标识符使用驼峰大小写形式

#### 3.1.3 注释

*   单行注释
*   多行注释

#### 3.1.4 严格模式

> 定义：ECMAScript3 的一些不规范拍给你发在这种模式下会被处理，对于不安全的活动将抛出错误

"use strict";

*   可以单独指定一个函数在严格模式下执行，只需要把这个预处理指令放到函数体开关即可

#### 3.1.5 语句

*   即使语句末尾的分号不是必需的，也应该加上 加分号有助于防止省略造成的问题
    *   避免内容输入不完整
    *   有助于开发者通过删除空行来压缩代码（如果没有结尾的分号，只删除空行，则会导致语法错误）
    *   加分号在某些情况下有助于提升性能，因为解析器会尝试在合适的位置补上分号以纠正语法错误

#### 3.2 关键字与保留字

> 按照规定，保留的关键字不能用作标识符或属性名

1. 关键字列表

break, case, catch ,calss, const, continue, debugger, default, delete, do,
else, export, extends, finally, for, fnction, if, import, in, instanceof,
new, return, super, switch, this, throw, try, type, var, void,
while, with, yield

2. 未来的保留字

- 始终保留

    enum

- 严格模式下保留

    implements, interface, let, package, protected, private, public, static

- 模块代码中保留

    await

    > 一般来说，不要把关键字与保留字作为标识符，以确保兼容过去和未来的 ECMAScript 版本

### 3.3 变量

## 4 变量、作用域与内存

## 5 基本引用类型

## 6 集合引用类型

## 7 迭代器与生成器

## 8 对象、类与面向对象编程

## 9 代理与反射

## 10 函数 \*

## 11 其约与异步函数

## 12 BOM

## 13 客户端检测

## 14 DOM

## 15 DOM 扩展

## 16 DOM2 和 DOM3

## 17 事件

## 18 动画与 Canvas 图形

## 19 表单脚本

## 20 JavaScript API

## 21 错误处理与调试

## 22 处理 XML

## 23 JSON +

JSON: JavaScript Object Notation

### 23.1 语法

> JSON 语法支持表示 3 种类型的值。

*   简单值: 字符串、数值、布尔值、null
*   对象
*   数组

    JSON 与 JS 的不同点

*   没有变量声明（JSON 中没有变量），最后也没有分号
*   属性必需要用双引号包裹起来；手动编写 JSON 时漏掉双引号或者使用单引号是觉错误

### 23.2 解析与序列化

#### 23.2.1 JSON 对象

*   stringify(): 将 JS 对象序列化为 JSON 字符串；默认会输出不包含空格或缩进的 JSON 字符串
    *   在序列化 JavaScript 对象时，所有函数和原型成员都会有意地在结果中省略；
    *   此外 undefined 的任何属性也会被路过；最终得到的就是所有实例属性均为有效 JSON 数据类型的表示。
*   parse(): 将 JSON 解析为原生的 JS 对象

#### 23.2.2 序列化选项

JSON.stringify(value\[, replacer\[, space]])

*   replacer 可以为数组或函数，undefined 的值不传递
*   space 可以为数字或字符串，最大长度为 10。为数值时，表示空格

##### Example

```js
let book = {
title: "Professional JavaScript",
authors: [
"Nicholas C. Zakas",
"Matt Frisbie"
],
edition: 4,
year: 2017
};
// Example1: 传递数组
let jsonText = JSON.stringify(book, ["title", "edition"]);
console.log(jsonText); // {"title":"Professional JavaScript","edition":4}
// Example2: 传递函数
jsonText = JSON.stringify(book, (key, value) => {
switch(key) {
case "authors":
return value.join(",");
case "year":
return 5000;
case "edition":
return undefined;
default:
return value;
}
});
console.log(jsonText); // {"title":"Professional JavaScript","authors":"Nicholas C. Zakas,Matt Frisbie","year":5000}
// Example3: 字符串缩进 - 数字，默认为空格
jsonText = JSON.stringify(book, null, 4);
console.log(jsonText);
// Example4: 字符串缩进 - 字符
jsonText = JSON.stringify(book, null, "--");
console.log(jsonText);
```

#### toJSON() 方法

*   在 JSON.stringify() 之前自定义 JSON 序列化，此时就要在序列化的对象中添加 toJSON() 方法。
*   箭头函数不能用来定义 toJSON（) 方法，主要原因是箭头函数的记忆法作用域是全局作用域，在这种情况下不合适。

    ```js
    let book = {
    title: "Professional JavaScript",
    authors: [
    "Nicholas C. Zakas",
    "Matt Frisbie"
    ],
    edition: 4,
    year: 2017,
    toJSON: function() {
    return this.title;
    }
    };
    let jsonText = JSON.stringify(book);
    console.log(jsonText);  // "Professional JavaScript"
    ```

#### 23.2.3 解析选项

*   JSON.parse(text\[, reviver]) 方法也可以传递一个额外的参数,这个函数会针对每个键值对都调用一次.

    ```js
    let book = {
    title: "Professional JavaScript",
    authors: [
    "Nicholas C. Zakas",
    "Matt Frisbie"
    ],
    edition: 4,
    year: 2017,
    releaseDate: new Date(2017, 11, 1)
    };
    let jsonText = JSON.stringify(book);
    console.log(jsonText);  // {"title":"Professional JavaScript","authors":["Nicholas C. Zakas","Matt Frisbie"],"edition":4,"year":2017,"releaseDate":"2017-11-30T16:00:00.000Z"}
    let bookCopy = JSON.parse(jsonText, (key, value) => key == "releaseDate" ? new Date(value) : value);
    console.log(bookCopy.releaseDate.getFullYear());  // 2017
    ```

## 24 网络请求与远程资源

Ajax - Asynchronous\[eɪˈsɪŋkrənəs] JavaScript and XML

### 24.1 XMLHttpRequest

#### 24.1.1 使用 XHR

*   声明 XHR
    *   `let xhr = new XMLHttpRequest();`
*   请求准备：`xhr.open("get", "example.php", true)`
    *   使用 XHR 首先要调用 open(请求类型、请求URL，是否异步) 方法
*   请求发送：`xhr.send(null)`
    *   如果不需要请求体，必需传 null
    *   调用 send() 后，请求会发送到服务器
*   数据接收：当 xhr 收到响应后，xmr 的以下属性会被填充上数据
    *   responseText: 作为响应体返回的文本
    *   responseXML: 如果响应体内容是 xml，返回对应的数据
    *   status: 响应的 Http 状态
        *   状态码 2xx 表示 成功；304 表示资源未修改过，从浏览器缓存中直接拿取。
    *   statusText: 响应的 Http 状态描述
*   `readyState` 属性，表示当前处在请求/响应过程的哪个阶段； 每次 readyState 从一个值变成另一个值，都会触发 `readystatechange` 事件。为保证跨浏览器的兼容性，onreadystatechange 事件处理程序应该在调用 open() 之前赋值
    *   0：未初始化(Uninitialized)。尚未调用 open() 方法
    *   1: 已打开（Open)。已调用 open()方法，尚未调用 send() 方法
    *   2：已改送(Send)。已调用 send() 方法，尚未收到响应
    *   3: 接收中(Receiving)。已经收到部分响应
    *   4: 完成(Complete)。已经收到所有响应，可以使用了。
*   `abort()` 方法：在收到响应之前如果想取消异步请求，可以调用 abort() 方法。

    ```js
    let xhr = new XMLHttpRequest();
    xhr.onreadystatechange = function() {
    if (xhr.readyState == 4) {
    if (xhr.status >= 200 && xhr.status < 300 || xhr.status == 304) {
    console.log(xhr.responseText);
    } else {
    console.log("Request was unsuccessful: " + xhr.status);
    }
    }
    }
    xhr.open("get", "https://img-home.csdnimg.cn/data_json/toolbar/toolbar1105.json", true);
    xhr.send(null);
    ```

#### 24.1.2 HTTP 头部

*   XHR 会默认发送一些 HTTP 头部信息
    *   Accept: 浏览器可以处理的内容类型
    *   Accept-Charset: 浏览器可以显示的字符集
    *   Accept-Encoding: 浏览器可以处理的压缩编码类型
    *   Cookie: 页面中设置的 Cookie
    *   Host: 发送请求的页面所在域
*   如果需要发送额外的请求头部，可以使用 setRequestHeader(name, value);
*   setRequestHeader() 方法要写在 open() 之前、send() 之后
*   getResponseHeader(name) 方法获取响应头部信息
*   getAllRequestHeaders() 方法获取所有头部信息

    ```js
    let xhr = new XMLHttpRequest();
    xhr.onreadystatechange = function () {
    if (xhr.readyState == 4) {
    if (xhr.status >= 200 && xhr.status < 300 || xhr.status == 304) {
    console.log(xhr.responseText);
    let myHeader = xhr.getResponseHeader("MyHeader");
    let allHeaders = xhr.getAllResponseHeaders();
    console.log(myHeader);  // null - 很奇怪
    console.log(allHeaders);
    } else {
    console.log("Request was unsuccessful: " + xhr.status);
    }
    }
    }
    xhr.open("get", "https://img-home.csdnimg.cn/data_json/toolbar/toolbar1105.json", true);
    xhr.setRequestHeader("MyHeader", "MyValue")
    xhr.send(null);
    ```

#### 24.1.3 GET 请求

> URI 与 URL

URI = Uniform Resource Identifier 统一资源标志符
URL = Uniform Resource Locator 统一资源定位符
URN = Uniform Resource Name 统一资源名称
大白话，就是URI是抽象的定义，不管用什么方法表示，只要能定位一个资源，就叫URI，本来设想的的使用两种方法定位：1，URL，用地址定位；2，URN 用名称定位。
举个例子：去村子找个具体的人（URI），如果用地址：某村多少号房子第几间房的主人 就是URL， 如果用身份证号+名字 去找就是URN了。

*   GET 请求用于向服务器查询某些信息。
*   对于 XHR 而言，查询字符串必须正确编码后添加到 URL 后面，然后再传给 open() 方法。
*   URL 中的请求参数与值都必须使用 encodeURIComponent() 编码。

    ```js
    function addURLParam(url, name, value) {
    url += (url.indexOf("?") == -1 ? "?" : "&");
    url += encodeURIComponent(name) + "=" + encodeURIComponent(value);
    return url;
    }
    let url = "example.php"
    url = addURLParam(url, "name", "Nicholas");
    url = addURLParam(url, "book", "Professional Javascript");
    console.log(url); // example.php?name=Nicholas&book=Professional%20Javascript
    xhr.open("get", url, false);
    ```

#### 24.1.4 POST 请求

*   POST 请求用于向服务器发送应该保存的数据。
*   使用 XHR 模拟表单提交；把 Content-Type 头部设置为 "application/x-www-formurlencoded"，这是提交表单时使用的内容类型
*   创建对应格式的字符串。如果确实有一个表单需要序列化并通过 XHR 发送到服务器，可以使用 serialize() 函数来创建应用的字符串

    ```js
    xhr.open("post", postexample.php", true);
    xhr.setRequestHeader("Content-Type", "application/-x-www-formurlencoded");
    let form = document.getElementById("user-info");
    xhr.send(serialize(form));
    ```

#### 24.1.5 XMLHttpRequest Level 2

##### FormData 类型

*   FormData 类型便于表单序列化
    *   let data = new FormData();
    *   data.append("name", "Nicholas");
*   通过直接给 FormData 构造函数传入一个表单元素，也可以将表单中的数据作为键值对填充进去。
    *   let data = new FormData(document.forms\[0]);
*   不再需要给 XHR 对象显示设置任何请头部。

    ```js
    xhr.open("post", postexample.php", true);
    let form = document.getElementById("user-info");
    xhr.send(new FormData(form)));
    ```

##### 超时

*   给 timeout 属性设置了一个时间，且在该时间内没有收到响应时，中断请求，XHR 对象就会触发 timeout 事件。
*   在超时之后访问 status 属性会发生错误。为做好防护，可以把检查 status 属性的代码封装在 try/catch 语句中。

    ```js
    let xhr = new XMLHttpRequest();
    xhr.onreadystatechange = function () {
    try {
    if (xhr.readyState == 4) {
    if (xhr.status >= 200 && xhr.status < 300 || xhr.status == 304) {
    console.log(xhr.responseText);
    } else {
    console.log("Request was unsuccessful: " + xhr.status);
    }
    }
    } catch (ex) {
    }
    }
    xhr.open("get", "https://img-home.csdnimg.cn/data_json/toolbar/toolbar1105.json", true);
    xhr.timeout = 1000;
    xhr.ontimeout = function () {
    console.log("Request didn't not return in a second.")
    }
    xhr.send(null);
    ```

##### overrideMineType() 方法

```js
// 假定服务器实际发送了 XML 数据，但响应头设置的 MIME 类型是 text/plain，就会导致 responseXML 属性值是 null。
xhr.open("get", "text.php", true);
xhr.overrideMimeType("text/xml");
xhr.send(null);
```

### 24.2 进度事件

*   六个进度事件 Progress Events
    *   loadstart: 在接收到响应的第一个字节时触发
    *   progress: 在揟响应期间反复触发
    *   error: 在请求出错时触发
    *   abort: 在调用 abort() 终止连接时触发
    *   load: 在成功接收完响应时触发
    *   loadend: 在成功接收完响应时触发
*   每次请求都会首先触发 loadstart 事件，之后是一个或多个 progress 事件，接着是 error、abort 或 load 中的一个，最后以 loadend 事件结束。

#### 24.2.1 load 事件

*   以 load 事件替代 readystatechange 事件，简化交互模式；就不用再检查 readyState 属性了
*   onload 事件处理程序会收到一个 event 对象，其 target 属性设置为 XHR 实例。

    ```js
    let xhr = new XMLHttpRequest();
    xhr.onload = function() {
    if ((xhr.status >= 200 && xhr.status < 300) || xhr.status == 304) {
    alert(xhr.responseText);
    } else {
    alert("Response was unsuccessful: " + xhr.status); 
    }
    };
    xhr.open("get", "altevents.php", true);
    xhr.send(null);
    ```

#### 24.2.2 progress 事件

*   在浏览器接收数据期间，这个事件会反复触发。onpregress 事件处理程序会收到 event 对象，其 target 属性是 XHR 对象。
*   event 包含 3 个额外属性
    *   lengthComputable: 布尔值，表示进度信息是否可用
    *   position: 接收到的字节数
    *   totalSize: 是响应的 Content-Length 头部定义的总字节数
*   为了保证正确执行，必须在调用 open() 之前添加 onprogress 事件处理程序。

    ```js
    let xhr = new XMLHttpRequest();
    xhr.onload = function() {
    if ((xhr.status >= 200 && xhr.status < 300) || xhr.status == 304) {
    alert(xhr.responseText);
    } else {
    alert("Response was unsuccessful: " + xhr.status); 
    }
    };
    // 每次更新，可以看到接收数据的百分比
    xhr.onprogress = function() {
    let divStatus = document.getElementById("status");
    if (event.lengthComputable) {
    divStatus.innerHtml = "Received " + event.position + " of " + event.totalSize + " bytes"; 
    }
    }
    xhr.open("get", "altevents.php", true);
    xhr.send(null);
    ```

### 24.3 跨源资源共享

*   CORS (Cross-Origin Resource Sharing) 定义了浏览器与服务器如何实现跨源通信
*   CORS 的思路是使用自定义的 HTTP 头部允许浏览器和服务器相互了解，以确实请求或响应应该成功还是失败。
    *   发送请求 - Origin: http://www.nczonline.net
    *   服务响应请求 - Access-Control-Allow-Origin: http://www.nczonline.net
*   现代浏览器通过 XMLHttpRequest 对象原生支持 CORS。要向不同域的源发送请求，可以使用标准 XHR 对象并给 open() 方法传入一个绝对 URL
    *   `xhr.open("get", "http://www.somewhere-else.com/page/", true)`
*   出于安全考虑，跨域 XHR 有一些额外限制
    *   不能使用 setRequestHeader() 设置自定义头部
    *   不能发送和接收 Cookie
    *   getAllResponseHeaders() 方法始终返回空字符串
*   无论同域还是跨域，访问本地资源用相对 URL，访问远程资源用绝对 URL，可以区分使用场景，也可以避免访问本地资源时出现头部或 cookie 信息访问受限的问题。

#### 24.3.1 预检请求 -

#### 24.3.2 依据请求 -

### 24.4 替代性跨源技术

#### 24.4.1 图片探测 -

#### 24.4.2 JSONP

*   JSONP (JSON with padding)，会被包含在一个函数调用里
    *   `callback({"name": "Nicholas"});`
*   JSONP 格式包含两部分：回调和数据。回调是页面接收到响应之后应该调用的函数，通常回调函数的名称是通过请求来动态指定的。而数据就是作为参数传递给回调函数函数的 JSON 数据。

    ```js
    function handleResponse(response) {
    console.log(`You're at IP address ${response.ip}, which is in ${response.city}, 
    ${response.region_name}.`)
    }
    let script = document.createElement("script");
    script.src = "http://freegeoip.net/json/?callback=handleResponse";
    document.body.insertBefore(script, document.body.firstChild);
    ```

### 24.5 Fetch API

*   Fetch API 能够执行 XHR 对象的所有任务，更易使用，接口更现代化，必须异步。

#### 24.5.1 基本用法

##### 分派请求

*   fetch() 只有一个必需的参数 input，多数情况下这个参数是要获取资源的 URL。这个方法返回一个期约。

    ```js
    fetch({type: "basic", url: "github.com"})
    .then(response => {
    console.log(response); // Response {type: "basic", url: ...}
    });
    ```

##### 读取响应

```js
fetch("bar.txt")
.then(response => {
response.text().then(data => {
console.log(data);
})
});
// 上下等同
fetch("bar.txt")
.then(response => response.text())
.then(data => console.log(data));
```

##### 处理状态码和请求失败

*   response.status: 状态码
*   response.statusText: 状态文本
*   response.ok: boolean

    ```js
    // 成功获取响应请求
    fetch("bar.txt")
    .then(resp => console.log(resp.status, resp.statusText)); // 200 OK
    // 请求不存在的资源
    fetch("/does-not-exist")
    .then(resp => console.log(resp.status, resp.statusText)); // 404 Not Found
    // 服务器错误
    fetch("/throw-server-error")
    .then(resp => console.log(resp.status, resp.statusText)); // 500 Internal Server Error
    // 服务器没有响应而导致浏览器超时
    fetch("/hangs-forever")
    .then(response => console.log(response), err => console.log(err)); // TypeError: "NetworkError when attempting to fetch resource"
    ```

*   通过 url 属性检测通过 fetch() 发送请求时使用的完整 URL

    ```js
    window.location.href  // 'https://segmentfault.com/a/1190000041305485'
    fetch('qux').then(resp => console.log(resp.url)); // https://segmentfault.com/a/qux
    fetch('/qux').then(resp => console.log(resp.url));  // https://segmentfault.com/qux
    fetch('//qux').then(resp => console.log(resp.url)); // https://qux/
    fetch('https://qux.com').then(resp => console.log(resp.url)); // https://qux.com/
    ```

##### 自定义选项

*   body: Blog, BufferSource, FormData, URLSearchParams, ReadableStream, String
    *   指定使用请求体时请求体的内容
*   cache: (default), no-store, reload, no-cache, force-cache, only-if-cached
    *   用于控制浏览器与 HTTP 缓存的交互
*   credentials: (same-origin), omit, include
    *   用于指定在外发请求中如何包含 cookie
*   headers
    *   用于指定请求头部；默认值为不包含键值对的 Headers 对象
*   integrity
    *   用于强制子资源完整性；默认为空字符串
*   keepalive
    *   用于指示浏览器允许请求存在时间超出页面生命周期；默认为 false
*   method: (GET), POST, PUT, PATCH, DELETE, HEAD, OPTIONS, CONNECT, TRACE
    *   用于指定 HTTP 请求方法
*   mode: cors, no-cors, same-origin, navigate
    *   通过构造函数手动创建 Request 实例时，默认为 cors；否则，默认为 no-cors
*   redirect: (follow), error, manual
    *   用于指定如何处理重定向响应（状态码为 301, 302, 303, 307, 308）
*   referrer: (client/about:client), no-referrer, <URL>
    *   用于指定 HTTP 的 Referer 头部的内容
*   referrerPolicy: (no-referrer-when-downgrade), no-referrer, origin, same-origin, strict-origin, origin-when-cross-origin, strict-origin-when-cross-origin, unsafe-url
    *   用于 HTTP 的 Referer 头部
*   signal
    *   用于支持通过 AbortController 中断进行中的 fetch() 请求

#### 24.5.2 常见 Fetch 请求模式

##### 1 发送 JSON 数据

```js
let payload = JSON.stringify({foo: 'bar'});
let jsonHeaders = new Headers({'Content-Type': 'application/json'});
fetch('/send-me-json', {
method: 'POST', // 发送请求时必须使用一种 HTTP 方法
body: payload,
headers: jsonHeaders
});
```

##### 2 在请求体中发送参数

```js
let payload = 'foo=bar&baz=qux';
let paramHeaders = new Headers({'application/x-www-form-urlencoded; charset=UTF-8});
fetch('/send-me-params', {
method: 'POST', // 发送请求时必须使用一种 HTTP 方法
body: payload,
headers: paramHeaders
});
```

##### 3 发送文件

> 因为请求体支持 FormData 实现，所以 fetch() 也可以序列化并发送文件字段中的文件

```js
let imageFormData = new FormData();
let imageInput = document.querySelector("input[type='file']");
imageFormData.append('image', imageInput.files[0]);
fetch('/img-upload', {
method: 'POST', // 发送请求时必须使用一种 HTTP 方法
body: imageFormData
});
// 多个文件
let imageFormData = new FormData();
let imageInput = document.querySelector("input[type='file'][multiple]");
for (let i = 0; i < imageInput.files.length; i++) {
imageFormData.append('image', imageInput.files[i]);
}
fetch('/img-upload', {
method: 'POST', // 发送请求时必须使用一种 HTTP 方法
body: imageFormData
});
```

##### 4 加载 Blob 文件

```js
const imageElement = document.querySelector('img');
fetch('my-image.png')
.then(resp => resp.blob())
.then(blob => {
imageElement.src = URL.createObjectURL(blob);
});
```

##### 5 发送跨源请求

*   跨源请求时，响应要包含 CORS 头部才能保证浏览器收到响应。没有时会发出错误
    *   TypeError: Failed to fetch
    *   No 'Access-Control-Allow-Origin' header is present on the requested resource.
*   如果代码不需要访问响应，也可以发送 no-cors 请求。此时响应的 type 属性值为 opaque，因此无法读取响应内容。这种方式适合改善探测请求或者将响应缓存起来供以后使用。

    ```js
    fetch('//cross-origin.com', {method:; 'no-cors'})
    .then(resp => console.log(resp.type))
    ```

##### 6 中断请求

*   Fetch API 支持通过 AbortController/AbortSignal 对中断请求。

    ```js
    let abortController = new AbortController();
    fetch('wikipedia.zip', {signal: abortController.signal})
    .catch(() => console.log('aborted!'));
    // 10 毫秒后中断请求
    setTimeout(() => abortController.abort(), 10);
    ```

## 25 客户端存储

## 26 模块

## 27 工作者线程

## 28 最佳实践
