### 防抖

> 利用闭包，**某个时间段内只触发执行一次函数**（举例：电梯门每当新进来一个人后都重新计算开门关门时间）
>
> 重复触发事件时，会重新开始计时，直到设定时间段内没有再次触发，才会执行事件

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
}, 2000)
```

### 节流



