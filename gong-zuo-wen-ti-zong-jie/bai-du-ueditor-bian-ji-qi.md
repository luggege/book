### 百度UEditor编辑器

[https://my.oschina.net/u/205403/blog/313180](https://my.oschina.net/u/205403/blog/313180)

这个坑娘的功能，开始时居然不知道如何触发，以为有个按钮，点击一下触发，翻阅了文档，没有发现，然后再网络上看到原来是复制粘贴非白名单内的图片到编辑框时触发，坑娘啊...............

问题又来了：今天在写百度UEditor编辑器的【取远程图片功能】时有碰到：该功能如何关闭了？

ueditor.all.js文件有个配置参数：catchRemoteImageEnable

ueditor.config.js 加上配置参数

```javascript
//抓取远程图片是否开启,默认true
,catchRemoteImageEnable:false
```

然后编辑器页面，刷新，然后复制粘贴远程图片，这时不再向服务端发送get请求catchimage。

