### setTimeout

> setTimeout\(fn, \[delay\], \[arg\]\)，遇到正在执行的代码阻塞，可能会超时执行

```js
// 用setInterval实现setTimeout

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
// 用setTimeout实现setInterval

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

### requestAnimationFrame

> 一个专门的循环函数，旨在浏览器中高效的运行动画，在浏览器重新加载显示内容之前执行指定的代码块，从而允许动画以适当的帧速率运行，而不管它在什么环境中运行，可运行多次。解决setInterval会丢帧的问题

```js
// 不指定时间间隔，在当前条件下尽可能快速平稳的运行它
var raf = requestAnimationFrame()

// 取消
cancelAnimationFrame(raf)
```



