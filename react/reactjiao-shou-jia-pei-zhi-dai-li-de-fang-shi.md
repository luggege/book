### react脚手架配置代理的两种方式

* package.json追加如下配置

```js
proxy: 'https://baidu.com'
```

缺点：无法配置多个代理

* 在src下建立setupProxy.js文件，不允许改名

```js
const proxy = require('http-proxy-middleware');

module.exports = function(app) {
    app.use(
        proxy('/api1', {
            target: 'https://baidu.com',
            changeOrigin: true, // 默认false，控制服务器收到的请求头中Host字段的值
            pathRewrite: {      // 重写请求路径（将/api1替换为空串），给服务器的路径去掉前缀
                '^/api1': ''
            }
        })
    )
}
```



