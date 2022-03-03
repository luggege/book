### hash & history

> mode: history/hash\(默认\)，本质上还是利用浏览器自身的特性，改变url但是不请求接口，监听浏览器的两个原生事件，实现前端路由，如：

* hashChange事件
* popState事件

#### history

> 记录了浏览器当前窗口的浏览历史

* pushState\({}, '', ''\)：修改search部分，三个参数：
* * state对象，popState事件触发时回调函数中的event.state可接收，可为null
  * 新页面标题，目前浏览器忽略，可为null
  * 新页面地址
* replaceState\({}, '', ''\)：替换当前历史记录

> pushState、replaceState并不会立马触发popState事件，只是url变化  
> go、back、forward或者手动点击浏览器前进和后退按钮才会触发popState

* go\(\)
* back\(\)
* forward\(\)

* state：history.state可查看到当前页面的state对象

* length：history.length浏览器历史记录的个数

```js
window.addEventListener('popstate', function(event) {
    console.log('location: ' + document.location)
    console.log('state: ' + JSON.stringify(event.state))
})
```

#### hash

> 改变的是\#后面hash部分

* 监听hashchange事件，可以拿到新旧两个url

```js
window.addEventListener('hashchange', function (e) {
  console.log(e.newURL, e.oldURL)
  var str = e.newURL.split('#')[1]
})
```

**比较：**

* hash丑，只能传短字符串，history可以传递state对象
* history模式，需要后端配合，否则（页面回退刷新？）找不到路径404的问题
* hash只能是同一文档，history可以是同源的任意文档URL
* hash浏览器都支持，history是HTML5的新特性



