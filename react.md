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

* 虚拟dom属性少，真实dom属性多（虚拟dom是React内部用，无需真实dom那么多属性）
* 虚拟dom最终会被react转为真实的dom呈现在页面上
* 二者本质上都是object对象

#### React/Vue中key的作用

> * 虚拟dom中key的作用：
>
> * * 简单的说：key是虚拟dom对象的标识，在更新显示时key起着极其重要的作用
>   * 详细的说：当状态中的数据发生变化时，react会根据【新数据】生成【新的虚拟dom】，随后react进行【新虚拟dom】与【旧虚拟dom】的diff比较，比较规则如下：
>   * * 旧虚拟dom中找到了与新虚拟dom相同的key：
>     * * 若虚拟dom中内容没变，直接使用之前的真实dom
>       * 若虚拟dom中内容变了，则生成新的真实dom，随后替换掉页面中之前的真实dom
>     * 旧虚拟dom中未找到与新虚拟dom相同的key：
>     * * 根据数据创建新的真实dom，随后渲染到页面
> * 用index作为key可能会引发的问题：
>
> * * 若对数据进行：逆序添加、逆序删除等破坏顺序操作：会产生没有必要的真实dom更新，界面效果没问题，但效率低
>   * 如果结构中还包含输入类的dom：会产生错误dom更新，界面有问题
>   * 注意！如果不存在对数据的逆序添加、逆序删除等破坏顺序操作，仅用于渲染列表用于展示，使用index作为key是没有问题的

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

所有React组件都必须是纯函数，并禁止修改其自身props

#### 受控组件&非受控组件

> 非受控组件：状态现用现取（ref）
>
> 受控组件：状态由React维护（setState存 state取）



