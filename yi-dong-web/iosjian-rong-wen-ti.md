### IOS中的position：fixed中的input元素调出软键盘引起的定位出错问题（安卓正常）

**原理：**

IOS中对于固定定位（position：fixed）的元素，当软键盘唤起后，fixed元素将失效，IOS认为用户更希望元素随着滚动而移动。所以，当超出一屏滚动时，会将其当做position：absolute随页面滚动而滚动，这是IOS设计特有的机制，并不是bug

基于上述原因，可有如下**两种方案：**

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

### 移动端body设置overflow：hidden失效问题

> 场景：有弹出层锁定外层body，否则会出现双滚动条

**分析：**

整个viewport的overflow取决于html的overflow，html、body的overflow默认均为visible

* 直接设置html的overflow：hidden即可，body无需设置也不会生效
* 如果不设置html，只设置body的overflow：hidden

上面两点在大部分现代浏览器中都是可行的，但是**在IOS中不行可继续滑动**

**原理：**

IOS认为，网页内容是个整体，需要将所有内容展示出来，所以hidden不起作用，不是bug，是刻意设定

**对viewport我们无法改变，但是我们可以改变body自身的overflow**

**方案：**

将html的overflow设为auto，这样body就不会继承viewport的overflow属性，然后设置body的overflow：hidden，大部分可实现。但是对于absolute的元素会相对于viewport定位，所以可设置body的position：relative，让其他元素都相对于body定位。

在弹出框弹出时设置body的overflow：hidden，关闭时设置overflow：auto，或者去掉overflow：hidden。

```js
html{
    height: 100%;
    overflow: auto;
    -webkit-overflow-scrolling: touch; /* 解决ios滑动不流畅问题 */
}
body{
    position: relative;
    -webkit-overflow-scrolling: touch;
    width: 100%;
    height: 100%;
    overflow-x: hidden; 
    overflow-y: hidden;
}
```



