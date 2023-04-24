### setTimeout

> setTimeout\(fn, \[delay\], \[arg\]\)，遇到正在执行的代码阻塞，可能会超时执行

* 用setInterval实现setTimeout

```js
mySetTimeout(() => {
    console.log('mySetTimeout')
}, 1000)

function mySetTimeout(callback, ms) {
    var timer = setInterval(() => {
        callback()
        clearInterval(timer)
    }, ms)
}
```

### setInterval

```js
mySetInterval(() => console.log('mySetInterval'), 1000)

function mySetInterval(callback, ms) {
    var timer = setTimeout(() => {
        callback();
        clearTimeout(timer)
        mySetInterval(callback, ms)
    }, ms)
}
```

* 用setTimeout实现setInterval

```js
var timer = myInterval(() => {
    console.log('myInterval')
}, 1000)

function myInterval(callback, ms) {
    let timer = null
    function fn() {
        callback()
        let intervalId = timer
        // 重复调用
        timer = setTimeout(fn, ms)
        // 清空上一次的定时器
        clearTimeout(intervalId)
        return intervalId
    }
    return setTimeout(fn, ms)
}

function clearMyInterval(intervalId) {
    clearTimeout(intervalId)
}
```

#### 为什么要用setTimeout 替代setInterval

* setInterval 会无视错误代码，即使代码报错，也会一直执行下去
* setInterval 会无视网络延迟，比如1s更新一次数据的需求，假如服务器请求数据发生延迟等情况，setInterval 不会等数据请求完才会执行下一次请求，而是时间到了就会再次请求，很容易造成请求堵塞，或者渲染堵塞，严重的会之间卡死
* setInterval 会出现越跑越快的问题

### requestAnimationFrame

> 一个专门的循环函数，旨在浏览器中高效的运行动画，在浏览器重新加载显示内容之前执行指定的代码块，从而允许动画以适当的帧速率运行，而不管它在什么环境中运行，可运行多次。解决setInterval会丢帧的问题

**requestAnimationFrame与setTimeout相比**

* requestAnimationFrame最大的优势是由浏览器决定回调函数的执行时机，即紧跟浏览器的刷新步调
* 其次，CPU节能：setTimeout实现的动画，当页面被隐藏或最小化时，setTimeout仍然在后台执行动画任务（只不过执行时间有所延迟），但其实此时页面不可见，刷新动画没有意义，而且还浪费CPU资源和电池寿命。而requestAnimationFrame不同，当页面处于未激活状态时，页面的屏幕绘制任务会被浏览器暂停，requestAnimationFrame停止渲染，当页面再次激活时，动画会从上次停留的地方继续执行，有效节省了CPU开销，提升性能和电池寿命。
* 也解决了setInterval会丢帧的问题

```js
// 不指定时间间隔，在当前条件下尽可能快速平稳的运行它
var raf = requestAnimationFrame()

// 取消
cancelAnimationFrame(raf)
```



