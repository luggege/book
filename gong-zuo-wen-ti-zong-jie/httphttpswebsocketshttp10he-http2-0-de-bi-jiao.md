### HTTP和HTTPS区别

http: 客户端直接发送URL请求服务端。

https: 1.客户端输入URL；2.服务端返回安全证书（CA申请）及公钥；3.客户端连同加密过（SSL/TLS加密传输协议）的信息传输到服务器端，服务端有唯一的钥匙解锁（私钥）解密

### http与websockets

http与https是无状态的：请求时链接tcp/ip协议管道，传输完数据后自动断开。

websockets是持久化的长连接：传输协议后不会自动断开，需要手动断开。

### http2.0相比1.0好在哪

提升了web性能，减少了网络延迟。

### 判断网络是否连通的方法

1. navigator.onLine：只在未连接到局域网或路由器时返回false，有可能在机器连接上路由器，但路由器未连接到网络时也会返回true，所以不准确
2. ajax请求静态页面或者接口来判断是否连通
3. 利用img的onerror来判断，原理同ajax。（图片加载失败触发onerror事件）



