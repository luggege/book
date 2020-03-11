### 垃圾回收机制

> V8垃圾回收机制将不再用到的内存释放

### 引起内存泄漏的原因

* 全局变量
* * 常规全局变量
  * 函数中误操作写入的全局变量

```js
function foo(){
    // 全部指向window
    bar = 'this is a global'
    //或者this
    this.bar = 'this is a global'
}
foo()
```

* 定时器引用的DOM元素

> 当node节点被删除后，实际定时器内的逻辑不需要了，但定时器内的回调函数无法被回收

```js
setInteval(function(){
    var node = document.getElementById('id')
    if(node){
        node.innerHtml = 'aaaa'
    }
}, 1000)
```

* 闭包

```js
var theThing = null;
var replaceThing = function(){
    var originalThing = theThing;
    var unused = function(){
        if(originalThing){
            console.log('Hi');
        }
    }
    theThing = {
        longStr: new Array(1000000).join('*'),
        someMethod: function(){
            console.log(someMessage)
        }
    }
}
setInteval(replaceThing, 1000);
```

* 缓存

> 缓存内容无法被回收



