# 事件

> 描述的是从页面中**接收事件的顺序**。

IE的事件流是事件**冒泡流**，

Netscape Communicator的事件流是事件**捕获流**。

### 注册事件的方式

1. onclick
2. addEventListener \*IE9+以上支持, this--&gt;target,调用的时候,系统会默认的传一个event进去,当触发事件的时候就会获取到目标事件的一些信息
3. attachEvent \*IE6~10支持,this--&gt;window,事件对象只能通过window.event获取

### 事件执行的顺序

**先捕获，后冒泡**

所有事件的**顺序**：其他元素**捕获**阶段事件 ==》**目标阶段**（按注册事件**先后顺序**）==〉其他元素**冒泡**阶段事件

```js
<div id="div1">
    div1
    <div id="div2">
        div2
        <div id="div3">
            div3
            <div id="div4">
                div4
            </div>
        </div>
    </div>
</div>
<script>
// addEventListener 默认false冒泡事件
document.getElementById('div1').addEventListener("click",function(){alert("1");},false);
document.getElementById('div4').addEventListener("click",function(){alert("4-2");},false);
document.getElementById('div2').addEventListener("click",function(){alert("2");},true);
document.getElementById('div3').addEventListener("click",function(){alert("3");},false);
document.getElementById('div4').addEventListener("click",function(){alert("4");},true);
// 2 4-2 4 3 1
</script>
```

**利用冒泡原理实现事件委托（事件代理**）

### mouseover与mouseout是冒泡的

### mouseenter与mouseleave是不冒泡的

#### 阻止冒泡行为

```js
box.click(function(e){
    e = window.event || e;
    if(e && e.stopPropagation){     
        e.stopPropagation();
    }
    else{    
        e.cancelBubble = true;
    }
})
```

#### 阻止默认行为

```js
function stopDefaultEvent(){
    if(window.event){   // IE
        window.event.returnValue = false
        // 或者 return false
    }else {
        event.preventDefault()
    }
}
```



