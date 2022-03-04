### hooks

解决了三个问题：

* 维护state状态：**React.useState**\(当前状态名，更新状态的函数名\)
* 模拟类式组件中的生命周期：**React.useEffect**\(\(\) =&gt; {}, \[\]\)
* 保存标签对象**React.useRef**\(\)

```js
import React, { Component } from 'react'
import reactDom from 'react-dom'

// 类式组件
// export default class index extends Component {
//     state = {
//         count: 0
//     }
//     myRef = React.createRef()
//     add = () => {
//         // 函数式的setState
//         this.setState(state => {
//             return {count: state.count + 1}
//         })
//     }
//     show = () => {
//         console.log(this.myRef.current.value)
//     }
//     componentDidMount() {
//         this.timer = setInterval(() => {
//             this.setState(state => ({count: state.count + 1}))
//         }, 1000)
//     }
//     unmount = () => {
//         reactDom.unmountComponentAtNode(document.getElementById('root'))
//     }
//     componentWillUnmount() {
//         clearInterval(this.timer)
//     }
//     render() {
//         return (
//             <div>
//                 <input type="text" ref={this.myRef}/>
//                 <h1>当前求和为： {this.state.count}</h1>
//                 <button onClick={this.add}>点我—+1</button>
//                 <button onClick={this.unmount}>卸载组件</button>
//                 <button onClick={this.show}>点击提示数据</button>
//             </div>
//         )
//     }
// }
```

```js
// 函数式组件
// 调用1+n次
function Demo() {
    // 1. useState(当前状态值，更新状态的函数)
    // 底层处理了，不会再次调用重置为0
    const [count, setCount] = React.useState(0)
    const [name, setName] = React.useState('tom')

    // 2. useEffect() （用于模拟类式组件中的生命周期）: 
    // 不写第二个参数时，相当于检测所有人，有改变就调用。若第二个为空，则只调用一次
    React.useEffect(() => {
        console.log('@@@')
        let timer = setInterval(() => {
            setCount(count => count + 1)
        }, 1000)
        // 返回的这个函数相当于componentWillUpdate
        return () => {
            clearInterval(timer)
        }
    }, [])

    // 3. useRef()：保存标签对象，与createRef()一样
    const myRef = React.useRef()

    function add() {
        // 第一种方式：
        // setCount(count + 1)
        // 第二种方式
        setCount(count => count + 1)
    }
    function changeName() {
        setName('jack')
    }
    function unmount() {
        reactDom.unmountComponentAtNode(document.getElementById('root'))
    }
    function show() {
        console.log(myRef.current.value)
    }
    return (
        <div>
            <input type="text" ref={myRef}/>
            <h1>当前求和为： {count}</h1>
            <div>我的名字是：{name}</div>
            <button onClick={add}>点我—+1</button>
            <button onClick={changeName}>点我改名</button>
            <button onClick={unmount}>卸载组件</button>
            <button onClick={show}>点击提示数据</button>
        </div>
    )
}

export default Demo
```



