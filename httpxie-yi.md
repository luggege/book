#### 浏览器访问URL过程

当我们在浏览器地址栏中输入要访问的URL后，浏览器会分析出URL上的域名，通过DNS服务器会查询出域名映射的IP地址，然后浏览器生成HTTP请求，并通过TCP/IP协议发送给web服务器，web 服务器收到请求后会根据请求生成响应内容。并通过TCP/IP协议返回给客户端。（HTTP协议是TCP/IP协议族的一种）

#### TCP/IP协议

TCP/IP协议族是由一个四层协议组成的系统，这四层协议分别为：应用层、传输层、网络层、数据链路层。如下图所示：

![](/assets/tcp.png)

1. 应用层
   > 应用层一般是我们编写的应用程序，其决定了向用户提供的应用服务。应用层可以通过系统调用与传输层进行通信。  
   > 处于应用层的协议非常多，比如FTP（File Transfer Protocol 文件传输协议）、DNS（Domain Name System 域名系统）、HTTP（HyperText Transfer Protocol 超文本传输协议）等。
2. 传输层
   > 传输层通过系统调用向应用层提供处于网络连接中的两台计算机之间的数据传输功能.  
   > 在传输层有两个性质不同的协议：TCP（Transmission Control Protocol 传输控制协议）、UDP（User Data Protocol 用户数据报协议）。
3. 网络层
4. 链路层

#### DNS查询原理

#### DNS递归和迭代的区别



#### TCP握手和挥手



#### TCP和UDP区别，UDP使用场景



#### HTTPS和HTTP区别



#### http2.0相比1.0好在哪






