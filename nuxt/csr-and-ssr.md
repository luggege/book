### 客户端渲染 & 服务端渲染

* CSR：用户请求页面，服务端返回模版页面，浏览器解析页面代码，通过js发起ajax请求拿到数据，利用模版引擎（Vue、React、Angular）渲染页面，注入到body中（浏览器审查元素，看不到body中的html结构）
* SSR：用户请求页面，服务端拿到自己的数据，利用服务端的模版引擎（Next、Nuxt、ejs），渲染带数据的页面，然后将完整的html结构返回到客户端，插入到body中（能看到）

#### 优缺点对比

* CSR：减轻服务器的压力，前后端完全分离，但是不利于SEO优化
* SSR：有利于SEO优化，但是对服务器性能配置要求高

实际：开发中，CSR与SSR相结合使用



