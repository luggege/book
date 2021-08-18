### context：生产者-消费者模式

> 适用于祖祖组件之间值的传递，实际更多情况使用react-redux

```js
import React, { Component } from 'react'
import './index.css'

// 创建Context对象
const Mycontext = React.createContext()
const {Provider, Consumer} = Mycontext

export default class A extends Component {
    state = {
        username: 'tom',
        age: 18
    }
    render() {
        const {username, age} = this.state
        return (
            <div className="parent">
                <div>我是A组件</div>
                <div>我的用户名是：{this.state.username}</div>
                {/* <B username={this.state.username}/> */}
                <Provider value={{username, age}}>
                    <B />
                </Provider>
            </div>
        )
    }
}

class B extends Component {
    render() {
        return (
            <div className="child1">
                <div>我是B组件</div>
                <div>我从A组件接收到的用户名是：{this.props.username}</div>
                <C username={this.props.username} />
            </div>
        )
    }
}

// 类式组件
// class C extends Component {
//     // 接收context
//     static contextType = Mycontext
//     render() {
//         console.log(this.context)
//         const {username, age} = this.context
//         return (
//             <div className="child2">
//                 <div>我是C组件</div>
//                 {/* <div>我从A组件接收到的用户名是：{this.props.username}</div> */}
//                 <div>我从A组件接收到的用户名是：{username}, 年龄：{age}</div>
//             </div>
//         )
//     }
// }

// 函数式组件
function C () {
    return (
        <div className="child2">
            <div>我是C组件</div>
            {/* 使用Consumer标签接收 */}
            <Consumer>
                {
                    // value => {
                    //     const {username, age} = value
                    //     return <div>我从A组件接收到的用户名是：{username}, 年龄：{age}</div>
                    // }
                    value => `用户名是：${value.username}，年龄是：${value.age}`
                }
            </Consumer>
        </div>
    )
}
```



