### web的缓存技术---性能优化

> 缓存静态资源（js、css、img）提升页面加载速度

* 浏览器缓存
* DNS缓存
* CDN缓存
* 反向代理缓存
* 数据库缓存

浏览器==发起web请求==》代理服务器==转发请求==〉源服务器

#### 浏览器缓存

> 是否缓存？缓存时间？由服务端决定，在network的请求头中的cache-control可以看到这些信息

* 强缓存
* * **cache-control**
  * * max-age：缓存的最大周期（秒），超出这个时间过期，与expires相反，相对于请求的时间，优先级高于expires
    * s-maxage：覆盖max-age或者expires，只能用于publc 如CDN，只能用于共享缓存
    * private：表明响应只能被单个用户缓存，不能作为共享缓存（即代理服务器不能缓存它），自己的服务器
    * public：默认，可以被任何对象缓存
    * no-cache：并不代表浏览器不缓存，而是缓存前向服务器确认资源是否被更改，为了保险同时设置private，max-age=0，no-cache
    * no-store：绝对禁用缓存
  * **Expires**
  * * 设置服务端的缓存过期时间
* 协商缓存

* * Last-Modified
  * Etag



