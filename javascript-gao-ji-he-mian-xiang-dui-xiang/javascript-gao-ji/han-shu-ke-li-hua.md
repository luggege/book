### 高阶函数

> 满足以下任一条件的函数就是高阶函数
>
> * 函数的参数是函数
> * 返回函数

### 柯里化

> 是把接收**多个参数**的函数变成一个**单一参数**（最初函数的第一个参数）的函数，并且返回接收**余下的参数**而且**返回结果**的新函数的技术（累积函数的参数，最后延迟执行）

好处：

* 参数复用

```js
// 普通函数
function check(reg, txt) {
    return reg.test(txt)
}
check(/\d+/g, 'test')     // false
check(/[a-z]+/g, 'test')  // true

// 复用第一个参数（正则规则），校验字符串
function curryCheck(reg) {
    return function(txt) {
        return reg.test(txt)
    }
}
const hasNumber = curryCheck(/\d+/g)
const hasLetter = curryCheck(/[a-z]+/g)
hasNumber('test')      // false
hasLetter('test')      // true
```

* 提前返回（提前确认）

```js
// 浏览器监听事件
var on = function(element, type, fn) {
    if(window.addEventListener) {
        if(element && type && fn) {
            element.addEventListener(type, () => {
                fn.apply(element, arguments)
            })
        }
    }else {
        if(element && type && fn) {
            element.attachEvent('on' + type, () => {
                fn.apply(element, arguments)
            })
        }
    }
}

// 改装后（自执行后返回一个函数，提前确定了会走哪一个分支）
var on = (function() {
    if(window.addEventListener) {
        return function(element, type, fn) {
            if(element && type && fn) {
                element.addEventListener(type, () => {
                    fn.apply(element, arguments)
                })
            }
        }
    }else {
        return function(element, type, fn) {
            if(element && type && fn) {
                element.attachEvent('on' + type, () => {
                    fn.apply(element, arguments)
                })
            }
        }
    }
})()
```

* 延迟执行

```js
// JS 中常用的bind，实现的机制就是柯里化
Function.prototype.bind = function(context) {
    var _this = this
    var args = Array.prototype.slice.call(arguments, 1)    
    return function() {
        return _this.apply(context, args)
    }
}
```

**通用的封装方法**

```js
// 初步封装
function curry(fn) {
    // args 获取第一个方法内的全部参数
    var args = Array.prototype.slice.call(arguments, 1);
    return function() {
        // 将后面方法的全部参数和args合并
        var newArgs = args.concat(Array.prototype.slice.call(arguments, 1))
        // 把合并后的参数通过apply作为fn的参数并执行fn
        return fn.apply(this, newArgs)
    }
}
```

缺点：不能支持三个参数以上

```js
// 支持多参数传递（递归）
function fn(a, b, c, d) {
    return a + b + c + d
}
function curry(fn, args) {
    args = args || [];
    const len = fn.length;  // 4
    let _this = this;
    return function() {
        // 收集参数
        let _args = Array.prototype.slice.call(arguments) // [1]、[2]、[3]、[4]
        Array.prototype.push.apply(args, _args)
        if(args.length < len) {
            return curry.apply(_this, fn, args)
        }
        // 收集完毕，执行fn
        return fn.apply(_this, args)
    }
}
const add = curry(fn)
add(1)(2)(3)(4)     // 10
```

#### 性能

* 存取arguments对象通常要比存取命名参数要慢一点
* 一些老版本的浏览器实现arguments.length是相当慢的
* 使用fn.apply\(\)和fn.call\(\)通常比直接调用fn\(\)稍微慢点
* 创建大量嵌套作用域和闭包函数会带来花销，无论是在内存上还是速度上

其实在大部分应用中，主要的性能瓶颈是在操作DOM节点上，这些js的性能损耗基本是可以忽略的，所以curry是可以放心使用的

