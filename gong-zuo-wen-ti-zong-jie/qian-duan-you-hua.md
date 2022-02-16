### 性能优化

1. css/js/图片压缩
2. 提高复用性
3. 减少http请求
4. js脚本底部加载

#### JS延迟加载

1. setTimeout

   ![](/assets/setTimeout-js.png)

2. script标签放到页面最后执行

3. $.getScript\(‘out.js’，function\(\){} \)加载脚本![](/assets/getScript.png)

4. defer和async（相同点：异步加载脚本；不同点：defer是**文档**加载完后执行脚本，async下载完立马执行**脚本**然后再继续解析文档）

5. 动态创建DOM方式![](/assets/js-dom.png)

### 雅虎 13条技巧提高网页速度

网页打开速度,是网站做SEO的一个重要方面,包括搜索引擎本身也会对自己的网页考虑这个问题:最近，雅虎的Exceptional Performance团队在其开发者网络上提出了提高网页打开速度的13条规则，其中包括“减少http请求“，避免网页转向"等具体内容如下：

* 1.减少http请求
* 2.减少多媒体，图片，声音的使用，传输以文字内容为先
* 3.用截止时间报头，由于时间是将来，对于缓存来说，可以减少部分http请求
* 4.支持Gzip
* 5.把CSS放在网页的顶部
* 6.活动的脚本文件放在底部
* 7.避免用CSS Expressions 
* 8.把JavaScript和CSS单独化，与网页分离
* 9.减小DNS查表时间
* 10.最小化JavaScript
* 11.避免网页的转向
* 12.删除重复的脚本 
* 13.配置Etags\(注：etags就是emacs的建表程式\) 

//post比get安全一点,地址栏看不到你的信息.\(但是post也会被抓包\)  
//get发送表单数据,post请求表单

响应式布局: \(媒体查询\)会改变板式布局  
屏幕自适应: \(rem/em\)不会改变板式布局

mvc: 作用:降低代码耦合度, 是一种开发模式思想  
factory: 和数据库访问相关的逻辑

