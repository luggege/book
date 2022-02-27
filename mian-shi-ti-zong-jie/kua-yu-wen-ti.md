### 跨域问题

> 浏览器的同源策略造成的：协议、域名、端口（上述三个条件不满足其一的都算跨域）

jsonp的跨域请求是不安全的,尽量不要使用

**jsonp的应用场景**

1. 没有后台人员,对服务器操作不了,只能通过jsonp的方式实现跨域请求

2. 主服务器分出来的子服务器,主服务器中放着一些接口,当不需要这个接口的时候,直接在前端删除相关代码请求自服务器也是可以的

**使用jsonp的情况**

* 数据接口,动静分离

* 后台无法开发接口

* 接口开了,但是用不了几天就废了

#### 解决跨域的几种方式

* jsonp

* * 原理：利用script标签的src属性，发送get请求不受跨域影响。缺点：只能**get**方式
  * ```js
    <script src='https://xxx.xxx.xx?key=value&callback=xxx'><script>
    ```
* iframe嵌套另一个页面

* * 二级域名相同的情况下，设置document.domain为共同那部分，在一个页面iframe引入另一个页面可以解决跨域问题
* CORS（跨域资源共享）：支持所有请求方式

* * 简单请求
  * > **GET, HEAD, POST**,并且 **Content-Type** 的值仅限于下列三者之一：
    >
    > * text/plain
    > * multipart/form-data
    > * application/x-www-form-urlencoded
  * 预检请求，option请求，后端配置白名单
* Nginx反向代理：服务器向服务器发起请求，不受浏览器的同源策略影响，因此利用Nginx充当代理服务器

* node服务做中间件代理，如**前端配置proxy**

* postMessage：跨窗口通信

* ```js
  window.postMessage(message, origin, [transfer])
  window.addEventListener("message", function receiveMessage(event) {}, false);
  ```
* websocket：建立长连接，server 与 client 都能主动向对方发送或接收数据（全双工通信）



