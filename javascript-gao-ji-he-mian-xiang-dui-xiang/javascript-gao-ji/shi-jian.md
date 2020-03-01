# 事件

> 描述的是从页面中**接收事件的顺序**。

IE的事件流是事件**冒泡流**，

Netscape Communicator的事件流是事件**捕获流**。

先捕获，后冒泡

所有事件的顺序：其他元素捕获阶段事件 ==》目标阶段（按注册事件先后顺序）==〉其他元素冒泡阶段事件

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

document.getElementById('div1').addEventListener("click",function(){alert("1");},false);
document.getElementById('div4').addEventListener("click",function(){alert("4-2");},true);
document.getElementById('div2').addEventListener("click",function(){alert("2");},true);
document.getElementById('div3').addEventListener("click",function(){alert("3");},false);
document.getElementById('div4').addEventListener("click",function(){alert("4");},false);
</script>
```

### 阻止冒泡

```js
e.stopPropagation();

// ie
e.cancelBubble = true;
```



