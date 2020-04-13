### IOS中的position：fixed中的input元素调出软键盘引起的定位出错问题（安卓正常）

原理：IOS中对于固定定位（position：fixed）的元素，当软键盘唤起后，fixed元素将失效，IOS认为用户更希望元素随着滚动而移动。所以，当超出一屏滚动时，会将其当做position：absolute随页面滚动而滚动，这是IOS设计特有的机制，并不是bug

基于上述原因，可有如下两种方案

* 既然IOS会将fixed当作absolute处理，索性不如直接使用absolute布局。也可以在input（凡是能唤起软键盘：text、textarea、select、时间日期选择）获取焦点时，改变‘position’为’static‘或‘absolute’；失去焦点时，恢复position为‘fixed’

```js
inputFocus(){
    document.getElementsByClassName('conference')[0].parentNode.style.position = 'absolute'
},
inputBlur(bool){
    if(!bool){
        document.getElementsByClassName('conference')[0].parentNode.style.position = 'fixed'
    }
},
```

* 不让整个页面滚动，只让主体部分滚动（适用于吸底元素）

```js
<div class="wrap">
    <div class="scroll">
        <div class="top"></div>
        <div class="main"></div>
    </div>
    <div class="fix-bottom position"></div>
</div>

.scroll {
    -webkit-overflow-scrolling: touch;/* 解决ios滑动不流畅问题 */
}
```



