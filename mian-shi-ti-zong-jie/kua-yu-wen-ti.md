# 跨域问题

### 端口号不同也算跨域

**jsonp的跨域请求是不安全的,尽量不要使用**

## jsonp的应用场景

1. 没有后台人员,对服务器操作不了,只能通过jsonp的方式实现跨域请求

   > 但是要实现jsonp跨域请求,肯定需要后台传回来的接口,说明,后台人员肯定是能操作服务器的,之所以让我们实现有三个原因: 一: 后台人员太懒,不想去操作服务器: 二: 不操作服务器是不想增加服务器的压力; 三: 后台人员不会.\(其实这个问题使后台人员可解决的,不是我们的活\)

2. 主服务器分出来的子服务器,主服务器中放着一些接口,当不需要这个接口的时候,直接在前端删除相关代码请求自服务器也是可以的

### 使用jsonp的情况

1. 数据接口,动静分离
2. 后台无法开发接口
3. 接口开了,但是用不了几天就废了

## 跨域

1. jsonp的跨域请求数据
2. iframe嵌套另一个页面
