#### 父子组件之间通信

* 父 ===&gt; 子：父组件通过**属性**往子组件传值，子组件通过**props**接收
* * children props
  * render props
* 子 ===&gt; 父：父组件通过**属性**传递**回调函数**，子组件通过**props调用**父组件的函数，最终父组件中操作函数

#### 非父子组件之间通信

* 借用第三方库**pubsub-js**，消息**订阅**-**发布机制（先订阅，后发布）**技术实现

解决的问题：之前，状态及状态操作的方法只能放在共同的父组件；现在，实现状态谁用谁操作，结构更清晰

```js
render() {
    return (
      <div className="todo-container">
        <Header />
        <List />
      </div>
    )
}
```

```js
// list
componentDidMount() {
    // 订阅消息
    this.token = PubSub.subscribe('addTodo', (msg, todo) => {
        console.log('消息已发布：', msg, todo);  // 消息已发布：addTodo
    })
}
componentWillUnMount() {
    // 取消订阅
    PubSub.unsubscribe(this.token)
}
```

```js
// header
handleKeyUp = (event) => {
    const {target, keyCode} = event
    // 发布消息
    PubSub.publish('addTodo', {id: nanoid(), name: target.value, done: false})
}
```

### redux

> 通常适用于祖孙组件通信

### context

> 生产者-消费者模式，开发中用的少



