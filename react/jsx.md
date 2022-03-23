### jsx

> 是JavaScript的一种语法扩展，jsx最终会被**babel**编译为**React.createElement**\(\)，创建出**虚拟dom**

特点：

* 花括号{}中可以放任何有效的表达式
* 属性中使用变量，花括号外不能包引号
* 因为jsx接近js，所以属性定义采用驼峰命名
* 可以单标签自闭合也可以双标签，必须闭合

```js
const vm = <h1 className="title">Hello React</h1>
// 等同于
// const vm = React.createElement('h1', {className: 'title'}, 'Hello React')

// 1. ReactDOM.render()：用于将虚拟DOM渲染到浏览器的真实DOM上
ReactDOM.render(vm, document.getElementById('root'))

// 2. ReactDOM.findDOMNode()：获取真实DOM，组件挂载之后使用，componentDidMount和componentDidUpdate方法中获取
// 3. ReactDOM.unmountCompoentAtNode()：用于执行卸载操作，在componentWillMount之前
// 4. ReactDOM.creatPortal(child, container)：将子结点挂载到指定Dom中，并不直接渲染DOM元素，不同于render
```

#### 虚拟dom与真实dom的区别

* 虚拟dom属性少，真实dom属性多（虚拟dom是React内部用，无需真实dom那么多属性）
* 虚拟dom最终会被react转为真实的dom呈现在页面上
* 二者本质上都是object对象

#### 虚拟dom的属性

* sel:选择器
* data:绑定的数据\(attribute/props/eventlistner/class/dataset/hook\)
* children:子节点数组
* text:当前text节点内容
* elm: 对真实dom element的引用
* key:用于优化DOM操作

#### diff算法比较的三个原则/策略

* 结构不一样，直接卸载重新create
* 结构一样，不会卸载但update
* 同层子节点，通过key来区分

#### React/Vue中key的作用

* 虚拟dom中key的作用：
* * 简单的说：key是虚拟dom对象的标识，在更新显示时key起着极其重要的作用
  * 详细的说：当状态中的数据发生变化时，react会根据【新数据】生成【新的虚拟dom】，随后react进行【新虚拟dom】与【旧虚拟dom】的**diff比较**，比较规则如下：
  * * 旧虚拟dom中找到了与新虚拟dom相同的**key**：
    * 若虚拟dom中**内容**没变，直接使用之前的真实dom
    * 若虚拟dom中**内容**变了，则生成新的真实dom，随后替换掉页面中之前的真实dom
    * 旧虚拟dom中**未找到**与新虚拟dom相同的**key**：
    * 根据数据创建新的真实dom，随后渲染到页面
* 用index作为key可能会引发的问题：
* * 若对数据进行：逆序添加、逆序删除等破坏顺序操作：会产生没有必要的真实dom更新，界面效果没问题，但效率低
  * 如果结构中还包含输入类的dom：会产生错误dom更新，界面有问题
  * 注意！如果不存在对数据的**逆序添加**、**逆序删除**等破坏顺序操作，仅用于渲染列表用于展示，使用index作为key是没有问题的



