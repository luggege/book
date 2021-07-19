### 定义ref的方式

> 不能在函数组件上使用下边的三种方式定义ref属性，因为他们没有实例。可以在函数组件内部const myRef = useRef\(null\)，然后ref={myRef}

* 字符串方式（不推荐使用：效率不高）

```js
<input ref='input1' type="text" placeholder="按回车确认" onKeyUp={this.handleKeyUp}/>

handleKeyUp = () => {
    console.log(this.refs.input1.value)
}
```

* 回调函数形式的ref
  > React帮调用这个回调函数，参数是当前dom节点

```js
<input ref={element => this.input1 = element} type="text" placeholder="按回车确认" onKeyUp={this.handleKeyUp}/>

handleKeyUp = () => {    
    console.log(this.input1.value)
}
```

**内联的函数**，在**更新**过程中会调用两次，第一次为null，第二次真实dom，因为每次渲染会创建新的函数实例，React清空旧的ref并且设置新的；class的绑定函数的方式可以避免，但无关紧要。

* createRef
  > React调用后返回一个容器，该容器可以存储被ref所标识的节点。该容器是专人专用的，同一命名后边的会覆盖前边的

```js
// 内联函数
<input ref={this.myRef} type="text" placeholder="按回车确认" onKeyUp={this.handleKeyUp}/>
// class绑定式函数
{/*<input ref={this.saveInput} type="text" placeholder="按回车确认"/>*/}

myRef = React.createRef()

handleKeyUp = () => {
    console.log(this.myRef)   // {current: input} ===> this.myRef.current.value
}
```



