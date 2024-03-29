# js的部分兼容写法

### 认识DOM0级方法跟DOM2级方法

> DOM0就是直接通过 onclick写在html里面的事件, 比如:

```js
<input onclick="alert(1)" />
```

> DOM2是通过 **addEventListener** 绑定的事件, 还有IE下的DOM2事件通过 **attachEvent **绑定;

①添加事件方法

addEventListener\(type, handler, false\)方法用于向指定元素添加事件句柄

三个参数分别是：

* event: 必传,字符串,指定事件名。

注意: 不要使用 "on" 前缀。 例如，使用 "click" ,而不是使用 "onclick"。

提示: 所有 HTML DOM 事件;

* function:必传。指定要事件触发时执行的函数。 当事件对象会作为第一个参数传入函数。 事件对象的类型取决于特定的事件。例如， "click" 事件属于 MouseEvent\(鼠标事件\) 对象
* useCapture:可选，是否在捕获或冒泡阶段执行，为bool值，**默认false：冒泡**

```javascript
addHandler：function(element,type,handler){
   if(element.addEventListener){//检测是否为DOM2级方法
     element.addEventListener(type, handler, false);
   }else if (element.attachEvent){//检测是否为IE级方法
     element.attachEvent("on" + type, handler);
   } else {//检测是否为DOM0级方法
     element["on" + type] = handler;
   }
}
```

②移除之前添加的事件方法

```javascript
removeHandler：function(element, type, handler){
  if (element.removeEventListener){ 
     element.removeEventListener(type, handler, false);
  } else if (element.detachEvent){
     element.detachEvent("on" + type, handler);
  } else {
     element["on" + type] = null;
  }
}
```

③获取事件及事件对象目标

获取**事件对象**的兼容性写法

```javascript
getEvent: function(event){
  // IE: window.event
  return event ? event : window.event;
}
```

获取**事件对象目标**的兼容性写法

```js
getTarget: function(event){
  return event.target || event.srcElement;
}
```

④阻止浏览器默认事件\(捕获\)的兼容性写法

```js
preventDefault: function(event){
    // IE: window.event
    var event = event || window.event;
    if (event.preventDefault){
        event.preventDefault();
    } else {
        event.returnValue = false;
        // 或者 return false;   // 原生js的return false阻止默认事件，jquery的既阻止默认事件又阻止冒泡
    }
}
```

⑤阻止事件冒泡的兼容性写法

```js
stopPropagation: function(event){
  var event = event || window.event;
  if (event.stopPropagation){
    event.stopPropagation();
  } else {
    event.cancelBubble = true;
  }
}
```

⑥mouseover和mouseout 事件才包含的获取相关元素的方法

```js
getRelatedTarget: function(event){ 
    if (event.relatedTarget){ 
        return event.relatedTarget; 
    } else if (event.toElement){ 
        return event.toElement; 
    } else if (event.fromElement){ 
        return event.fromElement; 
    } else { 
        return null; 
    }
}
```

⑦鼠标滚轮判断

对于mousedown 和mouseup 事件来说，则在其event 对象存在一个button 属性，表示按下或释放的按钮。

1. DOM的button 属性可能有如下3 个值：
   * 0 表示主鼠标按钮，
   * 1 表示中间的鼠标按钮（鼠标滚轮按钮），
   * 2 表示次鼠标按钮。
2. 在常规的设置中，主鼠标按钮就是鼠标左键，而次鼠标按钮就是鼠标右键。IE8 及之前版本也提供了button 属性，但这个属性的值与DOM 的button 属性有很大差异.
   * 0：表示没有按下按钮。
   * 1：表示按下了主鼠标按钮。
   * 2：表示按下了次鼠标按钮。
   * 3：表示同时按下了主、次鼠标按钮。
   * 4：表示按下了中间的鼠标按钮。
   * 5：表示同时按下了主鼠标按钮和中间的鼠标按钮。
   * 6：表示同时按下了次鼠标按钮和中间的鼠标按钮。
   * 7：表示同时按下了三个鼠标按钮。

```javascript
getButton: function(event){
  if(document.implementation.hasFeature("MouseEvents", "2.0")){
     return event.button;
  } else {
     switch(event.button){
        case 0:
        case 1:
        case 3:
        case 5:
        case 7:
        return 0;

        case 2:
        case 6:
        return 2;

        case 4:
        return 1;
     }
  }
}
```

⑧能够取得鼠标滚轮增量值（delta）的方法

```js
getWheelDelta: function(event){
     if (event.wheelDelta){
         return (client.engine.opera && client.engine.opera < 9.5 ? - event.wheelDelta : event.wheelDelta);
     } else {
         return -event.detail * 40;//firefox中的值为+3表示向上滚，-3表示向下滚 
     })
 }}
```

⑨跨浏览器的方式取得字符编码

```javascript
getCharCode: function(event){
    if (typeof event.charCode == "number"){
         return event.charCode;
    } else {
         return event.keyCode;
    }
}
```

⑩访问剪贴板中的数据

```javascript
getClipboardText: function(event){
    var clipboardData = (event.clipboardData || window.clipboardData);
    return clipboardData.getData("text");
}
```

⑩.设置剪贴板中的数据

```javascript
setClipboardText: function(event, value){
    if (event.clipboardData){
        return event.clipboardData.setData("text/plain", value);
    } else if (window.clipboardData){
        return window.clipboardData.setData("text", value);
    }
}
```

## 12.获取滚动位置的兼容写法

```js
//获取滚动位置的兼容写法
function scroll() {
    if (window.pageXOffset !== undefined) {
        return {
            "top": window.pageYOffset,
            "left": window.pageXOffset
        };
    } else if (document.compatMode === "CSS1Compat") {
        return {
            "top": document.documentElement.scrollTop,
            "left": document.documentElement.scrollLeft
        };
    } else {
        return {
            "top": document.body.scrollTop,
            "left": document.body.scrollLeft
        };
    }
}
```



