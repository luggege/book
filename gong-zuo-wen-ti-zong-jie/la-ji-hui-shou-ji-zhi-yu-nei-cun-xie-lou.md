### 垃圾回收机制

> V8垃圾回收机制将不再用到的内存释放

#### 引起内存泄漏的原因

* 全局变量
* * 常规全局变量
  * 函数中误操作写入的全局变量

```js
function foo(){
    // 全部指向window，变成全局变量
    bar = 'this is a global'
    //或者this
    this.bar = 'this is a global'
}
foo()
```

使用严格模式可以避免

* 绑定事件的dom，移除dom之后同时也需要解绑相应事件。**不用了的东西要记得及时归还**

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

* 不规范的使用闭包\(并不是一定会引起内存泄漏，只有在外部**引用**了才会引起内存泄漏\)

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

```js
function foo() {
    var a = {}
    function bar() {
        console.log(a)
    }
    // a 和 bar 相互循环使用
    a.fn = bar
    return bar
}
```

* 滥用缓存

> 缓存内容无法被回收

* 大量的使用console.log，console.log的对象是不能被垃圾回收，可能会造成内存泄漏



