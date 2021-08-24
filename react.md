#### jsx

> 是JavaScript的一种语法扩展，jsx最终会被babel编译为React.createElement\(\)，创建出虚拟dom

特点：

* 花括号{}中可以放任何有效的表达式
* 属性中使用变量，花括号外不能包引号
* 因为jsx接近js，所以属性定义采用驼峰命名
* 可以单标签自闭合也可以双标签，必须闭合

```js
const vm = <h1 className="title">Hello React</h1>

// 等同于
const vm = React.createElement('h1', {className: 'title'}, 'Hello React')

ReactDOM.render(vm, document.getElementById('root'))
```

#### 虚拟dom于真实dom的区别

* 虚拟dom属性少，真实dom属性多
* 虚拟dom最终会被react转为真实的dom呈现在页面上
* 二者 本质上都是object对象

#### 纯函数

> 需满足两个条件：
>
> * 返回值只受参数影响
> * 执行过程中无副作用（有副作用：对外部数据产生了可观察的变化）

```js
// 纯函数
function fn(a, b) {
    return (a + b)
}

// 不纯
function fn() {
    return Math.random()
}
```

```js
// 纯函数
function fn(obj, b) {
    return (obj.x + b)
}
const obj = {x: 2}

// 不纯
function fn(obj, b) {
    obj.x = 3
    return (obj.x + b)
}
const obj = {x: 2}
```



