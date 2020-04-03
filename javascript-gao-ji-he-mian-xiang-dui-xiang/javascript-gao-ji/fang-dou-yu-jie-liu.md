### 防抖

> 利用闭包，**某个时间段内只触发执行一次函数**（举例：电梯门每当新进来一个人后都重新计算开门关门时间）
>
> 重复触发事件时，会**重新开始计时**，直到设定时间段内没有再次触发，才会执行事件

应用：登录、注册、表单提交

```js
function debounce(fn,ms){
    var timer = null
    return function(){
        if(timer !== null){
            // 计时过程中触发相同事件，取消当前计时，重新开始计时
            clearTimeout(timer)
        }
        // 当前无计时，开始计时
        timer = setTimeout(fn, ms)
    }
}

document.getElementById('id').onclick = debounce(function(){
    console.log('防抖。。。。');
}, 1000)
```

### 节流

> 类似阀门控制一样，大量重复触发事件，定期只执行一次

应用：滚动条、联想

```js
function throttle(fn,delay){
    let flag = true
    return function(){
        if(!flag){
            //休息
            return false
        }
        //工作
        flag = false
        setTimeout(() => {
            fn()
            flag = true
        },delay)
    }
}

function scrollTop(){
    var scrollTop = document.body.scrollTop || document.documentElement.scrollTop
    console.log('scrollTop: ', scrollTop);
}

window.onscroll = throttle(scrollTop, 3000)
```

### 区别

防抖：大量重复操作，按最后一次重新计时，时间到开始执行

节流：大量重复操作，休息时间内永远不会执行函数，只有到了才会执行函数



