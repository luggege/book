### http与https协议

http: 客户端直接发送URL请求服务端。

https: 1.客户端输入URL；2.服务端返回安全证书及公钥；3.客户端连同加密过的信息传输到服务器端（有唯一的钥匙解锁）。

### http与websockets

http与https是无状态的：请求时链接tcp/ip协议管道，传输完数据后自动断开。

websockets是持久化的：传输协议后不会自动断开，需要手动断开。



